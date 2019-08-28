---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 1fd873e02dcc1fc824c8b17c52231c80c61e7c60
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045483"
---
# <a name="strongly-typed-extensions-sample"></a>Przykład rozszerzeń z silną kontrolą typów
W przykładzie zastosowano <xref:System.ServiceModel.Syndication.SyndicationFeed> klasę do celów przykładu. Wzorce przedstawione w tym przykładzie mogą jednak być używane ze wszystkimi klasami zespalania, które obsługują dane rozszerzenia.  
  
 Model obiektów zespolonych (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>i powiązane klasy) obsługuje swobodny dostęp do danych <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> rozszerzenia przy użyciu właściwości i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> . Ten przykład pokazuje, jak zapewnić dostęp z ograniczonym dostępem do danych rozszerzenia przez zaimplementowanie niestandardowych <xref:System.ServiceModel.Syndication.SyndicationFeed> klas <xref:System.ServiceModel.Syndication.SyndicationItem> pochodnych i udostępnienie określonych rozszerzeń specyficznych dla aplikacji jako właściwości o jednoznacznie określonym typie.  
  
 Przykładem tego przykładu jest zaimplementowanie elementu Extension zdefiniowanego w proponowanym rozszerzeniu RFC. Jest to przeznaczone tylko do celów demonstracyjnych, a ten przykład nie jest pełną implementacją proponowanej specyfikacji.  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 Poniższy przykład kodu XML przedstawia wpis Atom 1,0 z dodatkowym `<in-reply-to>` elementem rozszerzenia.  
  
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
  
 Element określa trzy wymagane `type` atrybuty (`ref`i `href`), a jednocześnie umożliwia również obecność dodatkowych atrybutów rozszerzenia i elementów rozszerzenia. `<in-reply-to>`  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelowanie elementu w odpowiedzi  
 W tym przykładzie `<in-reply-to>` element jest modelowany jako CLR, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>, co umożliwia korzystanie z programu <xref:System.Runtime.Serialization.DataContractSerializer>z. Implementuje także niektóre metody i właściwości umożliwiające dostęp do danych elementu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 `Source` `MediaType` <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> Klasa implementuje właściwości dla wymaganego atrybutu (`HRef`,, i), a także kolekcje do zatrzymania i. `InReplyToElement`  
  
 `InReplyToElement` Klasa<xref:System.Xml.Serialization.IXmlSerializable> implementuje interfejs, który umożliwia bezpośrednią kontrolę nad sposobem odczytywania wystąpień obiektów z i zapisywania ich w kodzie XML. `HRef` `Ref` `Source`Metoda najpierw odczytuje wartości właściwości,, i`MediaType` z<xref:System.Xml.XmlReader>przenoszonegodoniego. `ReadXml` Wszystkie nieznane atrybuty są przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji. Gdy wszystkie atrybuty zostały odczytane, <xref:System.Xml.XmlReader.ReadStartElement> jest wywoływana, aby przewyższyć czytnik do następnego elementu. Ponieważ element modelowany przez tę klasę nie ma wymaganych elementów podrzędnych, elementy podrzędne są buforowane w `XElement` wystąpieniach i przechowywane <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> w kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 `WriteXml` `Ref` `HRef` `MediaType` W programie `Source``WriteXml` Metoda najpierw zapisuje wartości właściwości,,, i jako atrybuty XML (nie odpowiada za pisanie rzeczywistego elementu zewnętrznego `InReplyToElement` sama, jak to zostało zrobione przez obiekt wywołujący `WriteXml`). Zapisuje również zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do składnika zapisywania, jak pokazano w poniższym kodzie.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed i ThreadedItem  
 W przykładzie, `SyndicationItems` z `InReplyTo` rozszerzeniami `ThreadedItem` są modelowane przez klasę. Podobnie `ThreadedFeed` `ThreadedItem` Klasa`SyndicationFeed` jest klasą, której elementy to wszystkie wystąpienia.  
  
 Klasa dziedziczy z `SyndicationFeed` iprzesłonięcia`OnCreateItem` , aby zwrócić. `ThreadedItem` `ThreadedFeed` Implementuje także metodę uzyskiwania dostępu `Items` do kolekcji jako `ThreadedItems`, jak pokazano w poniższym kodzie.  
  
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
  
 Klasa `ThreadedItem` dziedziczy z `SyndicationItem` i tworzy `InReplyToElement` jako właściwość o jednoznacznie określonym typie. Zapewnia to wygodny programistyczny dostęp do `InReplyTo` danych rozszerzenia. Implementuje `TryParseElement` także i `WriteElementExtensions` odczytuje i zapisuje dane rozszerzenia, jak pokazano w poniższym kodzie.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
