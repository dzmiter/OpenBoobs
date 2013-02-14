class DefaultController < ApplicationController

require 'open-uri'
require 'RMagick'

def index
@OpenBoobs = open("http://oboobs.ru/"){
|f|f.read}
@likes = @OpenBoobs.scan(/<div id\=\"divrank\d+\"\>(\d+)\<\/div\>/)
@photos = @OpenBoobs.scan(/<img src="(.*)" alt=".*" width=".*"/)

@length = 1

@realPhotos = []

#File.open("./likes", "w"){|file| file.write(@realPhotos)}

@photos.each_index { |i|
	@realPhotos [i] = []
	photo = @photos[i].first
	
	@realPhotos[i][0] ="./assets/" +  File.basename(photo)	
	
	writeOut = File.new("./app/assets/images/" + File.basename(photo), "wb")
	writeOut.write(open(photo).read) 
	writeOut.close
	
	#text = Magick::Draw.new
	
	#text.annotate(@realPhotos[i], 0, 0, 0, 100, likes[i].to_s) do
	# self.gravity = Magick::SouthGravity
	# self.pointsize = 72
	# self.stroke = 'black'
	# self.fill = '#FAFAFA'
	# self.font_weight = Magick::BoldWeight
	# self.font_stretch = Magick::UltraCondensedStretch
	#end
}

File.open("./likes", "w"){|file| file.write(@realPhotos)}

end
end
