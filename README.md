package Webcrawler;


import java.io.BufferedWriter;
import java.io.File;

import java.io.FileWriter;
import java.io.IOException;


import java.util.logging.Level;
import java.util.logging.Logger;


import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.select.Elements;

public class WebCrawler 
{
	public static void main(String[] args)
	{
		
		try {
			
			
			
			Document doc = Jsoup.connect("https://www.oracle.com/java/index.html").get();
			Elements anchors = doc.select("a");
			for (org.jsoup.nodes.Element anchor: anchors){
				File file = new File("filename.txt");
				FileWriter fw = new FileWriter(file.getAbsoluteFile());
				BufferedWriter bw = new BufferedWriter(fw);
				bw.write(anchor.attr("href"));
				bw.close();// to close BufferedWriter
				System.out.println(anchor.attr("href"));	
			}
		} catch (IOException e){
			Logger.getLogger(WebCrawler.class.getName()).log(Level.SEVERE, null, e);
		}
		
		
	}
	 
		}
