**step1:在项目根目录build.grade文件中添加**
<pre><code>
allprojects {
   repositories {
 	  ...
 	  maven { url 'https://jitpack.io' }
   }
}
</code></pre>

 **step2:在app项目下的build.grade文件中添加依赖**
 <pre><code>
 dependencies {
     compile 'com.github.Waterelone:WT_Compress:1.0.0'
 }
 </code></pre>
 **step3：使用说明**
 <pre><code>
 public void compressImage(Uri uri) {
         Log.e("===compressImage===", "====开始传入原图uri==" + uri.getPath());
         try {
             File saveFile = new File(getExternalCacheDir(), "compress_" + System.currentTimeMillis() + ".jpg");
             Bitmap bitmap = MediaStore.Images.Media.getBitmap(getContentResolver(), uri);
             Log.e("===compressImage===", "====开始==压缩==saveFile==" + saveFile.getAbsolutePath());
             NativeUtil.compressBitmap(bitmap, saveFile.getAbsolutePath());
             Log.e("===compressImage===", "====完成==压缩==saveFile==" + saveFile.getAbsolutePath());
             imageView.setImageBitmap(bitmap);
         } catch (IOException e) {
             e.printStackTrace();
         }

     }
</code></pre>
