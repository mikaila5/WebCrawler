# WebCrawler
package Webcrawler;

import java.io.IOException;
import java.util.logging.Level;
import java.util.logging.Logger;
import org.jsoup.Jsoup;
//import org.jsoup.modes.Document;
import org.jsoup.select.Elements;

import javax.swing.text.Document;

public class WebCrawler 
{
	//private static final Logger log= Logger.getLogger( WebCrawler.class.getName() );

	public static void main(String[] args)
	{
		try {
			Document doc = (Document) Jsoup.connect("http://www.jsoup.org/").get();
			Elements newsHeadlines = ((Elements) doc).select("#mp-itn b a");
		} catch (IOException ex) {
			Logger.getLogger(WebCrawler.class.getName());log(Level.SEVERE, null, ex);
		}
		
	}

	private static void log(Level severe, Object object, IOException ex) {
		// TODO Auto-generated method stub
		
	}
	
}
