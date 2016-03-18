# WebCrawler
package Webcrawler;

import java.io.IOException;

import java.util.logging.Level;
import java.util.logging.Logger;

//import javax.lang.model.element.Element;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.select.Elements;


public class WebCrawler 
{
	public static void main(String[] args)
	{
		try {
			Document doc = Jsoup.connect("http://www.twu.ca/").get();
			Elements anchors = doc.select("a");
			for (org.jsoup.nodes.Element anchor: anchors){
				System.out.println(anchor.attr("href"));
			}
		} catch (IOException ex) {
			Logger.getLogger(WebCrawler.class.getName()).log(Level.SEVERE, null, ex);
		}
		
	}

	//private static void log(Level severe, Object object, IOException ex) {
		// TODO Auto-generated method stub
		
	}
	

