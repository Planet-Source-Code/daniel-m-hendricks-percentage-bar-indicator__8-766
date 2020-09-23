<div align="center">

## Percentage Bar Indicator


</div>

### Description

A percentage bar indicator. Can be used to create a "relevancy" statistic bar for custom search engine, to display user voting statistics (ie, 3 out of 4 stars), or display any other percentage graphically. See also my ASP.NET/C# version: http://www.planetsourcecode.com/vb/scripts/ShowCode.asp?txtCodeId=3415&lngWId=10
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Daniel M\. Hendricks](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/daniel-m-hendricks.md)
**Level**          |Intermediate
**User Rating**    |4.4 (22 globes from 5 users)
**Compatibility**  |PHP 4\.0
**Category**       |[Graphics/ Sound](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/graphics-sound__8-15.md)
**World**          |[PHP](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/php.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/daniel-m-hendricks-percentage-bar-indicator__8-766/archive/master.zip)





### Source Code

```
<?
$docroot = $DOCUMENT_ROOT; //On Windows machines, you'll need to hard code the current path.
$percent = Round(($value/$max)*100, 0);
$rectwidth = $width;
if ($showpercent) {	$width += (imagefontwidth($fontsize) * strlen($percent."%")) + imagefontwidth("%"); }
$image = imagecreate($width, $height);
//Set the colors and calculate font width/height.
$bg_color = imagecolorallocate($image, 0xFF, 0xFF, 0xFF); //white
$bar_color = imagecolorallocate($image, 0xFF, 0x40, 0x40); //red
$border_color = imagecolorallocate($image, 0x00, 0x00, 0x00); //black
$font_color = imagecolorallocate($image, 0x00, 0x00, 0x00); //black
$font_width = imagefontwidth($fontsize) * strlen($percent."%");
$font_height = imagefontheight($fontsize);
//Bar Generation Code
imagerectangle($image, 0, 0, $rectwidth-1, $height-1, $border_color);
ImageFilledRectangle($image, 1, 1, $rectwidth*($percent/100)-2, $height-2, $bar_color);
for($a = 0; $a <= $rectwidth-1; $a += ($rectwidth/$max)) {
	imageline($image, $a, 0, $a, $height, $border_color);
}
if ($showpercent) { imagestring($image, $fontsize, $width-$font_width, ($height-$font_height)/2, $percent."%", $font_color); }
// Flush Image
header("Content-type: image/png");
ImagePNG($image);
ImageDestroy($image);
?>
```

