---
title: Ładowanie danych z czytnika
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7e74918c-bc72-4977-a49b-e1520a6d8f60
ms.openlocfilehash: 90a66e04bda4fb2ee4216e8aabd631afb2f28dd0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710716"
---
# <a name="load-data-from-a-reader"></a>Ładowanie danych z czytnika
Jeśli dokument XML zostanie załadowany przy użyciu metody <xref:System.Xml.XmlDocument.Load%2A> i parametru <xref:System.Xml.XmlReader>, występują różnice w zachowaniu, które występuje w porównaniu z zachowaniem ładowania danych z innych formatów. Jeśli czytnik jest w stanie początkowym, <xref:System.Xml.XmlDocument.Load%2A> zużywa całą zawartość z czytnika i kompiluje Document Object Model XML (DOM) ze wszystkich danych w czytniku.  
  
 Jeśli czytnik jest już umieszczony w węźle w dokumencie, a czytnik jest następnie przenoszona do metody <xref:System.Xml.XmlDocument.Load%2A>, <xref:System.Xml.XmlDocument.Load%2A> próbuje odczytać bieżący węzeł i wszystkie jego elementy równorzędne, aż do tagu końcowego, który zamknie bieżącą głębokość do pamięci. Pomyślnie podjęto próbę <xref:System.Xml.XmlDocument.Load%2A> zależy od węzła, na którym jest on odczytywany podczas próby obciążenia, ponieważ <xref:System.Xml.XmlDocument.Load%2A> sprawdza, czy plik XML z czytnika jest poprawnie sformułowany. Jeśli plik XML nie jest poprawnie sformułowany, <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek. Na przykład poniższy zestaw węzłów zawiera dwa elementy poziomu głównego, kod XML nie jest poprawnie sformułowany, a <xref:System.Xml.XmlDocument.Load%2A> zgłasza wyjątek.  
  
- Węzeł komentarza, po którym następuje węzeł elementu, po którym następuje węzeł elementu, po którym następuje węzeł EndElement.  
  
 Poniższy zestaw węzłów tworzy niekompletny DOM, ponieważ nie ma elementu głównego poziomu.  
  
- Węzeł komentarza, po którym następuje węzeł ProcessingInstruction, po którym następuje węzeł komentarza, po którym następuje węzeł EndElement.  
  
 Nie zgłasza to wyjątku, a dane są ładowane. Można dodać element główny na początku tych węzłów i utworzyć poprawnie sformułowany kod XML, który można zapisać bez błędu.  
  
 Jeśli czytnik znajduje się w węźle liścia, który jest nieprawidłowy dla poziomu głównego dokumentu (na przykład odstępu lub węzła atrybutu), czytnik jest nadal odczytywany do momentu, aż zostanie umieszczony w węźle, który może być używany jako element główny. Dokument rozpoczyna ładowanie w tym momencie.  
  
 Domyślnie <xref:System.Xml.XmlDocument.Load%2A> nie sprawdza, czy kod XML jest prawidłowy przy użyciu definicji typu dokumentu (DTD) lub walidacji schematu. Sprawdza tylko, czy plik XML jest poprawnie sformułowany. Aby można było sprawdzić poprawność, należy utworzyć <xref:System.Xml.XmlReader> przy użyciu klasy <xref:System.Xml.XmlReaderSettings>. Klasa <xref:System.Xml.XmlReader> może wymusić walidację przy użyciu schematu DTD lub języka definicji schematu (XSD). Właściwość <xref:System.Xml.ValidationType> klasy <xref:System.Xml.XmlReaderSettings> określa, czy wystąpienie <xref:System.Xml.XmlReader> wymusza weryfikację. Aby uzyskać więcej informacji na temat walidacji danych XML, zobacz sekcję uwagi na stronie informacje referencyjne <xref:System.Xml.XmlReader>.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
