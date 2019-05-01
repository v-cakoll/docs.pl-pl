---
title: Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
ms.openlocfilehash: b5a7f68edc49a02bb99ca05765d4582b798e72ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855208"
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS
Podczas tworzenia usługi syndykacji usługi Windows Communication Foundation (WCF), utworzyć źródła danych i elementów za pomocą następujących klas:  
  
- <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
- <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
- <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
- <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
- <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
- <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
- <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 Element <xref:System.ServiceModel.Syndication.SyndicationFeed> może być serializowany w dowolnym formacie syndykacji, dla którego zdefiniowano elementu formatującego. Usługi WCF jest dostarczany z dwóch elementów formatujących: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Model obiektów wokół <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> jest wyrównany dokładniej ze specyfikacją Atom 1.0 niż specyfikacji RSS 2.0. Jest to spowodowane Atom 1.0 jest bardziej znaczące specyfikacja, która definiuje elementy, które są niejednoznaczne lub pominięte ze specyfikacji RSS 2.0. W związku z tym wiele elementów w modelu obiektu syndykacji programu WCF mają nie bezpośrednie reprezentacji w specyfikacji RSS 2.0. Podczas serializacji <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> obiekty do RSS 2.0 WCF służy do serializacji elementów danych specyficznych dla Atom jako elementów kwalifikowaną przestrzenią nazw rozszerzeń, które są zgodne ze specyfikacją Atom. Można to kontrolować za pomocą parametru przekazanego do <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktora.  
  
 Przykłady kodu, w tym temacie jednej z dwóch metod zdefiniowane w tym miejscu to zrobić serializacji rzeczywistych.  
  
 `SerializeFeed` serializuje zespolonego źródła danych.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem` serializuje element syndykacji.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowana Atom 1.0.  
  
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
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowana RSS 2.0.  
  
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
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.SyndicationItem> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowana Atom 1.0.  
  
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
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowana RSS 2.0.  
  
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
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.SyndicationPerson> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationPerson> jest serializowana Atom 1.0.  
  
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
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationPerson> klasa jest serializowana RSS 2.0, jeśli istnieje tylko jedna <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje w `Authors` lub `Contributors` kolekcji, odpowiednio.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationPerson> klasa jest serializowana RSS 2.0, jeśli istnieje więcej niż jedna <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje w `Authors` lub `Contributors` kolekcji, odpowiednio.  
  
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
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.SyndicationLink> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowana Atom 1.0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowana RSS 2.0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.SyndicationCategory> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowana Atom 1.0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowana RSS 2.0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzona przy użyciu zawartość HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasie z atrybutem zawartość HTML jest serializowana Atom 1.0.  
  
 `<content type="html"><html> some html </html></content>`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasie z atrybutem zawartość HTML jest serializowana RSS 2.0.  
  
 `<description><html> some html </html></description>`  
  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzona przy użyciu zwykłego tekstu, zawartości.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy przy użyciu zwykłego tekstu, zawartości jest serializowana Atom 1.0.  
  
 `<content type="text">Some Plain Text</content>`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy przy użyciu zwykłego tekstu, zawartości jest serializowana RSS 2.0.  
  
 `<description>Some Plain Text</description>`  
  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzony z zawartością XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasa z zawartością XHTML jest serializowana Atom 1.0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasa z zawartością XHTML jest serializowana RSS 2.0.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasa jest serializowana Atom 1.0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasa z zawartością XHTML jest serializowana RSS 2.0.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Poniższy przykład kodu pokazuje jak do serializacji <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasa jest serializowana Atom 1.0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 XML pokazano sposób, w jaki <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasa z zawartością XHTML jest serializowana RSS 2.0.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)
- [Architektura syndykacji](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)
- [Instrukcje: Tworzenie podstawowego kanału informacyjnego RSS](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)
- [Instrukcje: Tworzenie podstawowego źródła danych Atom](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)
- [Instrukcje: Udostępnianie kanału informacyjnego w formatach Atom i RSS](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
