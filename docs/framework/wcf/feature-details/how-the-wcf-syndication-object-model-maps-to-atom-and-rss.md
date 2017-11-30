---
title: "Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0365eb37-98cc-4b13-80fb-f1e78847a748
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e6af3dc911cdf67e7290d339122821c00fe6bc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-the-wcf-syndication-object-model-maps-to-atom-and-rss"></a>Sposób mapowania modelu obiektu syndykacji programu WCF na kanały informacyjne Atom i RSS
Podczas tworzenia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługa syndykacji tworzenia źródła danych i elementy przy użyciu następujących klas:  
  
-   <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
-   <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
-   <xref:System.ServiceModel.Syndication.TextSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.UrlSyndicationContent>  
  
-   <xref:System.ServiceModel.Syndication.XmlSyndicationContent>  
  
 A <xref:System.ServiceModel.Syndication.SyndicationFeed> może być Zserializowany, w dowolnym formacie zespolonego, dla którego zdefiniowano elementu formatującego. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jest dostarczany z dwóch elementów formatujących: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter> i <xref:System.ServiceModel.Syndication.Rss20FeedFormatter>.  
  
 Model obiektów wokół <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> jest wyrównany dokładniejsze ze specyfikacją Atom 1.0 niż specyfikacji RSS 2.0. Jest to spowodowane Atom 1.0 to bardziej znaczące Specyfikacja definiujący elementy, które są niejednoznaczne lub pominięte ze specyfikacji RSS 2.0. W związku z tym wiele elementów w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelu obiektu syndykacji ma nie bezpośrednie reprezentacji w specyfikacji RSS 2.0. Podczas serializowania <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> obiektów do RSS 2.0 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] służy do serializacji elementów danych specyficznych dla Atom jako elementów kwalifikowana przestrzeni nazw rozszerzeń, które są zgodne ze specyfikacją Atom. Użytkownik może sterować za pomocą parametr przekazany do <xref:System.ServiceModel.Syndication.Rss20FeedFormatter> konstruktora.  
  
 Przykłady kodu, w tym temacie jednej z dwóch metod zdefiniowane w tym miejscu do rzeczywistego serializacji.  
  
 `SerializeFeed`serializuje zespolonego źródła danych.  
  
 [!code-csharp[SyndicationMapping#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#10)]
 [!code-vb[SyndicationMapping#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#10)]  
  
 `SerializeItem`serializuje elementu zespolonego.  
  
 [!code-csharp[SyndicationMapping#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#11)]
 [!code-vb[SyndicationMapping#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#11)]  
  
## <a name="syndicationfeed"></a>SyndicationFeed  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#0)]
 [!code-vb[SyndicationMapping#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#0)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowany Atom 1.0.  
  
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
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationFeed> jest serializowany RSS 2.0.  
  
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
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.SyndicationItem> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#1)]
 [!code-vb[SyndicationMapping#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#1)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowany Atom 1.0.  
  
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
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationItem> jest serializowany RSS 2.0.  
  
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
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.SyndicationPerson> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#2)]
 [!code-vb[SyndicationMapping#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#2)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationPerson> jest serializowany Atom 1.0.  
  
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
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationPerson> klasy jest serializowany RSS 2.0, jeśli istnieje tylko jedna <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje w `Authors` lub `Contributors` kolekcje, odpowiednio.  
  
```xml  
<author>Jesper.Aaberg@contoso.com</author>  
<a10:contributor>  
    <a10:name>Lene Aaling</a10:name>  
    <a10:uri>http://Contoso/Aaling</a10:uri>  
    <a10:email>Lene.Aaling@contoso.com</a10:email>  
</a10:contributor>  
```  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationPerson> klasy jest serializowany RSS 2.0, jeśli istnieje więcej niż jedna <xref:System.ServiceModel.Syndication.SyndicationPerson> istnieje w `Authors` lub `Contributors` kolekcje, odpowiednio.  
  
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
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.SyndicationLink> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#3)]
 [!code-vb[SyndicationMapping#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#3)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowany Atom 1.0.  
  
 `<link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationLink> jest serializowany RSS 2.0.  
  
 `<a10:link rel="alternate" type="text/html" title="My Link Title" length="2048" href="http://contoso/MyLink" />`  
  
## <a name="syndicationcategory"></a>SyndicationCategory  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.SyndicationCategory> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#4)]
 [!code-vb[SyndicationMapping#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#4)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowany Atom 1.0.  
  
 `<category term="categoryName" label="categoryLabel" scheme="categoryScheme" />`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.SyndicationCategory> jest serializowany RSS 2.0.  
  
 `<category domain="categoryScheme">categoryName</category>`  
  
## <a name="textsyndicationcontent"></a>TextSyndicationContent  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzony z zawartość HTML.  
  
 [!code-csharp[SyndicationMapping#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#5)]
 [!code-vb[SyndicationMapping#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#5)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością HTML jest serializowany Atom 1.0.  
  
 `<content type="html"><html> some html </html></content>`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością HTML jest serializowany RSS 2.0.  
  
 `<description><html> some html </html></description>`  
  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzony z zawartością w postaci zwykłego tekstu.  
  
 [!code-csharp[SyndicationMapping#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#6)]
 [!code-vb[SyndicationMapping#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#6)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością w postaci zwykłego tekstu jest serializowany Atom 1.0.  
  
 `<content type="text">Some Plain Text</content>`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością w postaci zwykłego tekstu jest serializowany RSS 2.0.  
  
 `<description>Some Plain Text</description>`  
  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy Atom 1.0 i RSS 2.0 podczas <xref:System.ServiceModel.Syndication.TextSyndicationContent> jest tworzony z zawartością XHTML.  
  
 [!code-csharp[SyndicationMapping#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#7)]
 [!code-vb[SyndicationMapping#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#7)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością XHTML jest serializowany Atom 1.0.  
  
 `<content type="xhtml">`  
  
 `<html> some xhtml </html>`  
  
 `</content>`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.TextSyndicationContent> klasy z zawartością XHTML jest serializowany RSS 2.0.  
  
 `<description><html> some xhtml </html></description>`  
  
## <a name="urlsyndicationcontent"></a>UrlSyndicationContent  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#8)]
 [!code-vb[SyndicationMapping#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#8)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasy jest serializowany Atom 1.0.  
  
 `<content type="audio" src="http://someurl/" />`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.UrlSyndicationContent> klasy z zawartością XHTML jest serializowany RSS 2.0.  
  
 `<description />`  
  
 `<content type="audio" src="http://Contoso/someurl/" xmlns="http://www.w3.org/2005/Atom" />`  
  
## <a name="xmlsyndicationcontent"></a>XmlSyndicationContent  
 Poniższy przykładowy kod przedstawia sposób serializacji <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasy Atom 1.0 i RSS 2.0.  
  
 [!code-csharp[SyndicationMapping#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/syndicationmapping/cs/snippets.cs#9)]
 [!code-vb[SyndicationMapping#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/syndicationmapping/vb/snippets.vb#9)]  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasy jest serializowany Atom 1.0.  
  
 `<content type="mytype">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
 Poniżej przedstawiono XML jak <xref:System.ServiceModel.Syndication.XmlSyndicationContent> klasy z zawartością XHTML jest serializowany RSS 2.0.  
  
 `<content type="mytype" xmlns="http://www.w3.org/2005/Atom">`  
  
 `<SomeData xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/FeedMapping" />`  
  
 `</content>`  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie syndykacji WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 [Architektura syndykacji](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 [Porady: Tworzenie podstawowego kanału informacyjnego RSS](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 [Porady: Tworzenie podstawowego źródła danych Atom](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 [Porady: udostępnianie źródło danych jako Atom i RSS](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)
