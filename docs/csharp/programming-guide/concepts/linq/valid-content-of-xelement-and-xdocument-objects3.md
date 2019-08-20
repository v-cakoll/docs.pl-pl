---
title: Prawidłowa zawartość elementów XElement i XDocument Objects3
ms.date: 07/20/2015
ms.assetid: 0d253586-2b97-459f-b1a7-f30f38f3ed9f
ms.openlocfilehash: 1ad5b18e3bbc2143a56f9c8e7b34354761b4e42f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590936"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a>Weryfikowanie zawartości obiektów XElement i XDocument
W tym temacie opisano prawidłowe argumenty, które mogą być przekazane do konstruktorów i metod, które są używane do dodawania zawartości do elementów i dokumentów.  
  
## <a name="valid-content"></a>Prawidłowa zawartość  
 Zapytania często są oceniane <xref:System.Collections.Generic.IEnumerable%601> do <xref:System.Xml.Linq.XElement> lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute>. Można przekazać kolekcje <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> obiekty do <xref:System.Xml.Linq.XElement> konstruktora. Z tego względu wygodnie jest przekazać wyniki zapytania jako zawartość do metod i konstruktorów używanych do wypełniania drzew XML.  
  
 Podczas dodawania prostej zawartości można przekazywać różne typy do tej metody. Prawidłowe typy to:  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- Dowolny typ, który `Object.ToString`implementuje.  
  
- Dowolny typ, który <xref:System.Collections.Generic.IEnumerable%601>implementuje.  
  
 Podczas dodawania złożonej zawartości można przekazywać różne typy do tej metody:  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- Dowolny typ, który implementuje<xref:System.Collections.Generic.IEnumerable%601>  
  
 Jeśli obiekt implementuje <xref:System.Collections.Generic.IEnumerable%601>, kolekcja w obiekcie jest wyliczana i dodawane są wszystkie elementy w kolekcji. Jeśli kolekcja zawiera <xref:System.Xml.Linq.XNode> obiekty lub <xref:System.Xml.Linq.XAttribute> , każdy element w kolekcji zostanie dodany osobno. Jeśli kolekcja zawiera tekst (lub obiekty, które są konwertowane na tekst), tekst w kolekcji zostanie połączony i dodany jako pojedynczy węzeł tekstowy.  
  
 Jeśli zawartość jest `null`, nic nie jest dodawane. Przekazywanie elementów kolekcji w kolekcji może być `null`możliwe. `null` Element w kolekcji nie ma wpływu na drzewo.  
  
 Dodany atrybut musi mieć unikatową nazwę w obrębie zawartego elementu.  
  
 W przypadku <xref:System.Xml.Linq.XNode> dodawania <xref:System.Xml.Linq.XAttribute> lub obiektów, jeśli nowa zawartość nie ma elementu nadrzędnego, obiekty są po prostu dołączone do drzewa XML. Jeśli nowa zawartość jest już nadrzędna i jest częścią innego drzewa XML, Nowa zawartość jest klonowana, a nowo sklonowana zawartość jest dołączona do drzewa XML.  
  
## <a name="valid-content-for-documents"></a>Prawidłowa zawartość dla dokumentów  
 Atrybuty i zawartość prosta nie mogą zostać dodane do dokumentu.  
  
 Istnieje wiele scenariuszy, które wymagają utworzenia <xref:System.Xml.Linq.XDocument>. Zamiast tego można zazwyczaj utworzyć drzewa XML z <xref:System.Xml.Linq.XElement> węzłem głównym. Jeśli użytkownik nie ma konkretnego wymagania dotyczącego tworzenia dokumentu (na przykład dlatego, że konieczne jest utworzenie instrukcji przetwarzania i komentarzy na najwyższym poziomie lub konieczność obsługi typów dokumentów), często jest wygodniejszy do użycia <xref:System.Xml.Linq.XElement> jako węzeł główny.  
  
 Prawidłowa zawartość dla dokumentu zawiera następujące elementy:  
  
- Zero lub jeden <xref:System.Xml.Linq.XDocumentType> obiekt. Typy dokumentów muszą występować przed elementem.  
  
- Zero lub jeden element.  
  
- Zero lub więcej komentarzy.  
  
- Zero lub więcej instrukcji przetwarzania.  
  
- Zero lub więcej węzłów tekstowych, które zawierają tylko biały znak.  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a>Konstruktory i funkcje, które umożliwiają dodawanie zawartości  
 Poniższe metody pozwalają dodać zawartość podrzędną do elementu <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>lub:  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|Konstruuje <xref:System.Xml.Linq.XDocument>a.|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|Dodaje do końca zawartości <xref:System.Xml.Linq.XElement> podrzędnej lub. <xref:System.Xml.Linq.XDocument>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|Dodaje zawartość po <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|Dodaje zawartość przed <xref:System.Xml.Linq.XNode>.|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|Dodaje zawartość na początku zawartości <xref:System.Xml.Linq.XContainer>podrzędnej.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|Zamienia całą zawartość (węzły podrzędne i atrybuty) obiektu <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|Zastępuje atrybuty <xref:System.Xml.Linq.XElement>.|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|Zamienia węzły podrzędne na nową zawartość.|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|Zamienia węzeł na nową zawartość.|  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md)
