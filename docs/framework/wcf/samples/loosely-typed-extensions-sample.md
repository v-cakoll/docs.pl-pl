---
title: Przykład rozszerzeń z typowaniem luźnym
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: f3beed9b9ca1dd6b1d4bb32078e6cd35a636501c
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714869"
---
# <a name="loosely-typed-extensions-sample"></a>Przykład rozszerzeń z typowaniem luźnym
Model obiektów zespolonych zapewnia rozbudowaną obsługę pracy z danymi rozszerzenia — informacje, które znajdują się w reprezentacji XML zespolonego źródła danych, ale nie są jawnie uwidocznione przez klasy takie jak <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>. Ten przykład ilustruje podstawowe techniki pracy z danymi rozszerzenia.  
  
 Przykład używa klasy <xref:System.ServiceModel.Syndication.SyndicationFeed> w celu przeprowadzenia tej operacji. Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia:  
  
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
  
- Atrybut `myAttribute` elementu `<feed>`.  
  
- `<simpleString>` elementu.  
  
- `<DataContractExtension>` elementu.  
  
- `<XmlSerializerExtension>` elementu.  
  
- `<xElementExtension>` elementu.  
  
## <a name="writing-extension-data"></a>Zapisywanie danych rozszerzenia  
 Rozszerzenia atrybutów są tworzone przez dodanie wpisów do kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Rozszerzenia elementów są tworzone przez dodanie wpisów do kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>. Rozszerzenia te mogą mieć wartości podstawowe, takie jak ciągi, serializacji XML obiektów .NET Framework lub węzły XML kodowane ręcznie.  
  
 Następujący przykładowy kod tworzy element rozszerzenia o nazwie `simpleString`.  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Przestrzeń nazw XML dla tego elementu jest pustą przestrzenią nazw (""), a jej wartością jest węzeł tekstowy, który zawiera ciąg "Hello, World!".  
  
 Jednym ze sposobów tworzenia złożonych rozszerzeń elementów składających się z wielu zagnieżdżonych elementów jest użycie .NET Framework interfejsów API do serializacji (obsługiwane <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer>), jak pokazano w poniższych przykładach.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 W tym przykładzie `DataContractExtension` i `XmlSerializerExtension` są typami niestandardowymi zapisanymi do użycia z serializatorem.  
  
 Klasy <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> można również użyć do tworzenia rozszerzeń elementów z wystąpienia <xref:System.Xml.XmlReader>. Pozwala to na łatwą integrację z interfejsami API przetwarzania XML, takimi jak <xref:System.Xml.Linq.XElement>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Odczytywanie danych rozszerzenia  
 Wartości rozszerzeń atrybutów można uzyskać, wyszukując atrybut w kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> przez <xref:System.Xml.XmlQualifiedName>, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozszerzenia elementów są dostępne za pomocą metody `ReadElementExtensions<T>`.  
  
```csharp  
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
  
 Możliwe jest również uzyskanie `XmlReader` w poszczególnych rozszerzeniach elementów za pomocą metody <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader>.  
  
```csharp  
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
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzenia z silną kontrolą typów](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
