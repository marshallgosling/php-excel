# php-excel

## PHPExcel library compatible with Laravel Framework >= 8.x

```php

use Nathan\PHPExcel;

function createObj()
{
    $objPHPExcel = new PHPExcel();
		
		// Set document properties
		$objPHPExcel->getProperties()->setCreator($creator)
		->setLastModifiedBy($creator)
		->setTitle($title)
		->setSubject($subject)
		->setDescription($description)
		->setKeywords($keywords)
		->setCategory($category);
}

function loadTemplate($file)
{
    $objPHPExcel = IOFactory::load($file);
}

function outputFile($filename, $mode='file')
{
    $objWriter = IOFactory::createWriter($objPHPExcel, 'Excel2007');
		
		if($mode == 'stream') {
		// Redirect output to a client’s web browser (Excel2007)
			header('Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet');
			header('Content-Disposition: attachment;filename="'.$filename.'"');
			header('Cache-Control: max-age=1920');
			
			$objWriter->save('php://output');
			exit;
		}
		if($mode == 'file') {
			$objWriter->save($filename);
		}

}


```
