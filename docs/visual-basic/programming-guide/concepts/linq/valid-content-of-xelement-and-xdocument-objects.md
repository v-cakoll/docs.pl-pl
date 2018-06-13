---
title: Nieprawidłowa zawartość klasy XElement i Objects2 klasy XDocument
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 4b1d588f0ebbfec6d5cf7a58b63f92005db75acc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649386"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Nieprawidłowa zawartość klasy XElement i obiektów klasy XDocument
W tym temacie opisano nieprawidłowe argumenty, które mogą zostać przekazane do konstruktorów i metod, które umożliwia dodawanie zawartości do elementów i dokumentów.  
  
## <a name="valid-content"></a>Nieprawidłowa zawartość.  
 Zapytania często obliczać <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Kolekcje można przekazać <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora. W związku z tym jest wygodne do przekazania wyników zapytania jako zawartość do metody i konstruktory używanych do wypełnienia drzew XML.  
  
 Podczas dodawania zawartości prostej, różnych typów mogą być przekazywane do tej metody. Prawidłowe typy:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Dowolnego typu, który implementuje `Object.ToString`.  
  
-   Dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Podczas dodawania zawartości złożonej, różne typy mogą zostać przekazane do tej metody:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601>  
  
 Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>wyliczeniu kolekcji w obiekcie i zostaną dodane wszystkie elementy w kolekcji. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiekty oddzielnie dodaniu każdego elementu w kolekcji. Jeśli kolekcja zawiera tekst (lub obiektów, które są konwertowane na tekst), tekst w kolekcji jest połączony i dodać jako węzeł jeden tekst.  
  
 Jeśli zawartość jest `null`, nic nie jest dodane. Podczas przekazywania kolekcji elementów w kolekcji może być `null`. A `null` elementu w kolekcji nie ma wpływu na drzewie.  
  
 Dodano atrybut musi mieć unikatową nazwę w ramach jego elementu zawierającego.  
  
 Podczas dodawania <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiekty, jeśli nowa zawartość nie ma elementu nadrzędnego, następnie obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest elementem nadrzędnym, a jest częścią innego drzewa XML, następnie nowej zawartości został sklonowany, a zawartość nowo sklonowanego jest dołączony do drzewa XML.  
  
## <a name="valid-content-for-documents"></a>Nieprawidłowa zawartość dokumentów  
 Atrybuty i prostej zawartości nie można dodać do dokumentu.  
  
 Nie ma wiele scenariuszy, które wymagają utworzenia <xref:System.Xml.Linq.XDocument>. Zamiast tego zazwyczaj można utworzyć z drzewa XML z <xref:System.Xml.Linq.XElement> węzła głównego. Jeśli nie ma określonych wymagań można utworzyć dokumentu (na przykład dlatego należy utworzyć instrukcji przetwarzania i komentarze na najwyższym poziomie lub ma do obsługi typów dokumentu), jest często bardziej wygodne <xref:System.Xml.Linq.XElement> jako węzeł główny.  
  
 Nieprawidłowa zawartość dokumentu obejmuje następujące funkcje:  
  
-   Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiektów. Typy dokumentów musi występować przed elementem.  
  
-   Zero lub jeden element.  
  
-   Komentarze do zera lub większej.  
  
-   Zero lub więcej instrukcji przetwarzania.  
  
-   Zero lub więcej węzły tekstowe, które zawierają tylko puste miejsca.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory i funkcje, które umożliwiają dodawanie zawartości  
 Następujące metody umożliwiają dodawanie zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje na końcu zawartości elementu podrzędnego <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku elementu podrzędnego zawartości <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Zamienia całą zawartość (węzły podrzędne i atrybuty) z <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Węzły podrzędne są zastępowane nową zawartość.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Zamienia węzła nową zawartość.|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
