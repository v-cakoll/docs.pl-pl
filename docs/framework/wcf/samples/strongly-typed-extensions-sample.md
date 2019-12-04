---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 4ad0a8e10ecbcb5e3ddf9106dbbaa55356314020
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716620"
---
# <a name="strongly-typed-extensions-sample"></a>Przykład rozszerzeń z silną kontrolą typów
Przykład używa klasy <xref:System.ServiceModel.Syndication.SyndicationFeed> w celu przeprowadzenia tej operacji. Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia.  
  
 Model obiektów zespolonych (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>i powiązane klasy) obsługuje swobodny dostęp do danych rozszerzenia przy użyciu <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> właściwości. Ten przykład pokazuje, jak zapewnić dostęp z ograniczonym dostępem do danych rozszerzenia przez zaimplementowanie niestandardowych klas pochodnych <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem>, które udostępniają określone rozszerzenia specyficzne dla aplikacji jako właściwości o jednoznacznie określonym typie.  
  
 Przykładem tego przykładu jest zaimplementowanie elementu Extension zdefiniowanego w proponowanym rozszerzeniu RFC. Jest to przeznaczone tylko do celów demonstracyjnych, a ten przykład nie jest pełną implementacją proponowanej specyfikacji.  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 Poniższy przykład kodu XML przedstawia wpis Atom 1,0 z dodatkowym elementem rozszerzenia `<in-reply-to>`.  
  
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
  
 Element `<in-reply-to>` określa trzy wymagane atrybuty (`ref`, `type` i `href`), jednocześnie umożliwiając obecność dodatkowych atrybutów rozszerzenia i elementów rozszerzenia.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelowanie elementu w odpowiedzi  
 W tym przykładzie element `<in-reply-to>` jest modelowany jako CLR implementujący <xref:System.Xml.Serialization.IXmlSerializable>, który umożliwia korzystanie z <xref:System.Runtime.Serialization.DataContractSerializer>. Implementuje także niektóre metody i właściwości umożliwiające dostęp do danych elementu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Klasa `InReplyToElement` implementuje właściwości dla wymaganego atrybutu (`HRef`, `MediaType`i `Source`), a także kolekcje do przechowywania <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 Klasa `InReplyToElement` implementuje interfejs <xref:System.Xml.Serialization.IXmlSerializable>, który umożliwia bezpośrednią kontrolę nad sposobem odczytywania wystąpień obiektów z i zapisywania ich w kodzie XML. Metoda `ReadXml` najpierw odczytuje wartości właściwości `Ref`, `HRef`, `Source`i `MediaType` z przenoszonego <xref:System.Xml.XmlReader>. Wszystkie nieznane atrybuty są przechowywane w kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A>. Gdy wszystkie atrybuty zostały odczytane, <xref:System.Xml.XmlReader.ReadStartElement> jest wywoływana w celu przełączenia czytnika do następnego elementu. Ponieważ element modelowany przez tę klasę nie ma wymaganych elementów podrzędnych, elementy podrzędne są buforowane w `XElement` wystąpieniach i przechowywane w kolekcji <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>, jak pokazano w poniższym kodzie.  
  
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
  
 W `WriteXml`Metoda `InReplyToElement` najpierw zapisuje wartości właściwości `Ref`, `HRef`, `Source`i `MediaType` jako atrybuty XML (`WriteXml` nie odpowiada za zapisanie rzeczywistego elementu zewnętrznego, jak to zostało wykonane przez wywołujący `WriteXml`). Zapisuje również zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do składnika zapisywania, jak pokazano w poniższym kodzie.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed i ThreadedItem  
 W przykładzie `SyndicationItems` z rozszerzeniami `InReplyTo` są modelowane przez klasę `ThreadedItem`. Podobnie Klasa `ThreadedFeed` jest `SyndicationFeed`, której elementy to wszystkie wystąpienia `ThreadedItem`.  
  
 Klasa `ThreadedFeed` dziedziczy po `SyndicationFeed` i przesłania `OnCreateItem` do zwrócenia `ThreadedItem`. Implementuje także metodę uzyskiwania dostępu do kolekcji `Items` jako `ThreadedItems`, jak pokazano w poniższym kodzie.  
  
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
  
 Klasa `ThreadedItem` dziedziczy po `SyndicationItem` i czyni `InReplyToElement` jako właściwość o jednoznacznie określonym typie. Zapewnia to wygodny programistyczny dostęp do danych rozszerzenia `InReplyTo`. Implementuje również `TryParseElement` i `WriteElementExtensions` do odczytywania i zapisywania danych rozszerzenia, jak pokazano w poniższym kodzie.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
