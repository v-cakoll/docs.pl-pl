---
title: Przykład rozszerzeń z typowaniem luźnym
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: b8d1d42864b8764551cc44a26d820090eb28971e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183549"
---
# <a name="loosely-typed-extensions-sample"></a>Przykład rozszerzeń z typowaniem luźnym
Model obiektu Syndication zapewnia bogatą obsługę pracy z danymi rozszerzenia — informacje, które są obecne w reprezentacji XML źródła syndykacji, ale nie są jawnie udostępniane przez klasy, takie jak <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>. W tym przykładzie przedstawiono podstawowe techniki pracy z danymi rozszerzenia.  
  
 Przykład używa <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy do celów przykładu. Jednak wzorce zademonstrowane w tym przykładzie mogą być używane ze wszystkimi klasami syndykacji, które obsługują dane rozszerzenia:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 W tym przykładzie użyto następującego dokumentu XML.  
  
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
  
- Atrybut `myAttribute` `<feed>` elementu.  
  
- `<simpleString>`Element.  
  
- `<DataContractExtension>`Element.  
  
- `<XmlSerializerExtension>`Element.  
  
- `<xElementExtension>`Element.  
  
## <a name="writing-extension-data"></a>Zapisywanie danych rozszerzenia  
 Rozszerzenia atrybutów są tworzone przez dodanie <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> wpisów do kolekcji, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Rozszerzenia elementu są tworzone przez dodanie <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> wpisów do kolekcji. Rozszerzenia te mogą przez podstawowe wartości, takie jak ciągi, serializacji XML obiektów .NET Framework lub węzłów XML kodowane ręcznie.  
  
 Poniższy przykładowy kod tworzy `simpleString`element rozszerzenia o nazwie .  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 Obszar nazw XML dla tego elementu jest pustą przestrzenią nazw (""), a jego wartość jest węzłem tekstowym zawierającym ciąg "hello, world!".  
  
 Jednym ze sposobów tworzenia złożonych rozszerzeń elementów, które składają się z wielu elementów zagnieżdżonych jest użycie interfejsów API programu .NET Framework do serializacji (zarówno <xref:System.Runtime.Serialization.DataContractSerializer> są obsługiwane, jak pokazano <xref:System.Xml.Serialization.XmlSerializer> w poniższych przykładach.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 W tym `DataContractExtension` przykładzie `XmlSerializerExtension` i są typy niestandardowe napisane do użycia z serializatora.  
  
 Klasa <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> może również służyć do tworzenia rozszerzeń elementów z wystąpienia. <xref:System.Xml.XmlReader> Pozwala to na łatwą integrację <xref:System.Xml.Linq.XElement> z interfejsami API przetwarzania XML, takich jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Odczyt danych rozszerzenia  
 Wartości dla rozszerzeń atrybutów można uzyskać, wyszukując atrybut w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji przez jego, <xref:System.Xml.XmlQualifiedName> jak pokazano w poniższym przykładowym kodzie.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Rozszerzenia elementu są dostępne `ReadElementExtensions<T>` przy użyciu metody.  
  
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
  
 Możliwe jest również uzyskanie `XmlReader` w poszczególnych rozszerzeniach <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> elementu przy użyciu metody.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Zobacz też

- [Rozszerzenia z silną kontrolą typów](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Syndykacja programu WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
