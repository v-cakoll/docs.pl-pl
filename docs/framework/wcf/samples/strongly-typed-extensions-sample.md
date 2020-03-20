---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 3cfbcddfdc7700618d499dd41d3a8c3b629bf550
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183315"
---
# <a name="strongly-typed-extensions-sample"></a>Przykład rozszerzeń z silną kontrolą typów
Przykład używa <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy do celów przykładu. Jednak wzorce zademonstrowane w tym przykładzie mogą być używane ze wszystkimi klasy syndykacji, które obsługują dane rozszerzenia.  
  
 Model obiektu Syndication<xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem>( , i powiązane klasy) obsługuje luźno typowany <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> dostęp do danych rozszerzenia przy użyciu właściwości i. W tym przykładzie pokazano, jak zapewnić silnie typisowany dostęp <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> do danych rozszerzenia, implementując niestandardowe klasy pochodne i które udostępniają niektóre rozszerzenia specyficzne dla aplikacji jako właściwości silnie typizowane.  
  
 Na przykład w tym przykładzie pokazano, jak zaimplementować element rozszerzenia zdefiniowane w proponowanych Atom Threading Extensions RFC. Ma to na celu wyłącznie demonstrację i próba ta nie ma być pełnym wdrożeniem proponowanej specyfikacji.  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 Poniższy przykład XML przedstawia wpis Atom 1.0 z dodatkowym `<in-reply-to>` elementem rozszerzenia.  
  
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
  
 Element `<in-reply-to>` określa trzy wymagane atrybuty `type` `href`(`ref`i ), a jednocześnie pozwala na obecność dodatkowych atrybutów rozszerzenia i elementów rozszerzenia.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelowanie elementu In-Reply-To  
 W tym przykładzie `<in-reply-to>` element jest modelowany jako <xref:System.Xml.Serialization.IXmlSerializable>CLR, który <xref:System.Runtime.Serialization.DataContractSerializer>implementuje , co umożliwia jego użycie z . Implementuje również niektóre metody i właściwości dostępu do danych elementu, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 Klasa `InReplyToElement` implementuje właściwości wymaganego atrybutu`HRef`( `MediaType`, `Source`, i ), a <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>także kolekcje do przechowywania i .  
  
 Klasa `InReplyToElement` implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który umożliwia bezpośrednią kontrolę nad tym, jak wystąpienia obiektów są odczytywane i zapisywane w formacie XML. Metoda `ReadXml` najpierw odczytuje wartości `Ref` `HRef`dla `Source`, `MediaType` , i <xref:System.Xml.XmlReader> właściwości z przekazanych do niego. Wszystkie nieznane atrybuty <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> są przechowywane w kolekcji. Gdy wszystkie atrybuty zostały <xref:System.Xml.XmlReader.ReadStartElement> odczytane, jest wywoływana, aby przejść czytnika do następnego elementu. Ponieważ element modelowany przez tę klasę nie ma wymaganych elementów podrzędnych, elementy podrzędne są buforowane w `XElement` wystąpieniach i przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W `WriteXml`, `InReplyToElement` metoda najpierw zapisuje wartości `Ref` `HRef`, `Source`, `MediaType` i właściwości jako`WriteXml` atrybuty XML ( nie jest odpowiedzialny za pisanie rzeczywistego `WriteXml`elementu zewnętrznego, jak to zrobić przez wywołującego ). Zapisuje również zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> do modułu zapisującego, jak pokazano w poniższym kodzie.  
  
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
 W próbce `SyndicationItems` `InReplyTo` z rozszerzeniami są `ThreadedItem` modelowane przez klasę. Podobnie `ThreadedFeed` klasa jest, `SyndicationFeed` którego elementy są wszystkie `ThreadedItem`wystąpienia .  
  
 Klasa `ThreadedFeed` dziedziczy `SyndicationFeed` i `OnCreateItem` zastępuje, aby `ThreadedItem`zwrócić . Implementuje również metodę dostępu do `Items` kolekcji, jak `ThreadedItems`pokazano w poniższym kodzie.  
  
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
  
 Klasa `ThreadedItem` dziedziczy `SyndicationItem` i `InReplyToElement` sprawia, że jako właściwości silnie typizowane. Zapewnia to wygodny programowy `InReplyTo` dostęp do danych rozszerzenia. Implementuje `TryParseElement` również `WriteElementExtensions` i do odczytu i zapisywania jego danych rozszerzenia, jak pokazano w poniższym kodzie.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
