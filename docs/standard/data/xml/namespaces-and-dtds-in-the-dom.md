---
title: Przestrzenie nazw i definicje DTD w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
ms.openlocfilehash: 22762e3a7003d9b28a53c7b500829aaa41924c6d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710599"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Przestrzenie nazw i definicje DTD w modelu DOM
Definicje typu dokumentu (DTD) komplikują obsługę przestrzeni nazw. Na przykład poniższy kod XML zawiera atrybuty domyślne zawierające dwukropki w nazwach.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Poniżej przedstawiono możliwe rozwiązania, jeśli ta konstrukcja jest dozwolona:  
  
- `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks musi być rozpoznawalny przy użyciu `xmlns:x` deklaracji przestrzeni nazw, która również musi znajdować się gdzieś w DTD. Wystąpił błąd podczas mapowania tego prefiksu na inny element w dokumencie wystąpienia.  
  
- `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks jest zawsze rozpoznawany w kontekście elementów wystąpienia. Oznacza to, że prefiks może być faktycznie mapowany na różne identyfikatory Uniform Resource Identifier (URI) obszaru nazw, w zależności od zakresu przestrzeni `item` nazw, w którym jest wyświetlany element. To zachowanie jest bardziej przewidywalne niż rozdzielczość podaną we wcześniejszym punktorze, ale ma inne skomplikowane konsekwencje, ponieważ wymaga podania atrybutów domyślnych.  
  
- Dwukropek jest ignorowany, ponieważ znajduje się w DTD, a nazwa atrybutu to `x:y`, brak prefiksu i brak identyfikatora URI przestrzeni nazw.  
  
- Dwukropek w atrybucie domyślnym zgłasza wyjątek, co oznacza, że dwukropek w nazwach w DTD nie są obsługiwane. Powoduje to przewidywalną zachowanie, ale oznacza, że nie można załadować wielu organizacja World Wide Web Consortium (W3C) opublikowanych elementów DTD.  
  
- Gdy użytkownik zażąda walidacji DTD, obsługa przestrzeni nazw dla całego dokumentu jest wyłączona. Dzięki temu można załadować definicje W3C i uzyskać przewidywalne zachowanie.  
  
 KOD XML w Microsoft .NET Framework implementuje drugą opcję maksymalnej zgodności W3C.  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
