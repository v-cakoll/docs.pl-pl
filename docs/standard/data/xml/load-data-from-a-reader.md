---
title: Ładowanie danych z czytnika
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5156374708beb07da875d2e2a8a3b74e52e21427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569977"
---
# <a name="load-data-from-a-reader"></a>Ładowanie danych z czytnika
Jeśli dokument XML został załadowany przy użyciu <xref:System.Xml.XmlDocument.Load%2A> — metoda i parametr <xref:System.Xml.XmlReader>, istnieją różnice w zachowaniu, który występuje w porównaniu do zachowania podczas ładowania danych z innych formatów. Jeśli czytnik jest w stanie początkowym <xref:System.Xml.XmlDocument.Load%2A> zużywa całą zawartość z czytnika i tworzy XML modelu DOM (Document Object) z wszystkich danych w czytniku.  
  
 Jeśli czytnik znajduje się już w węźle gdzieś w dokumencie i czytnik są następnie przekazywane do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> podejmuje próbę odczytania bieżącego węzła i wszystkich jego elementów równorzędnych, do tagu końcowego, który zamyka bieżący głębokość do pamięci. Powodzenie próba <xref:System.Xml.XmlDocument.Load%2A> zależą od węzła, który czytnik znajduje się w próba obciążenia jako <xref:System.Xml.XmlDocument.Load%2A> weryfikuje, czy poprawnie sformułowany plik XML z czytnika. Jeśli nie jest poprawnie sformułowany plik XML <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek. Na przykład następujący zestaw węzłów zawiera dwa elementy poziomu głównego, nie jest poprawnie sformułowany plik XML i <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.  
  
-   Węzłem komentarza, a następnie węzeł elementu, a następnie węzeł elementu, a następnie węzeł EndElement.  
  
 Następujący zestaw węzłów tworzy DOM niekompletne, ponieważ nie istnieje żaden element głównego poziomu.  
  
-   Następuje węzła ProcessingInstruction następuje węzłem komentarza, następuje węzła EndElement węzłem komentarza.  
  
 Nie zgłasza wyjątek, a dane zostaną załadowane. Możesz dodać element główny na początku te węzły i utworzyć poprawnie sformułowany plik XML, który może zostać zapisany bez błędów.  
  
 Jeśli czytnik jest ustawiony na węzeł liścia, który jest nieprawidłowy dla poziomu głównego dokumentu (na przykład białe miejsca lub atrybut węzłem), czytnik będzie kontynuowane do odczytu, dopóki nie zostanie on ustawiony na węźle, który może służyć do katalogu głównego. Dokument rozpoczyna się w tym momencie ładowania.  
  
 Domyślnie <xref:System.Xml.XmlDocument.Load%2A> nie sprawdza, czy kod XML jest nieprawidłowa definicja typu dokumentu (DTD) lub Sprawdzanie poprawności schematu. Tylko sprawdzi, czy kod XML jest poprawnie sformułowany. Aby sprawdzanie poprawności jest wykonywane, musisz utworzyć <xref:System.Xml.XmlReader> przy użyciu <xref:System.Xml.XmlReaderSettings> klasy. <xref:System.Xml.XmlReader> Klasy można wymusić przy użyciu schematu języka (XSD) definicji DTD lub schemat sprawdzania poprawności. <xref:System.Xml.ValidationType> Właściwość <xref:System.Xml.XmlReaderSettings> klasa określa, czy <xref:System.Xml.XmlReader> wystąpienia wymusza sprawdzania poprawności. Aby uzyskać więcej informacji o weryfikacji danych XML, zobacz sekcję uwag <xref:System.Xml.XmlReader> strony odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
