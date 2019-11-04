---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 5ee2f13df9d3c0841b3e8b62b1633ea4520d3860
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421512"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="1684d-102">Przykład rozszerzeń z silną kontrolą typów</span><span class="sxs-lookup"><span data-stu-id="1684d-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="1684d-103">Przykład używa klasy <xref:System.ServiceModel.Syndication.SyndicationFeed> w celu przeprowadzenia tej operacji.</span><span class="sxs-lookup"><span data-stu-id="1684d-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="1684d-104">Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1684d-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="1684d-105">Model obiektów zespolonych (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>i powiązane klasy) obsługuje swobodny dostęp do danych rozszerzenia przy użyciu <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1684d-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="1684d-106">Ten przykład pokazuje, jak zapewnić dostęp z ograniczonym dostępem do danych rozszerzenia przez zaimplementowanie niestandardowych klas pochodnych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>, które udostępniają określone rozszerzenia specyficzne dla aplikacji jako właściwości o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="1684d-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="1684d-107">Przykładem tego przykładu jest zaimplementowanie elementu Extension zdefiniowanego w proponowanym rozszerzeniu RFC.</span><span class="sxs-lookup"><span data-stu-id="1684d-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="1684d-108">Jest to przeznaczone tylko do celów demonstracyjnych, a ten przykład nie jest pełną implementacją proponowanej specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="1684d-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="1684d-109">Przykładowy kod XML</span><span class="sxs-lookup"><span data-stu-id="1684d-109">Sample XML</span></span>  
 <span data-ttu-id="1684d-110">Poniższy przykład kodu XML przedstawia wpis Atom 1,0 z dodatkowym elementem rozszerzenia `<in-reply-to>`.</span><span class="sxs-lookup"><span data-stu-id="1684d-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"   
                 p3:href="http://www.example.org/entries/1"   
                 p3:type="application/xhtml+xml"   
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"   
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="1684d-111">Element `<in-reply-to>` określa trzy wymagane atrybuty (`ref`, `type` i `href`), jednocześnie umożliwiając obecność dodatkowych atrybutów rozszerzenia i elementów rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="1684d-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="1684d-112">Modelowanie elementu w odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="1684d-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="1684d-113">W tym przykładzie element `<in-reply-to>` jest modelowany jako CLR implementujący <xref:System.Xml.Serialization.IXmlSerializable>, który umożliwia korzystanie z <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="1684d-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="1684d-114">Implementuje także niektóre metody i właściwości umożliwiające dostęp do danych elementu, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1684d-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =   
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,   
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="1684d-115">Klasa `InReplyToElement` implementuje właściwości dla wymaganego atrybutu (`HRef`, `MediaType`i `Source`), a także kolekcje do przechowywania <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="1684d-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="1684d-116">Klasa `InReplyToElement` implementuje interfejs <xref:System.Xml.Serialization.IXmlSerializable>, który umożliwia bezpośrednią kontrolę nad sposobem odczytywania wystąpień obiektów z i zapisywania ich w kodzie XML.</span><span class="sxs-lookup"><span data-stu-id="1684d-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="1684d-117">Metoda `ReadXml` najpierw odczytuje wartości właściwości `Ref`, `HRef`, `Source`i `MediaType` z przenoszonego <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="1684d-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="1684d-118">Wszystkie nieznane atrybuty są przechowywane w kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="1684d-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="1684d-119">Gdy wszystkie atrybuty zostały odczytane, <xref:System.Xml.XmlReader.ReadStartElement> jest wywoływana w celu przełączenia czytnika do następnego elementu.</span><span class="sxs-lookup"><span data-stu-id="1684d-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="1684d-120">Ponieważ element modelowany przez tę klasę nie ma wymaganych elementów podrzędnych, elementy podrzędne są buforowane w `XElement` wystąpieniach i przechowywane w kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1684d-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp  
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new   
                                 XmlQualifiedName(reader.LocalName,   
                                 reader.NamespaceURI),   
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="1684d-121">W `WriteXml`Metoda `InReplyToElement` najpierw zapisuje wartości właściwości `Ref`, `HRef`, `Source`i `MediaType` jako atrybuty XML (`WriteXml` nie odpowiada za zapisanie rzeczywistego elementu zewnętrznego. , tak jak to zostało wykonywane przez wywołującego `WriteXml`).</span><span class="sxs-lookup"><span data-stu-id="1684d-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="1684d-122">Zapisuje również zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do składnika zapisywania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1684d-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp  
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,   
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,   
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,   
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,   
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in   
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,   
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="1684d-123">ThreadedFeed i ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="1684d-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="1684d-124">W przykładzie `SyndicationItems` z rozszerzeniami `InReplyTo` są modelowane przez klasę `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="1684d-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="1684d-125">Podobnie Klasa `ThreadedFeed` jest `SyndicationFeed`, której elementy to wszystkie wystąpienia `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="1684d-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="1684d-126">Klasa `ThreadedFeed` dziedziczy po `SyndicationFeed` i przesłania `OnCreateItem` do zwrócenia `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="1684d-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="1684d-127">Implementuje także metodę uzyskiwania dostępu do kolekcji `Items` jako `ThreadedItems`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1684d-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp  
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="1684d-128">Klasa `ThreadedItem` dziedziczy po `SyndicationItem` i czyni `InReplyToElement` jako właściwość o jednoznacznie określonym typie.</span><span class="sxs-lookup"><span data-stu-id="1684d-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="1684d-129">Zapewnia to wygodny programistyczny dostęp do danych rozszerzenia `InReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="1684d-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="1684d-130">Implementuje również `TryParseElement` i `WriteElementExtensions` do odczytywania i zapisywania danych rozszerzenia, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1684d-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp  
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,   
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,   
                                                 string version)  
    {  
        if (this.InReplyTo != null &&   
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,   
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1684d-131">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="1684d-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1684d-132">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1684d-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1684d-133">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1684d-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1684d-134">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="1684d-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1684d-135">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1684d-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="1684d-136">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="1684d-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1684d-137">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1684d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1684d-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="1684d-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
