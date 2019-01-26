# MW-PdfHandler-WIndows
Workaround for Mediawiki PdfHandler Extension for Windows Server

Tested on Windows Server 2008 R2 running MediaWiki v1.31.1 and PHP v7.2.13

=================================
Prerequisites
=================================
* Download Ghostscript - https://www.ghostscript.com/download/gsdnld.html
* Download Xpdf tools -http://www.xpdfreader.com/download.html
* Download ImageMagick - http://www.imagemagick.org/script/download.php 
** Make sure that "Install legacy utilities (e.g. convert)" is checked for convert.exe


=================================
Installation
=================================
* Save the following files to C:\Windows\System32 or one of the System Environment Variables path
** gswin64c.exe (from Ghostscript)
** pdfinfo.exe (from Xpdf tools)
** pdftotext.exe (from Xpdf tools)
** convert.exe (from ImageMagick)

* Add the following code to the LocalSeetings.php
-------------------------------------------------------
////////////////////////////////////////////////////////////
//PDFHandler
////////////////////////////////////////////////////////////
$wgEnableUploads = true;
$wgAllowJavaUploads = true;
$wgUseImageMagick = true;
$wgImageMagickConvertCommand = 'convert.exe';

$wgPdfProcessor = 'gswin64c.exe';
$wgPdfInfo = 'pdfinfo.exe';
$wgPdftoText = 'pdftotext.exe';
$wgPdfPostProcessor = $wgImageMagickConvertCommand; 
////////////////////////////////////////////////////////////
-------------------------------------------------------