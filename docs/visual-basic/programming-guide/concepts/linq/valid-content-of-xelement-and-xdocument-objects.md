---
title: Nieprawidłowa zawartość XElement i XDocument Objects2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: 168c87f23d4545afe7b80579673c050068ee697b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502705"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Weryfikowanie zawartości obiektów XElement i XDocument
W tym temacie opisano prawidłowe argumenty, które mogą być przekazywane do konstruktorów i metod, których używasz do dodawania zawartości do elementów i dokumentów.  
  
## <a name="valid-content"></a>Nieprawidłowa zawartość  
 Zapytania często zwrócić <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Można przekazać kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora. Dlatego jest wygodne do przekazania wyników zapytania jako zawartość do metod i konstruktorów, używanych do wypełnienia drzew XML.  
  
 Podczas dodawania zawartość, proste, różne typy mogą być przekazywane do tej metody. Prawidłowe typy:  
  
-   <xref:System.String>  
  
-   <xref:System.Double>  
  
-   <xref:System.Single>  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Boolean>  
  
-   <xref:System.DateTime>  
  
-   <xref:System.TimeSpan>  
  
-   <xref:System.DateTimeOffset>  
  
-   Dowolny typ, który implementuje `Object.ToString`.  
  
-   Dowolny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>.  
  
 Podczas dodawania zawartości złożonej, różnych typów można przekazany do tej metody:  
  
-   <xref:System.Xml.Linq.XObject>  
  
-   <xref:System.Xml.Linq.XNode>  
  
-   <xref:System.Xml.Linq.XAttribute>  
  
-   Dowolny typ, który implementuje <xref:System.Collections.Generic.IEnumerable%601>  
  
 Jeśli obiekt implementuje interfejs <xref:System.Collections.Generic.IEnumerable%601>, są wyliczane kolekcji w obiekcie, a wszystkie elementy w kolekcji są dodawane. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiektów, każdy element w kolekcji zostanie dodany osobno. Jeśli kolekcja zawiera tekst (lub obiektów, które są konwertowane na tekst), tekst w kolekcji jest połączonych i dodać jako węzeł w jeden tekst.  
  
 Jeśli zawartość jest `null`, nic nie zostanie dodany. Podczas przekazywania kolekcję elementów w kolekcji może być `null`. Element `null` elementu w kolekcji nie ma wpływu na drzewie.  
  
 Dodano atrybut musi mieć unikatową nazwę w ramach jego elemencie zawierającego.  
  
 Podczas dodawania <xref:System.Xml.Linq.XNode> lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, następnie obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest elementem nadrzędnym, a jest częścią innego drzewa XML, następnie został sklonowany nowej zawartości, a nowo sklonowanego zawartości jest dołączony do drzewa XML.  
  
## <a name="valid-content-for-documents"></a>Nieprawidłowa zawartość dokumentów  
 Atrybuty i prostej zawartości nie można dodać do dokumentu.  
  
 Nie są wiele scenariuszy, w których konieczna utworzyć <xref:System.Xml.Linq.XDocument>. Zamiast tego można utworzyć zwykle z drzewa XML z <xref:System.Xml.Linq.XElement> węzła głównego. Jeśli nie masz określonych wymagań można utworzyć dokumentu, (na przykład dlatego, że należy utworzyć instrukcje przetwarzania i komentarze na najwyższym poziomie lub masz obsługę typów dokumentów), jest często bardziej wygodny w użyciu <xref:System.Xml.Linq.XElement> jako węzeł główny.  
  
 Nieprawidłowa zawartość dokumentu obejmuje następujące funkcje:  
  
-   Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiektów. Typy dokumentów musi występować przed elementem.  
  
-   Zero lub jeden element.  
  
-   Zero lub więcej komentarzy.  
  
-   Zero lub więcej instrukcji przetwarzania.  
  
-   Zero lub więcej węzły tekstowe, które zawierają tylko białe miejsca.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory i funkcje, które umożliwiają dodawanie zawartości  
 Następujące metody umożliwiają dodanie zawartość elementu podrzędnego do <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje do końca zawartość elementu podrzędnego <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartość elementu podrzędnego <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Zastępuje całą zawartość (węzły podrzędne i atrybuty) <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Zamienia węzłów podrzędnych nowej zawartości.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Zamienia węzeł nowej zawartości.|  
  
## <a name="see-also"></a>Zobacz także
- [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)
