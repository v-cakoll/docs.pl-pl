---
title: Kompilacja i ponowne użycie w wyrażeniach regularnych
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2166412269a84329d42f58c7e3423229be4327b8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877770"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Można zoptymalizować wydajność aplikacji, które zwiększone użycie wyrażeń regularnych zrozumienie, jak aparat wyrażeń regularnych kompiluje wyrażeń i zrozumienie, jak regularne wyrażenia są buforowane. W tym temacie omówiono kompilacji i buforowania.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenie regularne na sekwencję wewnętrznych instrukcji (są to kody wysokiego poziomu, które różnią się od języka Microsoft intermediate language lub MSIL). Gdy aparat wyrażeń regularnych, interpretuje kody wewnętrzne.  
  
 Jeśli <xref:System.Text.RegularExpressions.Regex> obiekt jest konstruowany przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji kompiluje wyrażenie regularne do jawnego kodu MSIL zamiast wewnętrznej instrukcji wysokiego poziomu wyrażenia regularnego. Dzięki temu. Kompilator just-in-time (JIT) w sieci można przekonwertować wyrażenia do macierzystego kodu maszynowego większą wydajność.  
  
Jednak wygenerowane MSIL nie może być zwolniony. Jedynym sposobem, aby zwolnić kod jest zwolnienie domeny aplikacji (czyli do zwolnienie wszystkich aplikacji użytkownika kodu.). Efektywne gdy wyrażenie regularne jest kompilowane przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji, nigdy nie zwalnia zasoby używane przez skompilowane wyrażenie, nawet jeśli wyrażenie regularne zostało utworzone przez <xref:System.Text.RegularExpressions.Regex> obiekt, który jest ogólnie wyrzucania elementów bezużytecznych.  
  
 Musisz być ostrożnym ograniczyć liczbę różnych wyrażeń regularnych kompilacji z <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcję, aby uniknąć zużywają za dużo zasobów. Jeśli aplikacja musi używać dużych lub nieograniczona liczba wyrażeń regularnych, każde wyrażenie powinny być interpretowane, nie są kompilowane. Jednak jeśli niewielka liczba wyrażeń regularnych są używane wielokrotnie, ich powinna być skompilowana przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> zapewnienia lepszej wydajności. Alternatywą jest używanie wstępnie skompilowanych wyrażeń regularnych. Można skompilować wszystkie wyrażenia do wielokrotnego użytku biblioteki DLL przy użyciu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metody. Umożliwia to uniknięcie konieczności kompilacji w czasie wykonywania przeoczeń od prędkości skompilowanych wyrażeń regularnych.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych zachowuje pamięć podręczną całej aplikacji skompilowanych wyrażeń regularnych. Pamięć podręczna przechowuje wzorce wyrażeń regularnych, które są używane tylko w wywołaniach metody statycznej. (Wzorce wyrażeń regularnych, przekazana do metody wystąpienia nie są buforowane.) Umożliwia to uniknięcie konieczności ponownej analizy wyrażenia do kodu bajtowego wysokiego poziomu każdorazowo, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest określana przez wartość `static` (`Shared` w języku Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwości. Domyślnie aparat wyrażenia regularnego buforuje maksymalnie 15 skompilowanych wyrażeń regularnych. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, najdawniej używaną wyrażenia regularnego jest odrzucana i nowe wyrażenie regularne jest buforowany.  
  
 Aplikację można korzystać ze wstępnie skompilowanych wyrażeń regularnych w jednym z dwóch sposobów:  
  
-   Za pomocą metody statycznej <xref:System.Text.RegularExpressions.Regex> obiekt do definiowania wyrażeń regularnych. Jeśli korzystasz z wzorcem wyrażenia regularnego, który został już zdefiniowany w innym wywołaniu metody statyczne, aparat wyrażeń regularnych pobierze go z pamięci podręcznej. Jeśli nie, aparat będzie kompilowania wyrażeń regularnych i dodaj go do pamięci podręcznej.  
  
-   Dzięki ponownemu wykorzystaniu istniejące <xref:System.Text.RegularExpressions.Regex> obiektu tak długo, jak jej wzorca wyrażenia regularnego jest wymagana.  
  
 Ze względu na obciążenie podczas tworzenia wystąpienia obiektu i kompilowania wyrażeń regularnych, tworzenie i szybko niszczenie liczne <xref:System.Text.RegularExpressions.Regex> obiektów jest procesem bardzo kosztowna. W przypadku aplikacji korzystających z dużej liczby różnych wyrażeń regularnych można zoptymalizować wydajność przy użyciu wywołania statycznej `Regex` metody i prawdopodobnie przez zwiększenie rozmiaru pamięci podręcznej wyrażenia regularnego.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażeń regularnych programu .NET](../../../docs/standard/base-types/regular-expressions.md)
