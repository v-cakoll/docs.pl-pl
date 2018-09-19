---
title: Przykład rozszerzeń z silną kontrolą typów
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: eccb0ce240d01ab8592a44daddcfa7aa3d2023fb
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46006499"
---
# <a name="strongly-typed-extensions-sample"></a>Przykład rozszerzeń z silną kontrolą typów
W przykładzie użyto <xref:System.ServiceModel.Syndication.SyndicationFeed> klasy na potrzeby przykładu. Jednak wzorce przedstawiono w tym przykładzie może być używany ze wszystkimi klasy syndykacji, które obsługuje rozszerzenie danych.  
  
 Modelu obiektu syndykacji programu (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, i pokrewne klasy) obsługuje typowaniem luźnym dostęp do danych rozszerzenia za pomocą <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> właściwości. W tym przykładzie pokazano, jak udostępnić silnie typizowanych danych rozszerzenia poprzez implementację niestandardowej klasy pochodne klasy <xref:System.ServiceModel.Syndication.SyndicationFeed> i <xref:System.ServiceModel.Syndication.SyndicationItem> , udostępnić niektórych rozszerzeń specyficznych dla aplikacji jako silnie typizowane właściwości.  
  
 Na przykład ten przykład pokazuje sposób implementacji elementu rozszerzenia zdefiniowane w RFC proponowanych rozszerzeń wątkowości Atom. Jest to tylko w celach demonstracyjnych, a w tym przykładzie nie jest przeznaczony do pełnej implementacji specyfikacji proponowane.  
  
## <a name="sample-xml"></a>Przykładowy kod XML  
 W poniższym przykładzie XML przedstawiono wpisu Atom 1.0 przy użyciu dodatkowego `<in-reply-to>` elementu rozszerzenia.  
  
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
  
 `<in-reply-to>` Element określa trzy atrybuty wymagane (`ref`, `type` i `href`) zachowaniu obecności dodatkowych rozszerzeń atrybuty i elementy rozszerzenia.  
  
## <a name="modeling-the-in-reply-to-element"></a>Elementu w-Odpowiedz do modelowania  
 W tym przykładzie `<in-reply-to>` element ma formę CLR, który implementuje <xref:System.Xml.Serialization.IXmlSerializable>, które umożliwia korzystanie z <xref:System.Runtime.Serialization.DataContractSerializer>. Implementuje także niektóre metody i właściwości do uzyskiwania dostępu do elementu danych, jak pokazano w poniższym przykładowym kodzie.  
  
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
  
 `InReplyToElement` Klasa implementuje właściwości dla wymaganego atrybutu (`HRef`, `MediaType`, i `Source`) oraz kolekcji do przechowywania <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 `InReplyToElement` Klasy implementuje <xref:System.Xml.Serialization.IXmlSerializable> interfejs, który zezwala na bezpośrednią kontrolę nad wystąpienia obiektu są odczytywane i zapisywane do pliku XML. `ReadXml` Metoda najpierw odczytuje wartości `Ref`, `HRef`, `Source`, i `MediaType` właściwości z <xref:System.Xml.XmlReader> przekazany. Wszystkie nieznane atrybuty są przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> kolekcji. Po przeczytaniu wszystkie atrybuty <xref:System.Xml.XmlReader.ReadStartElement> jest wywoływana w celu przechodzenia czytnik do następnego elementu. Ponieważ element przez tę klasę w modelu nie ma wymaganych elementów podrzędnych, elementy podrzędne Pobierz buforowane do `XElement` wystąpień i przechowywane w <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> kolekcji, jak pokazano w poniższym kodzie.  
  
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
  
 W `WriteXml`, `InReplyToElement` metoda najpierw zapisuje się wartości `Ref`, `HRef`, `Source`, i `MediaType` właściwości jako atrybuty XML (`WriteXml` nie jest odpowiedzialne za zapisywanie rzeczywistego elementu zewnętrznego sam, jak realizowane przez obiekt wywołujący `WriteXml`). Usługa również zapisuje zawartość <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> i <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> w składniku zapisywania, jak pokazano w poniższym kodzie.  
  
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
 W tym przykładzie `SyndicationItems` z `InReplyTo` rozszerzenia są modelowane przy `ThreadedItem` klasy. Podobnie `ThreadedFeed` klasa jest `SyndicationFeed` których elementy są wszystkie wystąpienia elementu `ThreadedItem`.  
  
 `ThreadedFeed` Klasa dziedziczy `SyndicationFeed` i zastępuje `OnCreateItem` do zwrócenia `ThreadedItem`. Implementuje także metodę uzyskiwania dostępu do `Items` kolekcji jako `ThreadedItems`, jak pokazano w poniższym kodzie.  
  
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
  
 Klasa `ThreadedItem` dziedziczy `SyndicationItem` i sprawia, że `InReplyToElement` jako właściwość silnie typizowane. Zapewnia to wygodny dostęp programowy do `InReplyTo` rozszerzenia danych. Implementuje także `TryParseElement` i `WriteElementExtensions` do odczytywania i zapisywania jej danych rozszerzenia, jak pokazano w poniższym kodzie.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a>Zobacz też
