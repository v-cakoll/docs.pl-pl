---
title: Prawidłowa zawartość obiektów XElement i XDocument3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590936"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Weryfikowanie zawartości obiektów XElement i XDocument
W tym temacie opisano prawidłowe argumenty, które mogą być przekazywane do konstruktorów i metod, które są używane do dodawania zawartości do elementów i dokumentów.  
  
## <a name="valid-content"></a>Prawidłowa zawartość  
 Zapytania często <xref:System.Collections.Generic.IEnumerable%601> oceniają <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute>do lub z <xref:System.Xml.Linq.XElement> . Kolekcje <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty można <xref:System.Xml.Linq.XElement> przekazać do konstruktora. W związku z tym jest wygodne, aby przekazać wyniki kwerendy jako zawartość do metod i konstruktorów, które są używane do wypełniania drzew XML.  
  
 Podczas dodawania zawartości prostej, różne typy mogą być przekazywane do tej metody. Prawidłowe typy są następujące:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Dowolny typ, `Object.ToString`który implementuje .  
  
- Dowolny typ, <xref:System.Collections.Generic.IEnumerable%601>który implementuje .  
  
 Podczas dodawania złożonej zawartości do tej metody można przekazać różne typy:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Każdy typ implementuje<xref:System.Collections.Generic.IEnumerable%601>  
  
 Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana, a wszystkie elementy w kolekcji są dodawane. Jeśli kolekcja <xref:System.Xml.Linq.XNode> zawiera <xref:System.Xml.Linq.XAttribute> lub obiektów, każdy element w kolekcji jest dodawany oddzielnie. Jeśli kolekcja zawiera tekst (lub obiekty, które są konwertowane na tekst), tekst w kolekcji jest połączony i dodany jako węzeł pojedynczego tekstu.  
  
 Jeśli zawartość `null`jest , nic nie jest dodawane. Podczas przekazywania elementów kolekcji w `null`kolekcji może być . Element `null` w kolekcji nie ma wpływu na drzewo.  
  
 Dodany atrybut musi mieć unikatową nazwę w jego element zawierający.  
  
 Podczas <xref:System.Xml.Linq.XNode> dodawania lub <xref:System.Xml.Linq.XAttribute> obiektów, jeśli nowa zawartość nie ma nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.  
  
## <a name="valid-content-for-documents"></a>Prawidłowa zawartość dokumentów  
 Atrybutów i prostej zawartości nie można dodać do dokumentu.  
  
 Nie ma wielu scenariuszy, które <xref:System.Xml.Linq.XDocument>wymagają utworzenia pliku . Zamiast tego zazwyczaj można utworzyć drzewa <xref:System.Xml.Linq.XElement> XML z węzłem głównym. Jeśli nie masz określonego wymogu utworzenia dokumentu (na przykład dlatego, że musisz utworzyć instrukcje przetwarzania i komentarze na najwyższym poziomie lub <xref:System.Xml.Linq.XElement> musisz obsługiwać typy dokumentów), często wygodniej jest używać jako węzła głównego.  
  
 Prawidłowa zawartość dokumentu zawiera następujące elementy:  
  
- Zero lub <xref:System.Xml.Linq.XDocumentType> jeden obiekt. Typy dokumentów muszą znajdować się przed elementem.  
  
- Zero lub jeden element.  
  
- Zero lub więcej komentarzy.  
  
- Zero lub więcej instrukcji przetwarzania.  
  
- Zero lub więcej węzłów tekstowych, które zawierają tylko biały znak.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory i funkcje umożliwiające dodawanie zawartości  
 Następujące metody umożliwiają dodawanie zawartości podrzędnej <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>do zawartości podrzędnej lub :  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XElement>plik .|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XDocument>.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje na końcu zawartości <xref:System.Xml.Linq.XElement> podrzędnej <xref:System.Xml.Linq.XDocument>lub .|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość <xref:System.Xml.Linq.XNode>po pliku .|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość <xref:System.Xml.Linq.XNode>przed .|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartości podrzędnej pliku <xref:System.Xml.Linq.XContainer>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Zastępuje całą zawartość (węzły podrzędne <xref:System.Xml.Linq.XElement>i atrybuty) pliku .|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Zastępuje atrybuty pliku <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Zastępuje węzły podrzędne nową zawartością.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Zastępuje węzeł nową zawartością.|  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md)
