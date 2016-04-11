package Webcrawler;

import java.io.BufferedWriter;
import java.io.File;

import java.io.FileWriter;
import java.io.IOException;
import java.util.Scanner;
import java.util.logging.Level;
import java.util.logging.Logger;



import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.select.Elements;

import java.net.HttpURLConnection;

import java.net.URL;

public class WebCrawler 
{
	
	public static void main(String[] args) throws IOException
	{ 
		Scanner scanner = new Scanner(System.in);  
		System.out.println("Enter a link: ");
		String userinput = scanner.nextLine(); 
		
		try{
			Document doc = Jsoup.connect(userinput).get();
			org.jsoup.select.Elements links = doc.select("a");
			for(org.jsoup.nodes.Element e:links) {
				File file = new File("filename.txt");
				FileWriter fw = new FileWriter(file.getAbsoluteFile());
				BufferedWriter bw = new BufferedWriter(fw);
				bw.write(e.attr("abs:href"));
				bw.close();// be sure to close BufferedWriter
				
				System.out.println(e.attr("abs:href")); //attribute key in parenthesis
			

				Elements link = doc.select("a[href]");
				int n = link.size();
				
			
		        }
			
		}
		catch (IOException ex) {
			Logger.getLogger(WebCrawler.class.getName()).log(Level.SEVERE, null, ex); 
			//Severe is a message indicates a serious failure
		}
		Document doc = Jsoup.connect(userinput).get();
		org.jsoup.select.Elements links = doc.select("a");
		Elements link = doc.select("a[href]");
		int n = link.size();
		System.out.println("");
		System.out.println("The number of links found:" + n);
		System.out.println("");
				for(int i = 0; i < link.size() ; i += 1)
				{
				String urlString = userinput;
				URL url = new URL(urlString);
				final URL url1 = new URL(userinput);
				HttpURLConnection huc = (HttpURLConnection) url1.openConnection();
				int response= huc.getResponseCode();
				if(response != 404){ 
				 System.out.println("exists");
				} else {
				    System.out.println("does not exist");
				}
				}
				}
		
	}
	 
