---
title: Przykład rozszerzeń z typowaniem luźnym
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 21690aebca250880a8eb51aee0821220a00bc0c0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039478"
---
# <a name="loosely-typed-extensions-sample"></a>Przykład rozszerzeń z typowaniem luźnym
Model obiektów zespolonych zapewnia rozbudowaną obsługę pracy z danymi rozszerzenia — informacje, które znajdują się w reprezentacji XML zespolonego źródła danych, ale nie są <xref:System.ServiceModel.Syndication.SyndicationFeed> jawnie <xref:System.ServiceModel.Syndication.SyndicationItem>uwidocznione przez klasy takie jak i. Ten przykład ilustruje podstawowe techniki pracy z danymi rozszerzenia.  
  
 W przykładzie zastosowano <xref:System.ServiceModel.Syndication.SyndicationFeed> klasę do celów przykładu. Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 W przypadku odwołania do tego przykładu jest używany następujący dokument XML.  
  
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
  
 Ten dokument zawiera następujące fragmenty danych rozszerzenia:  
  
- `myAttribute` Atrybut`<feed>` elementu.  
  
- `<simpleString>`postaci.  
  
- `<DataContractExtension>`postaci.  
  
- `<XmlSerializerExtension>`postaci.  
  
- `<xElementExtension>`postaci.  
  
## <a name="writing-extension-data"></a>Zapisywanie danych rozszerzenia  
 Rozszerzenia atrybutów są tworzone przez dodanie wpisów do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji, jak pokazano w poniższym przykładowym kodzie.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Rozszerzenia elementów są tworzone przez dodanie wpisów do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji. Rozszerzenia te mogą mieć wartości podstawowe, takie jak ciągi, serializacji XML obiektów .NET Framework lub węzły XML kodowane ręcznie.  
  
 Następujący przykładowy kod tworzy element rozszerzenia o nazwie `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Przestrzeń nazw XML dla tego elementu jest pustą przestrzenią nazw (""), a jej wartością jest węzeł tekstowy, który zawiera ciąg "Hello, World!".  
  
 Jednym ze sposobów tworzenia złożonych rozszerzeń elementów, które składają się z wielu zagnieżdżonych elementów jest użycie .NET Framework interfejsów API do serializacji ( <xref:System.Runtime.Serialization.DataContractSerializer> obsługiwane <xref:System.Xml.Serialization.XmlSerializer> są zarówno, jak i), jak pokazano w poniższych przykładach.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 W tym przykładzie `DataContractExtension` `XmlSerializerExtension` są to typy niestandardowe, które są zapisywane do użycia z serializatorem.  
  
 Klasy można również użyć do tworzenia rozszerzeń elementów <xref:System.Xml.XmlReader> z wystąpienia. <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Pozwala to na łatwą integrację z interfejsami API <xref:System.Xml.Linq.XElement> przetwarzania XML, takimi jak pokazano w poniższym przykładowym kodzie.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Odczytywanie danych rozszerzenia  
 Wartości rozszerzeń atrybutów można uzyskać, wyszukując atrybut w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji <xref:System.Xml.XmlQualifiedName> , tak jak pokazano w poniższym przykładowym kodzie.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozszerzenia elementów są dostępne za pomocą `ReadElementExtensions<T>` metody.  
  
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
  
 Możliwe jest również uzyskanie `XmlReader` dostępu do poszczególnych rozszerzeń elementu przy <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> użyciu metody.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzenia z silną kontrolą typów](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
