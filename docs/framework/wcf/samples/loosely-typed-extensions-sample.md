---
title: "Przykład rozszerzeń z typowaniem luźnym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 280445240dae215013069c65ab12b9e38227f5c1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="loosely-typed-extensions-sample"></a>Przykład rozszerzeń z typowaniem luźnym
W modelu obiektu syndykacji zapewnia sformatowanego obsługuje do pracy z danymi rozszerzenia — informacje, które znajduje się w zespolonego źródła danych jego reprezentacja w formacie XML, ale nie są jawnie udostępnianych przez klas takich jak <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>. W tym przykładzie przedstawiono podstawowe techniki do pracy z danymi rozszerzenia.  
  
 W przykładzie użyto <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy na potrzeby przykładu. Wzorce zostało to pokazane w tym przykładzie można jednak wszystkie klasy zespolonego, które obsługuje rozszerzenie danych:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 Odwołania następujący dokument XML jest używany w tym przykładzie.  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 Ten dokument zawiera następujące elementy danych rozszerzenia:  
  
-   `myAttribute` Atrybutu `<feed>` elementu.  
  
-   `<simpleString>`element.  
  
-   `<DataContractExtension>`element.  
  
-   `<XmlSerializerExtension>`element.  
  
-   `<xElementExtension>`element.  
  
## <a name="writing-extension-data"></a>Zapisywanie danych rozszerzenia  
 Atrybut rozszerzenia są tworzone przez dodanie wpisów <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji, jak pokazano w poniższym kodzie próbki.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Element rozszerzenia są tworzone przez dodanie wpisów <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji. Te rozszerzenia mogą przez podstawowe wartości, takie jak ciągi, serializations XML obiektów .NET Framework lub węzłów XML kodowane ręcznie.  
  
 Następujący przykładowy kod tworzy rozszerzenia elementu o nazwie `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Przestrzeń nazw XML dla tego elementu jest pusta przestrzeń nazw ("") i jego wartość wynosi węzeł tekstowy, który zawiera ciąg "hello, world!".  
  
 Aby utworzyć złożonego elementu rozszerzenia, które składają się z wielu elementów zagnieżdżonych jest korzystanie z interfejsów API architektury .NET Framework do serializacji (zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane) jak pokazano w poniższych przykładach.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 W tym przykładzie `DataContractExtension` i `XmlSerializerExtension` są zapisywane do użycia z serializatora typów niestandardowych.  
  
 <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Klasy może również służyć do tworzenia rozszerzenia elementu z <xref:System.Xml.XmlReader> wystąpienia. Dzięki temu Łatwa integracja z językiem XML przetwarzania interfejsów API, takich jak <xref:System.Xml.Linq.XElement> jak pokazano w poniższym kodzie próbki.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Odczytywanie danych rozszerzenia  
 Wartości dla atrybutu rozszerzeń można uzyskać przez wyszukanie atrybutu w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji przez jego <xref:System.Xml.XmlQualifiedName> jak pokazano w poniższym kodzie próbki.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Element rozszerzenia są dostępne przy użyciu `ReadElementExtensions<T>` metody.  
  
```  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 Istnieje również możliwość uzyskania `XmlReader` na pojedynczy element rozszerzenia przy użyciu <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzenia z silną kontrolą typów](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
