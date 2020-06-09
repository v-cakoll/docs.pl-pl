---
title: Przykład rozszerzeń z typowaniem luźnym
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 0a08ca19e5e6bff7223d45726617d2c2163ca3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591868"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="42e17-102">Przykład rozszerzeń z typowaniem luźnym</span><span class="sxs-lookup"><span data-stu-id="42e17-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="42e17-103">Model obiektów zespolonych zapewnia rozbudowaną obsługę pracy z danymi rozszerzenia — informacje, które znajdują się w reprezentacji XML zespolonego źródła danych, ale nie są jawnie uwidocznione przez klasy takie jak <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> .</span><span class="sxs-lookup"><span data-stu-id="42e17-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="42e17-104">Ten przykład ilustruje podstawowe techniki pracy z danymi rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="42e17-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="42e17-105">W przykładzie zastosowano <xref:System.ServiceModel.Syndication.SyndicationFeed> klasę do celów przykładu.</span><span class="sxs-lookup"><span data-stu-id="42e17-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="42e17-106">Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="42e17-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="42e17-107">Przykładowy kod XML</span><span class="sxs-lookup"><span data-stu-id="42e17-107">Sample XML</span></span>  
 <span data-ttu-id="42e17-108">W przypadku odwołania do tego przykładu jest używany następujący dokument XML.</span><span class="sxs-lookup"><span data-stu-id="42e17-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="42e17-109">Ten dokument zawiera następujące fragmenty danych rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="42e17-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="42e17-110">`myAttribute`Atrybut `<feed>` elementu.</span><span class="sxs-lookup"><span data-stu-id="42e17-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="42e17-111">`<simpleString>`postaci.</span><span class="sxs-lookup"><span data-stu-id="42e17-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="42e17-112">`<DataContractExtension>`postaci.</span><span class="sxs-lookup"><span data-stu-id="42e17-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="42e17-113">`<XmlSerializerExtension>`postaci.</span><span class="sxs-lookup"><span data-stu-id="42e17-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="42e17-114">`<xElementExtension>`postaci.</span><span class="sxs-lookup"><span data-stu-id="42e17-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="42e17-115">Zapisywanie danych rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="42e17-115">Writing Extension Data</span></span>  
 <span data-ttu-id="42e17-116">Rozszerzenia atrybutów są tworzone przez dodanie wpisów do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="42e17-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="42e17-117">Rozszerzenia elementów są tworzone przez dodanie wpisów do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="42e17-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="42e17-118">Rozszerzenia te mogą mieć wartości podstawowe, takie jak ciągi, serializacji XML obiektów .NET Framework lub węzły XML kodowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="42e17-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="42e17-119">Następujący przykładowy kod tworzy element rozszerzenia o nazwie `simpleString` .</span><span class="sxs-lookup"><span data-stu-id="42e17-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="42e17-120">Przestrzeń nazw XML dla tego elementu jest pustą przestrzenią nazw (""), a jej wartością jest węzeł tekstowy, który zawiera ciąg "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="42e17-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="42e17-121">Jednym ze sposobów tworzenia złożonych rozszerzeń elementów, które składają się z wielu zagnieżdżonych elementów jest użycie .NET Framework interfejsów API do serializacji ( <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> obsługiwane są zarówno, jak i), jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="42e17-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="42e17-122">W tym przykładzie są to `DataContractExtension` `XmlSerializerExtension` typy niestandardowe, które są zapisywane do użycia z serializatorem.</span><span class="sxs-lookup"><span data-stu-id="42e17-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="42e17-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection>Klasy można również użyć do tworzenia rozszerzeń elementów z <xref:System.Xml.XmlReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="42e17-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="42e17-124">Pozwala to na łatwą integrację z interfejsami API przetwarzania XML, takimi jak <xref:System.Xml.Linq.XElement> pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="42e17-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="42e17-125">Odczytywanie danych rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="42e17-125">Reading Extension Data</span></span>  
 <span data-ttu-id="42e17-126">Wartości rozszerzeń atrybutów można uzyskać, wyszukując atrybut w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji, <xref:System.Xml.XmlQualifiedName> tak jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="42e17-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="42e17-127">Rozszerzenia elementów są dostępne za pomocą `ReadElementExtensions<T>` metody.</span><span class="sxs-lookup"><span data-stu-id="42e17-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="42e17-128">Możliwe jest również uzyskanie dostępu do `XmlReader` poszczególnych rozszerzeń elementu przy użyciu <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.</span><span class="sxs-lookup"><span data-stu-id="42e17-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="42e17-129">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="42e17-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="42e17-130">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="42e17-131">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="42e17-132">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="42e17-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="42e17-133">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="42e17-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="42e17-134">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="42e17-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="42e17-135">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="42e17-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="42e17-136">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="42e17-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="42e17-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42e17-137">See also</span></span>

- [<span data-ttu-id="42e17-138">Rozszerzenia o jednoznacznie określonym typie</span><span class="sxs-lookup"><span data-stu-id="42e17-138">Strongly typed Extensions</span></span>](strongly-typed-extensions-sample.md)
- [<span data-ttu-id="42e17-139">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="42e17-139">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
