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

public class WebCrawler {
	
	public static void main(String[] args) throws IOException {
	
		//gets an input website from the user
		Scanner scanner = new Scanner(System.in);  
		System.out.println("Enter a link: ");
		String userinput = scanner.nextLine(); 
		
	/*
	* Page Collector
	* The first part of this program searches through the given website from the user
	* All the links contained in that website would be found.
	*/
		//executes cases that go as planned
		try {
		
			//gets a href attribute to resolve an absolute URL
			Document doc = Jsoup.connect(userinput).get();
			org.jsoup.select.Elements links = doc.select("a");
			
			for(org.jsoup.nodes.Element e:links) {
				
				//prints out all the absolute links
				System.out.println(e.attr("abs:href")); //attribute key in parenthesis
			
				//Sets the size of the link(element) to variable named listSize
				Elements link = doc.select("a[href]");
				int listSize = link.size();
		        }
		}
		
		//catches any exceptional cases
		catch (IOException ex) {
			//Severe is a message indicates a serious failure
			Logger.getLogger(WebCrawler.class.getName()).log(Level.SEVERE, null, ex); 
			
		}
		
	/*
	*Links Checker
	*The second part of this program checks if the links exist or not.
	*/
	
		//gets a href attribute to resolve an absolute URL
		Document doc = Jsoup.connect(userinput).get();
		org.jsoup.select.Elements links = doc.select("a");
		Elements link = doc.select("a[href]");
		//Sets the size of the link(element) to variable named listSize
		int listSize = link.size();

		//prints spaces and the number of links found from the first part of the program
		System.out.println("");
		System.out.println("The number of links found:" + listSize);
		System.out.println("");
		
		// go through every link found
		for(int i = 0; i < listSize ; i += 1) {
			String urlString = userinput;
			URL url = new URL(urlString);
			final URL url1 = new URL(userinput);
			HttpURLConnection huc = (HttpURLConnection) url1.openConnection();
			int response= huc.getResponseCode();
			//check if the link exists or not
			if(response != 404){ 
				 System.out.println("exists");
			} else {
				System.out.println("does not exist");
			}
		}
	}
}
