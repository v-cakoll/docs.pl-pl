---
title: Przykład rozszerzeń z typowaniem luźnym
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: f46cf3dfcdb60669f0a02337b54de97d4af3efdc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042195"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="9ec9c-102">Przykład rozszerzeń z typowaniem luźnym</span><span class="sxs-lookup"><span data-stu-id="9ec9c-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="9ec9c-103">Modelu obiektu syndykacji programu zawiera, zaawansowana obsługa Praca z danymi rozszerzenia — informacje, które są obecne w kanał w reprezentacji XML, ale nie zostały jawnie udostępnianych przez klasy takie jak <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="9ec9c-104">W tym przykładzie przedstawiono podstawowe techniki do pracy z danymi rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="9ec9c-105">W przykładzie użyto <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy na potrzeby przykładu.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="9ec9c-106">Jednak wzorce przedstawiono w tym przykładzie może być używany ze wszystkimi klasy syndykacji, które obsługuje rozszerzenie danych:</span><span class="sxs-lookup"><span data-stu-id="9ec9c-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="9ec9c-107">Przykładowy kod XML</span><span class="sxs-lookup"><span data-stu-id="9ec9c-107">Sample XML</span></span>  
 <span data-ttu-id="9ec9c-108">Odwołanie następujący dokument XML jest używany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="9ec9c-109">Ten dokument zawiera następujące elementy danych rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="9ec9c-109">This document contains the following pieces of extension data:</span></span>  
  
-   <span data-ttu-id="9ec9c-110">`myAttribute` Atrybutu `<feed>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
-   <span data-ttu-id="9ec9c-111">`<simpleString>` element.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-111">`<simpleString>` element.</span></span>  
  
-   <span data-ttu-id="9ec9c-112">`<DataContractExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-112">`<DataContractExtension>` element.</span></span>  
  
-   <span data-ttu-id="9ec9c-113">`<XmlSerializerExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-113">`<XmlSerializerExtension>` element.</span></span>  
  
-   <span data-ttu-id="9ec9c-114">`<xElementExtension>` element.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="9ec9c-115">Zapisywanie danych rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="9ec9c-115">Writing Extension Data</span></span>  
 <span data-ttu-id="9ec9c-116">Atrybut rozszerzenia są tworzone przez dodanie pozycji do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="9ec9c-117">Element rozszerzenia są tworzone przez dodanie pozycji do <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="9ec9c-118">Te rozszerzenia mogą przez podstawowe wartości, takich jak ciągi, serializations XML obiektów .NET Framework lub węzłów XML kodowane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="9ec9c-119">Następujący przykładowy kod tworzy element rozszerzenia o nazwie `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="9ec9c-120">Przestrzeń nazw XML dla tego elementu jest pusta przestrzeń nazw (""), a jego wartość to węzeł tekstowy, który zawiera ciąg "hello, world!".</span><span class="sxs-lookup"><span data-stu-id="9ec9c-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="9ec9c-121">Jednym ze sposobów, aby utworzyć rozszerzeń elementów, które składają się z wielu elementów zagnieżdżonych jest użycie interfejsów API programu .NET Framework do serializacji (zarówno <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> są obsługiwane) jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="9ec9c-122">W tym przykładzie `DataContractExtension` i `XmlSerializerExtension` są zapisywane do użycia z serializatora typów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="9ec9c-123"><xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> Klasy może również służyć do tworzenia rozszerzenia elementu z <xref:System.Xml.XmlReader> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="9ec9c-124">Dzięki temu łatwą integrację z danymi XML przetwarzania interfejsów API, takich jak <xref:System.Xml.Linq.XElement> jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="9ec9c-125">Odczytywanie danych rozszerzenia</span><span class="sxs-lookup"><span data-stu-id="9ec9c-125">Reading Extension Data</span></span>  
 <span data-ttu-id="9ec9c-126">Wartości dla atrybutów rozszerzeń można uzyskać, sprawdzając atrybutu w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji przez jego <xref:System.Xml.XmlQualifiedName> jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="9ec9c-127">Element rozszerzenia są dostępne przy użyciu `ReadElementExtensions<T>` metody.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="9ec9c-128">Istnieje również możliwość uzyskania `XmlReader` na pojedynczego elementu rozszerzenia za pomocą <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> metody.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ec9c-129">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="9ec9c-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9ec9c-130">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ec9c-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9ec9c-131">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ec9c-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9ec9c-132">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ec9c-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9ec9c-133">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ec9c-134">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="9ec9c-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9ec9c-135">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ec9c-136">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9ec9c-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="9ec9c-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ec9c-137">See Also</span></span>  
 [<span data-ttu-id="9ec9c-138">Rozszerzenia z silną kontrolą typów</span><span class="sxs-lookup"><span data-stu-id="9ec9c-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [<span data-ttu-id="9ec9c-139">Syndykacja programu WCF</span><span class="sxs-lookup"><span data-stu-id="9ec9c-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
