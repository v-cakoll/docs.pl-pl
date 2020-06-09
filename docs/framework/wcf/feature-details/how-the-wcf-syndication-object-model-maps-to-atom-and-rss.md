---
title: Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: 67fbbb035a3a6683cefbf24e299f32579b674bbd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597257"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS
Podczas tworzenia usługi zespalania Windows Communication Foundation (WCF) można tworzyć źródła danych i elementy przy użyciu następujących klas:  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>Można zserializować do dowolnego formatu zespalania, dla którego zdefiniowano program formatujący. Usługa WCF dostarcza dwa elementy formatujące: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> .  
  
 Model obiektów wokół <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> jest bardziej ściśle wyrównany ze specyfikacją Atom 1,0 niż specyfikacja RSS 2,0. Jest to spowodowane tym, że Atom 1,0 jest bardziej znaczącą specyfikacją, która definiuje elementy, które są niejednoznaczne lub pominięte ze specyfikacji RSS 2,0. Z tego powodu wiele elementów w modelu obiektów zespolonych WCF nie ma bezpośredniej reprezentacji w specyfikacji RSS 2,0. Podczas serializacji <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów do RSS 2,0, WCF pozwala na Serializowanie elementów danych specyficznych dla Atom jako elementów rozszerzenia kwalifikowanej przestrzeni nazw, które są zgodne ze specyfikacją Atom. Można to kontrolować za pomocą parametru przesłanego do <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktora.  
  
 Przykłady kodu w tym temacie używają jednej z dwóch metod zdefiniowanych w tym miejscu do wykonania rzeczywistej serializacji.  
  
 `SerializeFeed`deserializacji źródła zespolonego.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem`deserializacji elementu zespolonego.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.SyndicationFeed> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowany do Atom 1,0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<feed xml:lang="EN-US" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text">My Feed Title</title>  
  <subtitle type="text">My Feed Description</subtitle>  
  <id>FeedID</id>  
  <rights type="text">Copyright 2007</rights>  
  <updated>2007-08-29T13:57:17-07:00</updated>  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <logo>http://server/image.jpg</logo>  
  <generator>Sample Code</generator>  
  <link rel="alternate" href="http://myfeeduri/" />  
  <entry>  
    <id>ItemID</id>  
    <title type="text">Item Title</title>  
    <summary type="text">Item Summary</summary>  
    <published>2007-08-29T00:00:00-07:00</published>  
    <updated>2007-08-29T13:57:17-07:00</updated>  
    <author>  
      <name>Jesper Aaberg</name>  
      <uri>http://Jesper/Aaberg</uri>  
      <email>Jesper@Aaberg.com</email>  
    </author>  
    <contributor>  
      <name>Lene Aaling</name>  
      <uri>http://Lene/Aaling</uri>  
      <email>Lene@Aaling.com</email>  
    </contributor>  
    <link rel="alternate" href="http://myitemuri/" />  
    <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
    <content type="text">Item Content</content>  
    <rights type="text">Copyright 2007</rights>  
    <source>  
      <title type="text">My Feed Title</title>  
      <subtitle type="text">My Feed Description</subtitle>  
      <id>FeedID</id>  
      <rights type="text">Copyright 2007</rights>  
      <updated>2007-08-29T13:57:17-07:00</updated>  
      <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
      <logo>http://server/image.jpg</logo>  
      <generator>Sample Code</generator>  
      <link rel="alternate" href="http://myfeeduri/" />  
    </source>  
  </entry>  
</feed>  
```  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowany do RSS 2,0.  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<rss xmlns:a10="http://www.w3.org/2005/Atom" version="2.0">  
  <channel>  
    <title>My Feed Title</title>  
    <link>http://myfeeduri/</link>  
    <description>My Feed Description</description>  
    <language>EN-US</language>  
    <copyright>Copyright 2007</copyright>  
    <lastBuildDate>Wed, 29 Aug 2007 13:57:17 -0700</lastBuildDate>  
    <category domain="categoryScheme">categoryName</category>  
    <generator>Sample Code</generator>  
    <image>  
      <url>http://server/image.jpg</url>  
      <title>My Feed Title</title>  
      <link>http://myfeeduri/</link>  
    </image>  
    <a10:id>FeedID</a10:id>  
    <item>  
      <guid isPermaLink="false">ItemID</guid>  
      <link>http://myitemuri/</link>  
      <author>Jesper@Aaberg.com</author>  
      <category domain="categoryScheme">categoryName</category>  
      <title>Item Title</title>  
      <description>Item Summary</description>  
      <source>My Feed Title</source>  
      <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
      <a10:updated>2007-08-29T13:57:17-07:00</a10:updated>  
      <a10:rights type="text">Copyright 2007</a10:rights>  
      <a10:content type="text">Item Content</a10:content>  
      <a10:contributor>  
        <a10:name>Lene Aaling</a10:name>  
        <a10:uri>http://Lene/Aaling</a10:uri>  
        <a10:email>Lene@Aaling.com</a10:email>  
      </a10:contributor>  
    </item>  
  </channel>  
</rss>  
```  
  
## <a name="syndicationitem"></a>SyndicationItem  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.SyndicationItem> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowany do Atom 1,0.  
  
```xml  
<entry xmlns="http://www.w3.org/2005/Atom">  
  <id>ItemID</id>  
  <title type="text">Item Title</title>  
  <summary type="text">Item Summary</summary>  
  <published>2007-08-29T00:00:00-07:00</published>  
  <updated>2007-08-29T14:07:09-07:00</updated>  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
  <author>  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor>  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
  <link rel="alternate" href="http://myitemuri/" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <category term="categoryName" label="categoryLabel" scheme="categoryScheme" />  
  <content type="text">Item Content</content>  
  <rights type="text">Copyright 2007</rights>  
  <source>  
    <title type="text">My Feed Title</title>  
    <subtitle type="text">My Feed Description</subtitle>  
    <link rel="alternate" href="http://myfeeduri/" />  
  </source>  
</entry>  
```  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowany do RSS 2,0.  
  
```xml  
<item>  
  <guid isPermaLink="false">ItemID</guid>  
  <link>http://myitemuri/</link>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Jesper Aaberg</name>  
    <uri>http://Jesper/Aaberg</uri>  
    <email>Jesper@Aaberg.com</email>  
  </author>  
  <author xmlns="http://www.w3.org/2005/Atom">  
    <name>Syed Abbas</name>  
    <uri>http://Contoso/Abbas</uri>  
    <email>Syed.Abbas@contoso.com</email>  
  </author>  
  <category domain="categoryScheme">categoryName</category>  
  <category domain="categoryScheme">categoryName</category>  
  <title>Item Title</title>  
  <description>Item Summary</description>  
  <source>My Feed Title</source>  
  <pubDate>Wed, 29 Aug 2007 00:00:00 -0700</pubDate>  
  <updated xmlns="http://www.w3.org/2005/Atom">2007-08-29T14:07:09-07:00</updated>  
  <rights type="text" xmlns="http://www.w3.org/2005/Atom">Copyright 2007</rights>  
  <content type="text" xmlns="http://www.w3.org/2005/Atom">Item Content</content>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
  <contributor xmlns="http://www.w3.org/2005/Atom">  
    <name>Kim Abercrombie</name>  
    <uri>http://Contoso/Abercrombie</uri>  
    <email>Kim.Abercrombie@contoso.com</email>  
  </contributor>  
</item>  
```  
  
## <a name="syndicationperson"></a>SyndicationPerson  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.SyndicationPerson> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationPerson> jest serializowany do Atom 1,0.  
  
```xml  
  <author>  
    <name>Jesper Aaberg</name>  
    <uri>http://Contoso/Aaberg</uri>  
    <email>Jesper.Aaberg@contoso.com</email>  
  </author>  
<contributor>  
    <name>Lene Aaling</name>  
    <uri>http://Contoso/Aaling</uri>  
    <email>Lene.Aaling@contoso.com</email>  
  </contributor>  
```  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.SyndicationPerson> serializacji klasy do RSS 2,0, jeśli tylko jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje w `Authors` `Contributors` kolekcji lub.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.SyndicationPerson> serializacji klasy do kanału informacyjnego RSS 2,0, jeśli więcej niż jeden <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje `Authors` `Contributors` odpowiednio w kolekcji lub.  
  
```xml  
<a10:author>  
    <a10:name>Jesper Aaberg</a10:name>  
    <a10:uri>http://Contoso/Aaberg</a10:uri>  
    <a10:email>Jesper.Aaberg@contoso.com</a10:email>  
</a10:author>  
<a10:author>  
    <a10:name>Syed Abbas</a10:name>  
    <a10:uri>http://Contoso/Abbas</a10:uri>  
    <a10:email>Syed.Abbas@contoso.com</a10:email>  
</a10:author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
<a10:contributor>  
    <a10:name>Kim Abercrombie</a10:name>  
    <a10:uri>http://Contoso/Abercrombie</a10:uri>  
    <a10:email>Kim.Abercrombie@contoso.com</a10:email>  
</a10:contributor>  
```  
  
## <a name="syndicationlink"></a>SyndicationLink  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.SyndicationLink> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowany do Atom 1,0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowany do RSS 2,0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.SyndicationCategory> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowany do Atom 1,0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Poniższy kod XML pokazuje, jak <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowany do RSS 2,0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasę do Atom 1,0 i RSS 2,0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> tworzenia przy użyciu zawartości HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością HTML do Atom 1,0.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością HTML do RSS 2,0.  
  
 `<description><html> some html </html></description>`  
  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasę do Atom 1,0 i RSS 2,0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> tworzenia przy użyciu zwykłej zawartości tekstowej.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością w postaci zwykłego tekstu do Atom 1,0.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością w postaci zwykłego tekstu do RSS 2,0.  
  
 `<description>Some Plain Text</description>`  
  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasę do Atom 1,0 i RSS 2,0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> tworzenia przy użyciu zawartości XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością XHTML do Atom 1,0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.TextSyndicationContent> serializacji klasy z zawartością XHTML do RSS 2,0.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.UrlSyndicationContent> serializacji klasy do Atom 1,0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.UrlSyndicationContent> serializacji klasy z zawartością XHTML do RSS 2,0.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Poniższy przykład kodu pokazuje, jak serializować <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasę do Atom 1,0 i RSS 2,0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.XmlSyndicationContent> serializacji klasy do Atom 1,0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Poniższy kod XML przedstawia sposób <xref:System.ServiceModel.Syndication.XmlSyndicationContent> serializacji klasy z zawartością XHTML do RSS 2,0.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie syndykacji WCF](wcf-syndication-overview.md)
- [Architektura syndykacji](architecture-of-syndication.md)
- [Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS](how-to-create-a-basic-rss-feed.md)
- [Instrukcje: tworzenie podstawowego źródła danych Atom](how-to-create-a-basic-atom-feed.md)
- [Instrukcje: udostępnianie kanału informacyjnego w formatach Atom i RSS](how-to-expose-a-feed-as-both-atom-and-rss.md)
