---
title: "Kompilacja i ponowne użycie w wyrażeniach regularnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing text with regular expressions, compilation
- searching with regular expressions, compilation
- .NET Framework regular expressions, engines
- .NET Framework regular expressions, compilation
- regular expressions, compilation
- compilation, regular expressions
- pattern-matching with regular expressions, compilation
- regular expressions, engines
ms.assetid: 182ec76d-5a01-4d73-996c-0b0d14fcea18
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 76acdf2d0d2f7805ec78ea44136bfc63441b9bc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Aby zoptymalizować wydajność aplikacji, które wykorzystują szeroką gamę wyrażeń regularnych zrozumienie, jak aparat wyrażeń regularnych kompiluje wyrażeń i zrozumienie, jak regular wyrażenia są buforowane. W tym temacie omówiono kompilacji i buforowania.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenia regularnego do sekwencji wewnętrznych instrukcji (są to kody wysokiego poziomu, które są inne niż firmy Microsoft język pośredni lub MSIL). Gdy aparat wykonuje wyrażenie regularne, interpretuje kody wewnętrzne.  
  
 Jeśli <xref:System.Text.RegularExpressions.Regex> obiekt jest tworzony z <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji kompiluje wyrażenie regularne do jawnego kodu MSIL zamiast instrukcji wewnętrzny wysokiego poziomu wyrażenia regularnego. Dzięki temu. Kompilatora just-in-time (JIT) w sieci można przekonwertować wyrażenia na kod natywny maszyny większą wydajność.  
  
Jednak wygenerowane MSIL nie może być zwolniony. Jedynym sposobem, aby zwolnić kodu jest wyładować domeny aplikacji (oznacza to, aby zwolnienie wszystkich aplikacji do kodu.). Efektywnie gdy wyrażenie regularne jest skompilowana przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji, nigdy nie zwalnia zasoby używane przez wyrażenie skompilowane, nawet jeśli wyrażenie regularne został utworzony przez <xref:System.Text.RegularExpressions.Regex> obiekt, który jest elementem wydane wyrzucania elementów bezużytecznych do.  
  
 Należy zachować ostrożność ograniczyć liczbę różnych wyrażeń regularnych kompilacji z <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcję, aby uniknąć zużywa zbyt wiele zasobów. Jeśli aplikacja musi używać dużych lub niepowiązany liczbę wyrażeń regularnych, każde wyrażenie powinny być rozumiane, nie został skompilowany. Jednak jeśli niewielka liczba wyrażeń regularnych są używane wielokrotnie, ich powinna być skompilowana z <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> w celu poprawy wydajności. Alternatywą jest używanie wyrażeń regularnych wstępnie skompilowana. Można skompilować wszystkie wyrażenia do wielokrotnego użytku biblioteki DLL przy użyciu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metody. Dzięki temu można uniknąć konieczności kompilacji w czasie wykonywania, jednocześnie nadal z szybkości skompilowane wyrażenia regularnego.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych przechowuje podręcznej całej aplikacji skompilowanych wyrażeń regularnych. Pamięć podręczna przechowuje wzorce wyrażenie regularne, które są używane tylko w przypadku wywołania metody statycznej. (Wyrażenie regularne wzorce dostarczony do metody wystąpienia nie są buforowane.) Dzięki temu można uniknąć konieczności ponownej analizy wyrażenia do kodu bajtowego wysokiego poziomu każdym razem, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest określana przez wartość `static` (`Shared` w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwości. Domyślnie aparat wyrażeń regularnych buforuje maksymalnie 15 skompilowane wyrażenia regularnego. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, jest odrzucany najdawniej używaną wyrażenia regularnego i nowe wyrażenie regularne jest buforowana.  
  
 Aplikację można korzystać z wstępnie skompilowanym wyrażeń regularnych w jednym z dwóch sposobów:  
  
-   Za pomocą metody statycznej z <xref:System.Text.RegularExpressions.Regex> obiekt do definiowania wyrażenia regularnego. Jeśli używasz wzorzec wyrażenia regularnego, który został już zdefiniowany w innym wywołaniu metody statycznej, aparat wyrażeń regularnych pobierze go z pamięci podręcznej. Jeśli nie, aparat będzie skompilować wyrażenia regularnego i dodaj go do pamięci podręcznej.  
  
-   Na podstawie istniejącej <xref:System.Text.RegularExpressions.Regex> obiekt tak długo, jak jego wzorzec wyrażenia regularnego jest wymagana.  
  
 Ze względu na obciążenie podczas tworzenia wystąpienia obiektu i kompilacji wyrażeń regularnych, tworzenie i szybko niszczenie wiele <xref:System.Text.RegularExpressions.Regex> obiektów jest bardzo kosztowna procesu. Dla aplikacji, które korzystają z wielu różnych wyrażeń regularnych, można zoptymalizować wydajność przy użyciu wywołań statyczne `Regex` metody i prawdopodobnie przez zwiększenie rozmiaru pamięci podręcznej wyrażenia regularnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
