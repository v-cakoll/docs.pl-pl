---
title: LINQ do XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168392"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ do XML vs. DOM (C#)
W tej sekcji opisano [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pewne kluczowe różnice między dominującym interfejsem API programowania XML, modelem obiektów dokumentu W3C (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nowe sposoby konstruowania drzew XML  
 W w3C DOM, można utworzyć drzewo XML od dołu do góry; oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodajesz elementy do dokumentu.  
  
 Na przykład, w następujący sposób, aby utworzyć drzewo XML przy <xref:System.Xml.XmlDocument>użyciu implementacji microsoft dom, :  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 Ten styl kodowania nie dostarcza wizualnie wiele informacji na temat struktury drzewa XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje to podejście do konstruowania drzewa XML, ale obsługuje również alternatywne podejście, *funkcjonalną konstrukcję.* Funkcjonalna konstrukcja <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> używa i konstruktorów do tworzenia drzewa XML.  
  
 Oto jak można skonstruować to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] samo drzewo XML przy użyciu konstrukcji funkcjonalnej:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Należy zauważyć, że wcięcie kodu do konstruowania drzewa XML pokazuje strukturę podstawowego xml.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md).  
  
## <a name="working-directly-with-xml-elements"></a>Praca bezpośrednio z elementami XML  
 Podczas programowania z XML, głównym celem jest zwykle na elementy XML i być może na atrybuty. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie można pracować bezpośrednio z elementami i atrybutami XML. Na przykład można wykonać następujące czynności:  
  
- Tworzenie elementów XML bez używania obiektu dokumentu w ogóle. Upraszcza to programowanie, gdy trzeba pracować z fragmentami drzew XML.  
  
- Załaduj `T:System.Xml.Linq.XElement` obiekty bezpośrednio z pliku XML.  
  
- Serializowanie `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.  
  
 Porównaj to z w3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML. W dom, węzły XML, w tym elementy i atrybuty, muszą być tworzone w kontekście dokumentu XML. Oto fragment kodu, aby utworzyć element nazwy w DOM:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]unika tej warstwy złożoności.  
  
 Korzystając z LINQ do XML, należy użyć <xref:System.Xml.Linq.XDocument> klasy tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Uproszczona obsługa nazw i przestrzeni nazw  
 Obsługa nazw, przestrzeni nazw i prefiksów obszaru nazw jest zazwyczaj złożoną częścią programowania XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazwy i przestrzenie nazw, eliminując wymóg zajmowania się prefiksami obszaru nazw. Jeśli chcesz kontrolować prefiksy obszaru nazw, możesz. Jeśli jednak zdecydujesz się nie jawnie sterować [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prefiksami obszaru nazw, przypisze prefiksy obszaru nazw podczas serializacji, jeśli są wymagane, lub serializuje przy użyciu domyślnych przestrzeni nazw, jeśli nie są. Jeśli używane są domyślne przestrzenie nazw, w dokumencie wynikowym nie będzie żadnych prefiksów obszaru nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Innym problemem z DOM jest to, że nie pozwala zmienić nazwę węzła. Zamiast tego należy utworzyć nowy węzeł i skopiować wszystkie węzły podrzędne do niego, tracąc oryginalną tożsamość węzła. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]unika tego problemu, umożliwiając ustawienie <xref:System.Xml.Linq.XName> właściwości w węźle.  
  
## <a name="static-method-support-for-loading-xml"></a>Obsługa metod statycznych dla ładowania XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia ładowanie języka XML przy użyciu metod statycznych zamiast metod instancji. Upraszcza to ładowanie i analizowanie. Aby uzyskać więcej informacji, zobacz [Jak załadować xml z pliku (C#)](./how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Usuwanie wsparcia konstrukcji DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dodatkowo upraszcza programowanie XML poprzez usunięcie obsługi jednostek i odniesień do jednostek. Zarządzanie jednostkami jest złożone i jest rzadko używane. Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania. Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewo jest wypełniane, wszystkie jednostki DTD są rozwinięte.  
  
## <a name="support-for-fragments"></a>Obsługa fragmentów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie zapewnia odpowiednika `XmlDocumentFragment` dla klasy. W wielu przypadkach jednak `XmlDocumentFragment` pojęcie może być obsługiwane przez wynik kwerendy, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode>która <xref:System.Collections.Generic.IEnumerable%601> jest <xref:System.Xml.Linq.XElement>wpisana jako , lub .  
  
## <a name="support-for-xpathnavigator"></a>Obsługa xpathnavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę za <xref:System.Xml.XPath.XPathNavigator> pośrednictwem <xref:System.Xml.XPath?displayProperty=nameWithType> metod rozszerzenia w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Obsługa odstępów i wcięć  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje biały znak w prostszy sposób niż DOM.  
  
 Typowym scenariuszem jest odczyt wciętego kodu XML, utworzenie drzewa XML w pamięci bez żadnych węzłów tekstu odstępu (czyli nie zachowanie odstępu), wykonanie niektórych operacji w pliku XML, a następnie zapisanie kodu XML z wcięciem. Podczas serializacji XML z formatowaniem zachowano tylko znaczące odstępy w drzewie XML. Jest to domyślne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zachowanie dla .  
  
 Innym typowym scenariuszem jest odczytywanie i modyfikowanie języka XML, który został już celowo wcięty. W jakikolwiek sposób możesz nie chcieć zmienić tego wcięcia. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przypadku , można to zrobić, zachowując biały znak podczas ładowania lub analizowania XML i wyłączania formatowania podczas serializacji XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przechowuje biały znak <xref:System.Xml.Linq.XText> jako węzeł, zamiast <xref:System.Xml.XmlNodeType.Whitespace> mieć typ węzła specjalistycznego, tak jak dom.  
  
## <a name="support-for-annotations"></a>Obsługa adnotacji  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]elementy obsługują rozszerzalny zestaw adnotacji. Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też inny rodzaj informacji specyficznych dla aplikacji. Aby uzyskać więcej informacji, zobacz [LINQ do XML Adnotacje](./linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Obsługa informacji o schemacie  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę sprawdzania poprawności XSD <xref:System.Xml.Schema?displayProperty=nameWithType> za pomocą metod rozszerzenia w przestrzeni nazw. Można sprawdzić, czy drzewo XML jest zgodne z XSD. Drzewo XML można wypełnić zestawem informacji po weryfikacji schematu (PSVI). Aby uzyskać więcej informacji, zobacz Jak <xref:System.Xml.Schema.Extensions>sprawdzić [poprawność przy użyciu XSD](./how-to-validate-using-xsd-linq-to-xml.md) i .
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie (LINQ to XML)](./linq-to-xml-overview.md)
