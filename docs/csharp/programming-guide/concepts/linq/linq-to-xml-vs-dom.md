---
title: LINQ to XML a DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 68d380873e71d767ddd60f8f9d0f4b82846d1371
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591768"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ to XML a DOM (C#)
W tej sekcji opisano niektóre kluczowe różnice [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] między programem a obecnym głównym interfejsem API programowania plików XML, W3C Document Object Model (dom).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nowe sposoby konstruowania drzew XML  
 W modelu W3C DOM utworzysz drzewo XML od dołu do góry. oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodasz elementy do dokumentu.  
  
 Na przykład poniżej przedstawiono typowy sposób tworzenia drzewa XML przy użyciu implementacji modelu DOM <xref:System.Xml.XmlDocument>firmy Microsoft:  
  
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
  
 Ten styl kodowania nie udostępnia wizualizacji więcej informacji o strukturze drzewa XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje to podejście do konstruowania drzewa XML, ale również obsługuje alternatywne podejście, *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna używa <xref:System.Xml.Linq.XElement> konstruktorów i <xref:System.Xml.Linq.XAttribute> do tworzenia drzewa XML.  
  
 Poniżej przedstawiono sposób konstruowania tego samego drzewa XML przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcji funkcjonalnej:  
  
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
  
 Zwróć uwagę, że Wcięcie kodu w celu skonstruowania drzewa XML pokazuje strukturę bazowego kodu XML.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XMLC#()](./linq-to-xml-overview.md).  
  
## <a name="working-directly-with-xml-elements"></a>Praca bezpośrednio z elementami XML  
 Gdy program jest używany w języku XML, główny fokus jest zazwyczaj na elementach XML i prawdopodobnie na atrybutach. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie można bezpośrednio korzystać z elementów i atrybutów XML. Można na przykład wykonać następujące czynności:  
  
- Utwórz elementy XML bez używania obiektu dokumentu. Upraszcza to programowanie, gdy trzeba będzie korzystać z fragmentów drzew XML.  
  
- Załaduj `T:System.Xml.Linq.XElement` obiekty bezpośrednio z pliku XML.  
  
- Serializacja `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.  
  
 Porównaj ten element z W3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML. W modelu DOM, węzły XML, w tym elementy i atrybuty, muszą zostać utworzone w kontekście dokumentu XML. Oto fragment kodu do utworzenia elementu Name w modelu DOM:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pozwala uniknąć tej warstwy złożoności.  
  
 W przypadku używania LINQ to XML <xref:System.Xml.Linq.XDocument> Klasa jest używana tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Uproszczona obsługa nazw i przestrzeni nazw  
 Obsługa nazw, przestrzeni nazw i prefiksów przestrzeni nazw jest ogólnie złożonym elementem programowania XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazwy i przestrzenie nazw, eliminując wymóg postępowania z prefiksami przestrzeni nazw. Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz. Ale jeśli zdecydujesz się nie jawnie kontrolować prefiksów przestrzeni nazw, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] program przypisze prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane, lub będzie serializować przy użyciu domyślnych przestrzeni nazw, jeśli nie. Jeśli są używane domyślne przestrzenie nazw, nie będzie żadnych prefiksów przestrzeni nazw w dokumencie będącym wynikiem. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
 Innym problemem z modelem DOM jest to, że nie pozwala na zmianę nazwy węzła. Zamiast tego należy utworzyć nowy węzeł i skopiować do niego wszystkie węzły podrzędne, tracąc oryginalną tożsamość węzła. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pozwala uniknąć tego problemu, umożliwiając ustawienie <xref:System.Xml.Linq.XName> właściwości w węźle.  
  
## <a name="static-method-support-for-loading-xml"></a>Obsługa metody statycznej do ładowania pliku XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia ładowanie XML przy użyciu metod statycznych zamiast metod instancji. Upraszcza to ładowanie i analizowanie. Aby uzyskać więcej informacji, zobacz [jak: Załaduj plik XML z plikuC#(](./how-to-load-xml-from-a-file.md)).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Usuwanie obsługi dla konstrukcji DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]bardziej upraszcza programowanie XML przez usunięcie obsługi jednostek i odwołań do jednostek. Zarządzanie jednostkami jest skomplikowane i rzadko jest używane. Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania. Po wypełnieniu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewa wszystkie jednostki DTD są rozwinięte.  
  
## <a name="support-for-fragments"></a>Obsługa fragmentów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie zapewnia równoważnej `XmlDocumentFragment` klasy. W wielu `XmlDocumentFragment` przypadkach koncepcje mogą być obsługiwane przez wynik zapytania, które zostało wpisane <xref:System.Xml.Linq.XNode>w <xref:System.Collections.Generic.IEnumerable%601> lub <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Obsługa elementu XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pomocą metod rozszerzających <xref:System.Xml.XPath?displayProperty=nameWithType> w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Obsługa białych znaków i wcięć  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje biały znak więcej niż w modelu DOM.  
  
 Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem. Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML. Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty. W żaden sposób nie trzeba zmieniać tego wcięcia. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie można to zrobić przez zachowanie białych znaków podczas ładowania lub analizowania kodu XML oraz wyłączanie formatowania podczas serializacji XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapisuje biały znak jako <xref:System.Xml.Linq.XText> węzeł, zamiast mieć wyspecjalizowany <xref:System.Xml.XmlNodeType.Whitespace> typ węzła, jak dom.  
  
## <a name="support-for-annotations"></a>Obsługa adnotacji  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]elementy obsługują rozszerzalny zestaw adnotacji. Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też innym rodzajem informacji specyficznych dla aplikacji. Aby uzyskać więcej informacji, zobacz [LINQ to XML adnotacje](./linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Obsługa informacji o schemacie  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę walidacji XSD za pomocą metod rozszerzających <xref:System.Xml.Schema?displayProperty=nameWithType> w przestrzeni nazw. Można sprawdzić, czy drzewo XML jest zgodne z XSD. Drzewo XML można wypełnić za pomocą sprawdzonych po walidacji schematu (PSVI). Aby uzyskać więcej informacji, zobacz [jak: Weryfikuj przy użyciu](./how-to-validate-using-xsd-linq-to-xml.md) XSD <xref:System.Xml.Schema.Extensions>i.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie (LINQ to XML)](./linq-to-xml-overview.md)
