	<?php

	//合成
 	$multiTIFF = new Imagick();
            for($i=3;$i>=1;$i--)
            {

                $auxIMG = new Imagick();
                $auxIMG->readImage('/data/wwwlogs/youkantou-server/'.$i.'.png');

                $multiTIFF->addImage($auxIMG);
            }

			//file multi.TIF
            $multiTIFF->writeImages('/data/wwwlogs/youkantou-server/multi423432.gif', true); // combine all image into one single image

			//files multi-0.TIF, multi-1.TIF, ...
            $multiTIFF->writeImages('/data/wwwlogs/youkantou-server/multi.gif', false);
			die;


			//抽帧
            $image = new Imagick('/data/11.gif');
            $frames = $image->coalesceImages();
            echo '帧数:' . count($frames);

            foreach ($frames as $i => $frame) {
                $frame->setImageFormat("jpg");
                $content = $frame->getImageBlob();

                    file_put_contents('/data/wwwlogs/youkantou-server/'.$i.'.gif', $content);
                //$frame->writeImage("pic_" . $i . ".jpg");
            }

            $frames->deconstructImages();die;