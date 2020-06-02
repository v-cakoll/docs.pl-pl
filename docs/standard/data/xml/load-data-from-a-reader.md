---
title: Ładowanie danych z czytnika
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
ms.openlocfilehash: 1c048b08380bebce3a627670d88ff6ae48084535
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289164"
---
# <a name="load-data-from-a-reader"></a>Ładowanie danych z czytnika
Jeśli dokument XML zostanie załadowany przy użyciu <xref:System.Xml.XmlDocument.Load%2A> metody i parametru <xref:System.Xml.XmlReader> , istnieją różnice w zachowaniu, które występuje w porównaniu z zachowaniem ładowania danych z innych formatów. Jeśli czytnik jest w stanie początkowym, <xref:System.Xml.XmlDocument.Load%2A> zużywa całą zawartość z czytnika i kompiluje Document Object Model XML (dom) ze wszystkich danych w czytniku.  
  
 Jeśli czytnik znajduje się już w węźle w dokumencie, a czytnik jest następnie przeszedł do <xref:System.Xml.XmlDocument.Load%2A> metody, <xref:System.Xml.XmlDocument.Load%2A> próbuje odczytać bieżący węzeł i wszystkie jego elementy równorzędne, aż do tagu końcowego, który zamknie bieżącą głębokość do pamięci. Pomyślne próba jest <xref:System.Xml.XmlDocument.Load%2A> zależna od węzła, na którym jest on odczytywany po próbie załadowania, ponieważ <xref:System.Xml.XmlDocument.Load%2A> sprawdza, czy plik XML z czytnika jest poprawnie sformułowany. Jeśli plik XML nie jest poprawnie sformułowany, <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek. Na przykład następujący zestaw węzłów zawiera dwa elementy poziomu głównego, kod XML nie jest dobrze sformułowany i <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.  
  
- Węzeł komentarza, po którym następuje węzeł elementu, po którym następuje węzeł elementu, po którym następuje węzeł EndElement.  
  
 Poniższy zestaw węzłów tworzy niekompletny DOM, ponieważ nie ma elementu głównego poziomu.  
  
- Węzeł komentarza, po którym następuje węzeł ProcessingInstruction, po którym następuje węzeł komentarza, po którym następuje węzeł EndElement.  
  
 Nie zgłasza to wyjątku, a dane są ładowane. Można dodać element główny na początku tych węzłów i utworzyć poprawnie sformułowany kod XML, który można zapisać bez błędu.  
  
 Jeśli czytnik znajduje się w węźle liścia, który jest nieprawidłowy dla poziomu głównego dokumentu (na przykład odstępu lub węzła atrybutu), czytnik jest nadal odczytywany do momentu, aż zostanie umieszczony w węźle, który może być używany jako element główny. Dokument rozpoczyna ładowanie w tym momencie.  
  
 Domyślnie program nie <xref:System.Xml.XmlDocument.Load%2A> sprawdza, czy kod XML jest prawidłowy przy użyciu definicji typu dokumentu (DTD) lub walidacji schematu. Sprawdza tylko, czy plik XML jest poprawnie sformułowany. Aby można było sprawdzić poprawność, należy utworzyć <xref:System.Xml.XmlReader> za pomocą <xref:System.Xml.XmlReaderSettings> klasy. <xref:System.Xml.XmlReader>Klasa może wymusić walidację za pomocą schematu DTD lub języka definicji schematu (XSD). <xref:System.Xml.ValidationType>Właściwość <xref:System.Xml.XmlReaderSettings> klasy określa, czy <xref:System.Xml.XmlReader> wystąpienie wymusza walidację. Aby uzyskać więcej informacji na temat walidacji danych XML, zobacz sekcję uwagi na <xref:System.Xml.XmlReader> stronie referencyjnej.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
