---
title: LINQ to XML a DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: b25993fba4d878beb881dfdc46effe5a8ab3485b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331700"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML a DOM (Visual Basic)
W tej sekcji opisano niektóre kluczowe różnice między [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i aktualnym głównym interfejsem API programowania plików XML, W3C Document Object Model (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nowe sposoby konstruowania drzew XML  
 W modelu W3C DOM utworzysz drzewo XML od dołu do góry. oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodasz elementy do dokumentu.  
  
 Na przykład poniżej przedstawiono typowy sposób tworzenia drzewa XML przy użyciu implementacji modelu DOM firmy Microsoft <xref:System.Xml.XmlDocument>:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 Ten styl kodowania nie udostępnia wizualizacji więcej informacji o strukturze drzewa XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje to podejście do konstruowania drzewa XML, ale również obsługuje alternatywne podejście, *konstrukcja funkcjonalna*. W Visual Basic, konstrukcja funkcjonalna używa literałów XML do tworzenia drzewa XML.  
  
 Poniżej przedstawiono sposób konstruowania tego samego drzewa XML przy użyciu konstrukcji funkcjonalnej [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]:  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Zwróć uwagę, że Wcięcie kodu w celu skonstruowania drzewa XML pokazuje strukturę bazowego kodu XML.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Praca bezpośrednio z elementami XML  
 Gdy program jest używany w języku XML, główny fokus jest zazwyczaj na elementach XML i prawdopodobnie na atrybutach. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można bezpośrednio korzystać z elementów i atrybutów XML. Można na przykład wykonać następujące czynności:  
  
- Utwórz elementy XML bez używania obiektu dokumentu. Upraszcza to programowanie, gdy trzeba będzie korzystać z fragmentów drzew XML.  
  
- Załaduj obiekty `T:System.Xml.Linq.XElement` bezpośrednio z pliku XML.  
  
- Serializacja `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.  
  
 Porównaj ten element z W3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML. W modelu DOM, węzły XML, w tym elementy i atrybuty, muszą zostać utworzone w kontekście dokumentu XML. Oto fragment kodu do utworzenia elementu Name w modelu DOM:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pozwala uniknąć tej warstwy złożoności.  
  
 W przypadku korzystania z LINQ to XML Klasa <xref:System.Xml.Linq.XDocument> jest używana tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Uproszczona obsługa nazw i przestrzeni nazw  
 Obsługa nazw, przestrzeni nazw i prefiksów przestrzeni nazw jest ogólnie złożonym elementem programowania XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] upraszcza nazwy i przestrzenie nazw, eliminując wymóg postępowania z prefiksami przestrzeni nazw. Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz. Ale jeśli zdecydujesz się nie jawnie kontrolować prefiksów przestrzeni nazw, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] będzie przypisywać prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane, lub będą serializować przy użyciu domyślnych przestrzeni nazw, jeśli nie. Jeśli są używane domyślne przestrzenie nazw, nie będzie żadnych prefiksów przestrzeni nazw w dokumencie będącym wynikiem. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Innym problemem z modelem DOM jest to, że nie pozwala na zmianę nazwy węzła. Zamiast tego należy utworzyć nowy węzeł i skopiować do niego wszystkie węzły podrzędne, tracąc oryginalną tożsamość węzła. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] uniknąć tego problemu, umożliwiając ustawienie właściwości <xref:System.Xml.Linq.XName> w węźle.  
  
## <a name="static-method-support-for-loading-xml"></a>Obsługa metody statycznej do ładowania pliku XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umożliwia ładowanie XML przy użyciu metod statycznych zamiast metod instancji. Upraszcza to ładowanie i analizowanie. Aby uzyskać więcej informacji, zobacz [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Usuwanie obsługi dla konstrukcji DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bardziej upraszcza programowanie XML przez usunięcie obsługi jednostek i odwołań do jednostek. Zarządzanie jednostkami jest skomplikowane i rzadko jest używane. Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania. Gdy zostanie wypełnione drzewo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], wszystkie jednostki DTD są rozwinięte.  
  
## <a name="support-for-fragments"></a>Obsługa fragmentów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie zapewnia odpowiednika dla klasy `XmlDocumentFragment`. W wielu przypadkach jednak pojęcie `XmlDocumentFragment` może być obsługiwane przez wynik zapytania, które jest wpisane jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode>lub <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Obsługa elementu XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pomocą metod rozszerzających <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Obsługa białych znaków i wcięć  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje biały znak więcej niż w modelu DOM.  
  
 Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem. Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML. Jest to domyślne zachowanie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty. W żaden sposób nie trzeba zmieniać tego wcięcia. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można to zrobić przez zachowanie białych znaków podczas ładowania lub analizowania kodu XML oraz wyłączanie formatowania podczas serializacji kodu XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przechowuje białe miejsca jako węzeł <xref:System.Xml.Linq.XText>, zamiast mieć wyspecjalizowany typ węzła <xref:System.Xml.XmlNodeType.Whitespace>, jak DOM.  
  
## <a name="support-for-annotations"></a>Obsługa adnotacji  
 elementy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługują rozszerzalny zestaw adnotacji. Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też innym rodzajem informacji specyficznych dla aplikacji. Aby uzyskać więcej informacji, zobacz [LINQ to XML adnotacje](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Obsługa informacji o schemacie  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia obsługę walidacji XSD za pomocą metod rozszerzających w przestrzeni nazw <xref:System.Xml.Schema?displayProperty=nameWithType>. Można sprawdzić, czy drzewo XML jest zgodne z XSD. Drzewo XML można wypełnić za pomocą sprawdzonych po walidacji schematu (PSVI). Aby uzyskać więcej informacji, zobacz [How to: Validate using XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
