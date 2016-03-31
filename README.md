package Webcrawler;

import java.io.IOException;
import java.util.logging.Level;
import java.util.logging.Logger;

import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

public class WebPage {
	private Anchor anchor;
	private String webPageHash;
	private int anchorParseStatus;
	private int emailParseStatus;
	
	
	private Document document;
	/**
	 * General constructor for crawling
	 */
	public WebPage(Anchor anchor) {
		this.anchor = anchor;
	}
	
	/**
	 * Jsoup gets html
	 * @return 
	 */
	public void WebPage11 (Anchor anchor)
	{
		this.anchor = anchor;
	}
	
	// Getters
	public Document getDocument()
	{
		return this.document;
	}
	
	public int getEmailParseStatus()
	{
		return this.emailParseStatus;
	}
	
	public String getWebPageHash()
	{
		return this.webPageHash;
	}
	
	public int getAnchorPageStatus()
	{
		return this.anchorParseStatus;
	}
	
	// JSoup carries the html
	public void loadDocumentFromWeb()
	{
		try 
		{
			Document doc = Jsoup.connect(anchor.getAnchorUrl()).get(); 
			Elements links = doc.select("a"); // Selects a tag HTML
			System.out.println("Número de links: " + links.size() + "\n");
			for(Element e: links) // Imports  org.jsoup.nodes.Element
			{
					System.out.println(e.attr("abs:href")); 
			}
		} catch (IOException e) 
		{
			e.printStackTrace();
		}	
	}
}

	
