---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 10e5f2772b1d5cb9508f9e990cfd385d96096018
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33507616"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="d35aa-102">Przykład rozszerzeń z silną kontrolą typów</span><span class="sxs-lookup"><span data-stu-id="d35aa-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="d35aa-103">W przykładzie użyto <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy na potrzeby przykładu.</span><span class="sxs-lookup"><span data-stu-id="d35aa-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="d35aa-104">Jednak można wzorce zostało to pokazane w tym przykładzie wszystkie klasy zespolonego, które obsługuje rozszerzenie danych.</span><span class="sxs-lookup"><span data-stu-id="d35aa-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="d35aa-105">W modelu obiektu syndykacji (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, i związanych z klasy) obsługuje typowaniem luźnym dostęp do danych rozszerzenia przy użyciu <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d35aa-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="d35aa-106">W tym przykładzie pokazano, jak udostępnić jednoznacznie rozszerzenia danych dzięki implementacji niestandardowego klas pochodnych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> który udostępnić niektóre rozszerzenia specyficzne dla aplikacji jako typu właściwości.</span><span class="sxs-lookup"><span data-stu-id="d35aa-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="d35aa-107">Na przykład w tym przykładzie pokazano, jak można zaimplementować elementu rozszerzenia zdefiniowane w RFC proponowanych rozszerzenia wątkowość Atom.</span><span class="sxs-lookup"><span data-stu-id="d35aa-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="d35aa-108">To jest tylko w celach demonstracyjnych i w tym przykładzie nie ma być pełnej implementacji proponowanych specyfikacji.</span><span class="sxs-lookup"><span data-stu-id="d35aa-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="d35aa-109">Przykładowy kod XML</span><span class="sxs-lookup"><span data-stu-id="d35aa-109">Sample XML</span></span>  
 <span data-ttu-id="d35aa-110">W poniższym przykładzie XML zawiera wpis Atom 1.0 z dodatkowymi `<in-reply-to>` elementu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d35aa-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
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
  
 <span data-ttu-id="d35aa-111">`<in-reply-to>` Element określa trzy wymaganych atrybutów (`ref`, `type` i `href`) zachowaniu obecność rozszerzenia dodatkowe atrybuty i elementy rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d35aa-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="d35aa-112">Elementu In-Odpowiedz do modelowania</span><span class="sxs-lookup"><span data-stu-id="d35aa-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="d35aa-113">W tym przykładzie `<in-reply-to>` element ma formę CLR, która implementuje <xref:System.Xml.Serialization.IXmlSerializable>, który umożliwia jego korzystanie z <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d35aa-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="d35aa-114">Również implementuje niektórych metod i właściwości do uzyskiwania dostępu do elementu danych, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="d35aa-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="d35aa-115">`InReplyToElement` Klasa implementuje właściwości wymaganego atrybutu (`HRef`, `MediaType`, i `Source`) oraz kolekcje do przechowywania <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="d35aa-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="d35aa-116">`InReplyToElement` Klasa implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który umożliwia bezpośrednią kontrolę nad jak wystąpienia obiektu są odczytywane i zapisywane do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="d35aa-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="d35aa-117">`ReadXml` Metoda odczytuje najpierw wartości `Ref`, `HRef`, `Source`, i `MediaType` właściwości z <xref:System.Xml.XmlReader> przekazany do niego.</span><span class="sxs-lookup"><span data-stu-id="d35aa-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="d35aa-118">Nieznany atrybutów są przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d35aa-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="d35aa-119">Po przeczytaniu wszystkie atrybuty <xref:System.Xml.XmlReader.ReadStartElement> jest wywoływana, aby przejść do następnego elementu czytnika.</span><span class="sxs-lookup"><span data-stu-id="d35aa-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="d35aa-120">Ponieważ element formowane przez tę klasę nie ma wymaganych elementów podrzędnych, elementy podrzędne pobrać buforowane w `XElement` wystąpień i przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d35aa-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="d35aa-121">W `WriteXml`, `InReplyToElement` metody najpierw zapisuje limit wartości `Ref`, `HRef`, `Source`, i `MediaType` właściwości jako atrybuty XML (`WriteXml` nie jest odpowiedzialny za zapisywanie rzeczywistego elementu zewnętrznego sam, jak wykonać przez obiekt wywołujący `WriteXml`).</span><span class="sxs-lookup"><span data-stu-id="d35aa-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="d35aa-122">Również zapisuje zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> w składniku zapisywania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d35aa-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```  
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
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="d35aa-123">ThreadedFeed i ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="d35aa-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="d35aa-124">W przykładzie `SyndicationItems` z `InReplyTo` rozszerzenia są formowane przez `ThreadedItem` klasy.</span><span class="sxs-lookup"><span data-stu-id="d35aa-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="d35aa-125">Podobnie `ThreadedFeed` jest klasa `SyndicationFeed` którego elementy są wszystkie wystąpienia `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="d35aa-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="d35aa-126">`ThreadedFeed` Klasa dziedziczy `SyndicationFeed` i zastępuje `OnCreateItem` do zwrócenia `ThreadedItem`.</span><span class="sxs-lookup"><span data-stu-id="d35aa-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="d35aa-127">Implementuje również metody do uzyskiwania dostępu do `Items` kolekcji jako `ThreadedItems`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d35aa-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="d35aa-128">Klasa `ThreadedItem` dziedziczy `SyndicationItem` i sprawia, że `InReplyToElement` jako właściwość jednoznacznie.</span><span class="sxs-lookup"><span data-stu-id="d35aa-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="d35aa-129">Zapewnia to wygodny dostęp programistyczny umożliwiający `InReplyTo` danych rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d35aa-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="d35aa-130">Implementuje również `TryParseElement` i `WriteElementExtensions` do odczytywania i zapisywania ich rozszerzenia danych, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d35aa-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d35aa-131">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d35aa-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d35aa-132">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35aa-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d35aa-133">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35aa-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d35aa-134">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d35aa-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d35aa-135">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d35aa-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d35aa-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d35aa-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d35aa-137">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d35aa-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d35aa-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d35aa-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="d35aa-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d35aa-139">See Also</span></span>
