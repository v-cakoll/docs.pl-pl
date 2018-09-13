---
title: Przestrzenie nazw i definicje DTD w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8a1de8ab10eff88757720a35aa9668125cfbfa
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44708273"
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Przestrzenie nazw i definicje DTD w modelu DOM
Obsługa complicate przestrzeni nazw definicje (pliki DTD) typu dokumentu. Na przykład następujący kod XML zawiera atrybuty domyślne zawierające dwukropki w nazwach.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Poniżej przedstawiono możliwe rozwiązania, jeśli ta konstrukcja jest dozwolony:  
  
-   `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks musi być rozpoznawalna przy użyciu `xmlns:x` deklaracji przestrzeni nazw musi również istnieć gdzieś w DTD. Jest to błąd, aby zamapować tego prefiksu na coś innego w dokumencie wystąpienia.  
  
-   `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks jest zawsze rozwiązane w kontekście elementów wystąpienia. Oznacza to, że do innej przestrzeni nazw Uniform Resource Identifier (URI), w zależności od zakresu przestrzeni nazw, w którym faktycznie zamapować prefiksu `item` element jest wyświetlany. To zachowanie jest bardziej przewidywalna od rozdzielczości w starszych punktor, ale ma inne zagadnienia skomplikowane, ponieważ wymaga, aby być zmaterializowany atrybutów domyślnych.  
  
-   Dwukropek jest ignorowana, ponieważ znajduje się w DTD, a nazwa atrybutu jest `x:y`, żadnego prefiksu i obszaru nazw URI.  
  
-   Dwukropek w atrybucie domyślne zgłasza wyjątek, informujący o tym w dwukropki w nazwach w DTD są nieobsługiwane. Skutkuje to zachowanie przewidywalne, ale nie można załadować wiele World Wide Web Consortium (W3C) oznacza, że publikowane definicje DTD.  
  
-   Gdy użytkownik zażąda weryfikacji DTD, obsługa przestrzeni nazw dla całego dokumentu jest wyłączona. Dzięki temu można załadować definicji DTD W3C i powoduje zachowanie przewidywalne.  
  
 Kod XML w Microsoft .NET Framework implementuje drugą opcją Maksymalna zgodność W3C.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
