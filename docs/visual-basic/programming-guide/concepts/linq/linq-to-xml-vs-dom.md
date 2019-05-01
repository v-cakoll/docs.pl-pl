---
title: LINQ to XML a Modelu DOM (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 282df577808342a52a70f419b2a7559752103a0f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051497"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML a Modelu DOM (Visual Basic)
W tej sekcji opisano niektóre podstawowe różnice między [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i bieżącej dominujący XML programowania interfejsu API, W3C Document Object Model (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nowe sposoby tworzenia drzew XML  
 W modelu DOM W3C tworzysz drzewa XML z dołu. oznacza to Utwórz dokument, tworzyć elementy, a następnie dodać elementy do dokumentu.  
  
 Na przykład, następujące byłoby typowym sposobem tworzenia drzewa XML przy użyciu implementacja firmy Microsoft w modelu DOM, <xref:System.Xml.XmlDocument>:  
  
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
  
 Ten styl kodowania nie zapewnia wizualne dużej ilości informacji na temat struktury drzewa XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje takie podejście do Konstruowanie drzewa XML, ale obsługuje także alternatywne podejście, *konstrukcja funkcjonalna*. W języku Visual Basic konstrukcja funkcjonalna używa literałów XML do tworzenia drzewa XML.  
  
 Oto jak będzie konstruowania tych samych drzewa XML przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcja funkcjonalna:  
  
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
  
 Należy zauważyć, że wcięć w kodzie do konstruowania drzewa XML pokazuje strukturę elementu bazowego XML.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Praca bezpośrednio z elementów XML  
 Gdy program za pomocą XML zespół podstawowego jest zazwyczaj na elementy XML, a być może w atrybutach. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można pracować bezpośrednio z elementów XML oraz atrybuty. Można na przykład, wykonaj następujące czynności:  
  
- Tworzenie elementów XML bez przy użyciu obiektu dokumentu w ogóle. Upraszcza to programowania, gdy trzeba pracować przy użyciu fragmentów drzew XML.  
  
- Obciążenia `T:System.Xml.Linq.XElement` obiektów bezpośrednio z pliku XML.  
  
- Serializowanie `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.  
  
 To porównać do modelu DOM W3C, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML. W modelu DOM węzłów XML, w tym elementów i atrybutów, należy utworzyć w kontekście dokumentu XML. Poniżej przedstawiono fragment kodu, aby utworzyć element nazwy w modelu DOM:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Jeśli chcesz użyć elementu na wiele dokumentów, należy zaimportować węzłów, wszystkich dokumentów. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pozwala uniknąć złożoności tej warstwy.  
  
 Podczas korzystania z LINQ to XML, należy użyć <xref:System.Xml.Linq.XDocument> klasy tylko wtedy, gdy chcesz dodać instrukcję przetwarzania lub komentarz na poziomie głównym dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Uproszczona obsługa nazw i przestrzeni nazw  
 Obsługa nazw, przestrzenie nazw i prefiksy przestrzeni nazw jest zazwyczaj złożonych częścią programowania XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] upraszcza nazw i przestrzeni nazw pozwala pozbyć się konieczności radzenia sobie z prefiksy przestrzeni nazw. Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz. Jeśli zdecydujesz się nie zostały jawnie kontrolowanie prefiksów przestrzeni nazw, jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] spowoduje przypisanie prefiksy przestrzeni nazw podczas serializacji, jeśli wymagane są lub będą serializacji przy użyciu domyślnych przestrzeni nazw, jeśli nie są one. Jeśli używane są domyślne obszary nazw, nie będzie żadnych prefiksów przestrzeni nazw w utworzonego dokumentu. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Inny problem z modelu DOM jest, że nie zezwala Ci zmienić nazwę węzła. Zamiast tego należy utworzyć nowy węzeł i skopiuj wszystkie węzły podrzędne, utraty oryginalną tożsamość węzła. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pozwala uniknąć tego problemu, należy włączyć ustawienia <xref:System.Xml.Linq.XName> właściwość w węźle.  
  
## <a name="static-method-support-for-loading-xml"></a>Obsługa statycznej metody ładowania danych XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia ładowanie kodu XML przy użyciu metody statyczne, zamiast metody wystąpienia. Upraszcza to ładowania i analizowania. Aby uzyskać więcej informacji, zobacz [jak: Ładowanie kodu XML z pliku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Usunięcie obsługi konstrukcji DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dodatkowo upraszcza programowanie, usuwając obsługę jednostek i odwołań do jednostek XML. Zarządzanie jednostkami jest złożona i jest rzadko używana. Usuwanie ich obsługi zwiększa wydajność i upraszcza interfejs programowania. Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewa jest wypełniana, zostaną rozwinięte wszystkie jednostki DTD.  
  
## <a name="support-for-fragments"></a>Obsługa fragmentów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie zapewnia odpowiedniego dla `XmlDocumentFragment` klasy. W wielu przypadkach jednak `XmlDocumentFragment` pojęcia mogą być obsługiwane w wyniku zapytania, które jest <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Obsługa klasy XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pośrednictwem metody rozszerzające w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Obsługa białych znaków i wcięć  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] obsługuje biały znak, co jest prostsze niż DOM.  
  
 Typowym scenariuszem jest Odczytaj dane XML z wcięciami, utworzyć drzewa XML w pamięci bez wszystkie węzły tekstowe białe miejsca (to znaczy nie zachowania biały), wykonywanie operacji na pliku XML, a następnie zapisz plik XML, z wcięciem. Po użytkownik serializacji XML za pomocą formatowania, tylko istotne biały znak w drzewie XML są zachowywane. Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega na odczytywanie i modyfikację XML, który już został celowo z wcięciami. Nie można zmienić to wcięcie w dowolny sposób. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można to zrobić przez zachowywanie białych znaków podczas ładowania lub nemohla analyzovat kód XML i wyłączanie formatowania podczas serializacji XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przechowuje biały znak jako <xref:System.Xml.Linq.XText> węzła zamiast wyspecjalizowanego <xref:System.Xml.XmlNodeType.Whitespace> typ węzła jako modelu DOM wykonuje.  
  
## <a name="support-for-annotations"></a>Obsługa adnotacji  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elementy obsługuje extensible zbiór adnotacji. Jest to przydatne do śledzenia dodatkowych informacji na temat elementu, np. informacji o schemacie, informacji na temat tego, czy element jest powiązany z interfejsu użytkownika lub inne informacje dotyczące rodzaju specyficzne dla aplikacji. Aby uzyskać więcej informacji, zobacz [adnotacje LINQ to XML](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Obsługa informacji o schemacie  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia obsługę walidację XSD za pośrednictwem metody rozszerzające w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw. Aby zweryfikować, że drzewa XML jest zgodny z XSD. Możesz wypełnić drzewa XML z zestaw informacji po weryfikacji (PSVI). Aby uzyskać więcej informacji, zobacz [jak: Weryfikowanie przy użyciu XSD](../../../../visual-basic/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
