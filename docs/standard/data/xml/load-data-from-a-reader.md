---
title: Ładowanie danych z czytnika
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55756092f086de47c4b2acb8f147ca3ab231abe1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44068927"
---
# <a name="load-data-from-a-reader"></a>Ładowanie danych z czytnika
Jeśli dokument XML jest ładowany za pomocą <xref:System.Xml.XmlDocument.Load%2A> metody i parametr <xref:System.Xml.XmlReader>, istnieją różnice w zachowaniu, który występuje w porównaniu do zachowania podczas ładowania danych z innych formatach. Jeśli czytnik jest w stanie początkowym <xref:System.Xml.XmlDocument.Load%2A> wykorzystuje całą zawartość z czytnika, a następnie tworzy XML modelu DOM (Document Object) wszystkie dane w czytniku.  
  
 Jeśli czytnik jest już umieszczony w węźle gdzieś w dokumencie i czytnik jest następnie przekazywany do <xref:System.Xml.XmlDocument.Load%2A> metody <xref:System.Xml.XmlDocument.Load%2A> podejmuje próbę odczytu z bieżącego węzła i wszystkich jego elementów równorzędnych do tagu końcowego, który zamyka bieżący głębokość do pamięci. Powodzenie próba dokonania <xref:System.Xml.XmlDocument.Load%2A> zależą od węzła, który proces czytający jest obciążenie zostanie podjęta, jako <xref:System.Xml.XmlDocument.Load%2A> sprawdza, czy poprawnie sformułowany plik XML z czytnika. Jeśli nie jest poprawnie sformułowany plik XML <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek. Na przykład następujący zestaw węzłów zawiera dwa elementy poziomu głównego, nie jest poprawnie sformułowany plik XML i <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.  
  
-   Węzeł komentarzy, a następnie węzeł elementu, a następnie węzeł elementu, a następnie węzeł EndElement.  
  
 Następujący zestaw węzłów tworzy niekompletne modelu DOM, ponieważ nie ma żadnego elementu poziomu głównego.  
  
-   Następuje węzła ProcessingInstruction, a następnie węzeł komentarzy, a następnie węzeł EndElement węzeł komentarzy.  
  
 To nie zgłasza wyjątku, a dane zostaną załadowane. Możesz dodać element główny na początku tych węzłów i utworzyć poprawnie sformułowany dokument XML, który może zostać zapisany bez błędów.  
  
 Jeśli czytnik jest umieszczony na węzeł liścia, który jest nieprawidłowy dla poziomu głównego dokumentu (na przykład białe miejsca lub atrybutu node), proces czytający w dalszym ciągu odczytu, dopóki nie zostanie on ustawiony na węzeł, który może służyć do katalogu głównego. Dokument rozpoczyna się, w tym momencie ładowania.  
  
 Domyślnie <xref:System.Xml.XmlDocument.Load%2A> nie sprawdza, czy kod XML jest prawidłowy, przy użyciu definicji typu dokumentu (DTD) lub Sprawdzanie poprawności schematu. Sprawdza tylko, czy kod XML jest dobrze sformułowany. Aby sprawdzanie poprawności jest wykonywane, musisz utworzyć <xref:System.Xml.XmlReader> przy użyciu <xref:System.Xml.XmlReaderSettings> klasy. <xref:System.Xml.XmlReader> Klasy mogą zostać wymuszone sprawdzanie poprawności przy użyciu schematu języka (XSD) definicji DTD lub schematu. <xref:System.Xml.ValidationType> Właściwość <xref:System.Xml.XmlReaderSettings> klasa określa, czy <xref:System.Xml.XmlReader> wystąpienia wymusza sprawdzania poprawności. Aby uzyskać więcej informacji o weryfikacji danych XML, zobacz sekcję Uwagi <xref:System.Xml.XmlReader> odwołania do stron.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
