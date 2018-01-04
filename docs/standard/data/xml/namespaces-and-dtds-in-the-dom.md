---
title: "Obszary nazw i elementów DTD w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e9b55c4-76ad-4f54-8d96-7ce4b4cf1e05
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cf085cf866ea6034679230115e588024fcd79a11
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="namespaces-and-dtds-in-the-dom"></a>Obszary nazw i elementów DTD w modelu DOM
Obsługa definicje (elementów DTD) complicate przestrzeni nazw typu dokumentu. Na przykład następujący kod XML zawiera zawierające dwukropki w nazwach atrybutów domyślnych.  
  
```xml  
<!ATTLIST item x:id CDATA #IMPLIED>  
```  
  
 Poniżej przedstawiono możliwe rozwiązania, jeśli ta konstrukcja jest dozwolone:  
  
-   `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks musi być rozpoznawalna przy użyciu `xmlns:x` deklaracji przestrzeni nazw musi również istnieć gdzieś w definicji DTD. Istnieje błąd mapowania prefiks na inną w dokumencie wystąpienia.  
  
-   `x:` Jest traktowany jako prefiks przestrzeni nazw, ale ten prefiks jest zawsze rozwiązane w kontekście elementów wystąpienia. Oznacza to, że prefiks faktycznie można zamapować na inną przestrzeń nazw Uniform Resource Identifier (URI), w zależności od zakresu przestrzeni nazw, w którym `item` element jest wyświetlany. To zachowanie jest bardziej przewidywalne od rozdzielczości, podany w starszych punktor, ale ma inne konsekwencje skomplikowane, ponieważ wymaga ona materializować domyślne atrybuty.  
  
-   Dwukropkiem jest ignorowany, ponieważ jest on DTD, a nazwa atrybutu jest `x:y`, bez prefiksu i bez identyfikatora URI przestrzeni nazw.  
  
-   Dwukropkiem w domyślny atrybut zgłasza wyjątek, informujący o tym, że dwukropków w nazwach wewnątrz DTD nie są obsługiwane. Powoduje to przewidywalne zachowanie, ale oznacza, że nie można załadować wiele sieci World Wide Web konsorcjum W3C opublikowane elementów DTD.  
  
-   Gdy użytkownik zażąda weryfikacji DTD, obsługa przestrzeni nazw w całym dokumencie jest wyłączona. Dzięki temu można załadować definicji DTD W3C i powoduje przewidywalne zachowanie.  
  
 Kod XML w programie Microsoft .NET Framework implementuje drugą opcją maksymalną zgodność W3C.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
