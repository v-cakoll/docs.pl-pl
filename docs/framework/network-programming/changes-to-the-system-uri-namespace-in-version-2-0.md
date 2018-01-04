---
title: Zmiany w przestrzeni nazw System.Uri w wersji 2.0
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35883fe9-2d09-4d8b-80ca-cf23a941e459
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3ebf74fbe7f2e207af8bf861efece58026148e2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="changes-to-the-systemuri-namespace-in-version-20"></a>Zmiany w przestrzeni nazw System.Uri w wersji 2.0
Wprowadzono kilka zmian <xref:System.Uri?displayProperty=nameWithType> klasy. Te zmiany stałej niepoprawnego zachowania, rozszerzone użyteczność i zwiększonych zabezpieczeń.  
  
## <a name="obsolete-and-deprecated-members"></a>Przestarzałe i przestarzałe elementy członkowskie  
 Konstruktory:  
  
-   Wszystkie konstruktory, które mają `dontEscape` parametru.  
  
 Metody:  
  
-   <xref:System.Uri.CheckSecurity%2A>  
  
-   <xref:System.Uri.Escape%2A>  
  
-   <xref:System.Uri.Canonicalize%2A>  
  
-   <xref:System.Uri.Parse%2A>  
  
-   <xref:System.Uri.IsReservedCharacter%2A>  
  
-   <xref:System.Uri.IsBadFileSystemCharacter%2A>  
  
-   <xref:System.Uri.IsExcludedCharacter%2A>  
  
-   <xref:System.Uri.EscapeString%2A>  
  
## <a name="changes"></a>Zmiany  
  
-   Dla schematy identyfikatorów URI, które nie mają części zapytania (pliku, ftp i inne) '?' znaków zawsze miały zmienione znaczenie i nie jest uważana za początku <xref:System.Uri.Query%2A> części.  
  
-   Niejawne pliku identyfikatory URI (w postaci "c:\directory\file@name.txt"), fragment znak (#) zawsze została zmieniona, chyba że wymagane jest pełne unescaping lub <xref:System.Uri.LocalPath%2A> jest `true`.  
  
-   Została usunięta obsługa hostname UNC; przyjęto w specyfikacji IDN reprezentujący międzynarodowe nazwy hostów.  
  
-   <xref:System.Uri.LocalPath%2A>zawsze zwraca wartość typu ciąg całkowicie niezmienionym znaczeniu.  
  
-   <xref:System.Uri.ToString%2A>nie unescape zmienionym '%', '?', lub znaku "#".  
  
-   <xref:System.Uri.Equals%2A>teraz obejmuje <xref:System.Uri.Query%2A> części w sprawdzania równości.  
  
-   Operatory "=="i"! =" zastąpione i połączone z <xref:System.Uri.Equals%2A> metody.  
  
-   <xref:System.Uri.IsLoopback%2A>teraz tworzy spójne wyniki.  
  
-   Identyfikator URI "`file:///path`" jest już przetłumaczyć "file://path".  
  
-   "#" teraz jest rozpoznawana jako terminatora nazwy hosta. Oznacza to, że "http://consoto.com#fragment" teraz jest konwertowany na "http://contoso.com/#fragment".  
  
-   Błąd podczas łączenia z fragmentem podstawowy identyfikator URI został rozwiązany.  
  
-   Błąd w <xref:System.Uri.HostNameType%2A> został rozwiązany.  
  
-   Błąd podczas analizowania NNTP jest stała.  
  
-   Identyfikator URI w postaci HTTP:contoso.com teraz zgłasza wyjątek podczas analizowania.  
  
-   Platformę poprawnie obsługuje informacje o użytkowniku w identyfikatorze URI.  
  
-   Kompresja ścieżka identyfikatora URI jest ustalony tak, aby przerwane identyfikatora URI nie można przejść przez system plików główny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Uri?displayProperty=nameWithType>
