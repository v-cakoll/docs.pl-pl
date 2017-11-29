---
title: LINQ do XML programu vs. Modelu DOM (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f89d3ded61daf16d4a59ccabb4d58625cae4a58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ do XML programu vs. Modelu DOM (Visual Basic)
W tej sekcji opisano niektóre podstawowe różnice między [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i bieżącego XML dominujący programowania interfejsu API, W3C modelu DOM (Document Object).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nowe sposoby tworzenia drzewa XML  
 W modelu DOM W3C drzewo XML od dołu kompilacji oznacza to Utwórz dokument, tworzenie elementów, a następnie dodaj elementy do dokumentu.  
  
 Na przykład następujące będzie typowy sposób tworzenia drzewa XML za pomocą przez firmę Microsoft implementacją modelu DOM, <xref:System.Xml.XmlDocument>:  
  
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
  
 Ten styl kodowania nie zapewnia wizualnie dużej ilości informacji o strukturze drzewa XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje takie podejście do konstruowania drzewo XML, ale obsługuje także alternatywne podejście *funkcjonalności konstrukcji*. W języku Visual Basic funkcjonalności konstrukcji używa literałów XML do konstruowania drzewo XML.  
  
 Oto jak będzie skonstruować tym samym drzewie XML za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcji funkcjonalności:  
  
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
  
 Zwróć uwagę, że wcięcia kodu można utworzyć drzewa XML zawiera struktury XML podstawowej.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Praca bezpośrednio z elementów XML  
 Podczas programowania za pomocą XML programu głównym celem jest zwykle na elementy XML i być może w atrybutach. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz pracować bezpośrednio z elementów XML oraz atrybuty. Można na przykład, wykonaj następujące czynności:  
  
-   Utwórz elementy XML bez użycia obiektu dokumentu w ogóle. Upraszcza programowanie podczas pracy z fragmenty XML drzewa.  
  
-   Obciążenia `T:System.Xml.Linq.XElement` obiektów bezpośrednio z pliku XML.  
  
-   Serializować `T:System.Xml.Linq.XElement` obiektów w pliku lub strumienia.  
  
 To porównać do modelu DOM W3C, w którym dokumentu XML służy jako kontener logiczny do drzewa XML. W modelu DOM węzłów XML, w tym elementów i atrybutów, należy utworzyć w kontekście dokumentu XML. Oto fragment kodu, aby utworzyć element nazwy w modelu DOM:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzłów w dokumentach. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pozwala uniknąć tej warstwy złożoności.  
  
 Podczas korzystania z LINQ do XML, użyj <xref:System.Xml.Linq.XDocument> klasy tylko, jeśli chcesz dodać komentarz lub przetwarzania instrukcję na głównym poziomie dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Uproszczone Obsługa nazwy i przestrzenie nazw  
 Obsługa nazwy przestrzeni nazw i prefiksy przestrzeni nazw jest zwykle złożonych częścią programowania w języku XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]upraszcza nazwy i przestrzenie nazw, eliminując konieczność postępowania w przypadku prefiksy przestrzeni nazw. Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz. Jeśli zdecydujesz się nie jawnie kontrolować prefiksy przestrzeni nazw, jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przypisze prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane lub będzie serializować przy użyciu domyślne obszary nazw, jeśli nie są one. Jeśli są używane domyślne obszary nazw, nie będzie żadnych prefiksów przestrzeni nazw w wynikowym dokumencie. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Inny problem z modelu DOM jest, że nie zezwala można zmienić nazwy węzła. Zamiast tego należy utworzyć nowy węzeł i skopiuj wszystkie węzły podrzędne, utraty oryginalnej tożsamości węzła. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]w celu uniknięcia tego problemu, należy włączyć ustawienia <xref:System.Xml.Linq.XName> właściwość w węźle.  
  
## <a name="static-method-support-for-loading-xml"></a>Obsługa statycznej metody ładowania danych XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Umożliwia ładowanie pliku XML przy użyciu metody statyczne, zamiast metody wystąpienia. Upraszcza to załadowanie i analiza kodu. Aby uzyskać więcej informacji, zobacz [porady: obciążenia XML z pliku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Usunięcie wsparcia dla konstrukcji DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dodatkowo upraszcza programowanie przez usunięcie obsługę jednostek i odwołań do jednostek XML. Zarządzanie jednostkami jest złożony i jest rzadko używana. Usunięcie ich obsługa zwiększa wydajność i upraszcza interfejsu programowania. Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewa zostanie wypełnione, zostaną rozwinięte wszystkie jednostki DTD.  
  
## <a name="support-for-fragments"></a>Obsługa fragmentów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]nie ma odpowiednika dla `XmlDocumentFragment` klasy. W wielu przypadkach, jednak `XmlDocumentFragment` koncepcji są obsługiwane przez wyników zapytania, które jest typu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Obsługa parametrem XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pośrednictwem metody rozszerzenia w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Obsługa biały znak i wcięcie  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]obsługuje biały znak prostsze niż modelu DOM.  
  
 Typowy scenariusz jest Odczytaj dane XML z wcięciami, utwórz drzewo XML w pamięci bez żadnych białe węzły tekstowe (to znaczy nie zachowania biały znak), operacji na pliku XML, a następnie zapisz plik XML z wcięcia. Podczas formatowania kodu XML, tylko znaczący biały znak w drzewie XML są zachowywane. Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Inny typowy scenariusz polega może odczytywać i modyfikować XML, który już został celowo wcięcia. Nie można zmienić tej wcięcia w dowolny sposób. W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], aby to zrobić, zachowując biały znak po załadowaniu lub analizy kodu XML i wyłączanie formatowania podczas serializacji XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przechowuje biały znak jako <xref:System.Xml.Linq.XText> węzła, zamiast specjalistycznej <xref:System.Xml.XmlNodeType.Whitespace> typ węzła jako model DOM jest.  
  
## <a name="support-for-annotations"></a>Obsługa adnotacji  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]elementy obsługują rozszerzony zbiór adnotacji. Jest to przydatne w przypadku śledzenia dodatkowych informacji na temat elementu, takie jak informacje o schemacie, informacji na temat tego, czy element jest powiązany z interfejsu użytkownika lub inne informacje dotyczące rodzaju specyficzne dla aplikacji. Aby uzyskać więcej informacji, zobacz [LINQ do XML adnotacje](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Obsługa informacji o schemacie  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia obsługę sprawdzania poprawności XSD za pośrednictwem metody rozszerzenia w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw. Aby zweryfikować, że drzewo XML jest zgodny z XSD. Można go wypełnić drzewa XML z typu infoset po schema weryfikacji (PSVI). Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności za pomocą schematu XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) i <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie (LINQ do XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
