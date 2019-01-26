# MW-v1.31.1-PdfHandler-Windows-Server
Workaround for Mediawiki PdfHandler Extension for Windows Server

*Tested on Windows Server 2008 R2 running MediaWiki v1.31.1 and PHP v7.2.13.
*Based on the snapshot of version 21f2fe9 of the PdfHandler extension for MediaWiki REL1_31 - https://www.mediawiki.org/wiki/Special:ExtensionDistributor?extdistname=PdfHandler&extdistversion=REL1_31

* Special thanks to Tommyheyser for the original fix - https://www.mediawiki.org/w/index.php?title=Topic:Uo126vm59hjjamjq&topic_showPostId=uo1afnwi0x5lcii7#flow-post-uo1afnwi0x5lcii7
* The code has been changed to avoid pdfinfo and pdftotext hangs that prevents some pdfs to be uploaded

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
//PDFHandler Extension

$wgEnableUploads = true;

$wgAllowJavaUploads = true;

$wgUseImageMagick = true;

$wgImageMagickConvertCommand = 'convert.exe';


$wgPdfProcessor = 'gswin64c.exe';

$wgPdfInfo = 'pdfinfo.exe';

$wgPdftoText = 'pdftotext.exe';

$wgPdfPostProcessor = $wgImageMagickConvertCommand; 
