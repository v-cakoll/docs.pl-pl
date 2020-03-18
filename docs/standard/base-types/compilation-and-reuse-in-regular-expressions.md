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
ms.openlocfilehash: 3e1dfe8373145286b03e503f038e267ff0d4c4f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091733"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Można zoptymalizować wydajność aplikacji, które intensywnie korzystają z wyrażeń regularnych, rozumiejąc, jak aparat wyrażeń regularnych kompiluje wyrażenia i rozumiejąc, jak są buforowane wyrażenia regularne. W tym temacie omówiono kompilacji i buforowania.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenie regularne do sekwencji instrukcji wewnętrznych (są to kody wysokiego poziomu, które różnią się od języka pośredniego firmy Microsoft lub MSIL). Gdy aparat wykonuje wyrażenie regularne, interpretuje kody wewnętrzne.  
  
 Jeśli <xref:System.Text.RegularExpressions.Regex> obiekt jest konstruowany z opcją, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> kompiluje wyrażenie regularne do jawnego kodu MSIL zamiast instrukcji wewnętrznych wyrażeń regularnych wysokiego poziomu. Pozwala to . Net just-in-time (JIT) kompilator do konwersji wyrażenia do natywnego kodu maszynowego w celu uzyskania wyższej wydajności.  
  
Jednak wygenerowany MSIL nie może być rozładowany. Jedynym sposobem, aby zwolnić kod jest zwolnienie całej domeny aplikacji (to znaczy, aby zwolnić cały kod aplikacji.). Skutecznie po skompilowaniu wyrażenia regularnego <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> z opcją nigdy nie zwalnia zasobów używanych przez skompilowane wyrażenie, <xref:System.Text.RegularExpressions.Regex> nawet jeśli wyrażenie regularne zostało utworzone przez obiekt, który sam jest zwolniony do wyrzucania elementów bezużytecznych.  
  
 Należy zachować ostrożność, aby ograniczyć liczbę różnych wyrażeń regularnych, które można skompilować z opcją, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> aby uniknąć zużywa zbyt wiele zasobów. Jeśli aplikacja musi używać dużej lub nieograniczonej liczby wyrażeń regularnych, każde wyrażenie powinno być interpretowane, a nie kompilowane. Jednak jeśli niewielka liczba wyrażeń regularnych są używane wielokrotnie, <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> powinny być kompilowane z dla lepszej wydajności. Alternatywą jest użycie wstępnie skompilowanych wyrażeń regularnych. Można skompilować wszystkie wyrażenia do dll wielokrotnego użytku <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> przy użyciu metody. Pozwala to uniknąć konieczności kompilowania w czasie wykonywania, a jednocześnie korzystających z szybkości skompilowanych wyrażeń regularnych.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych utrzymuje pamięć podręczną skompilowanych wyrażeń regularnych w całej aplikacji. Pamięć podręczna przechowuje wzorce wyrażeń regularnych, które są używane tylko w wywołaniach metod statycznych. (Wzorce wyrażeń regularnych dostarczane do metod wystąpienia nie są buforowane). Pozwala to uniknąć konieczności ponownej analizy wyrażenia do kodu bajtu wysokiego poziomu za każdym razem, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest `static` `Shared` określana przez <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> wartość właściwości ( w języku Visual Basic). Domyślnie aparat wyrażeń regularnych buforuje do 15 skompilowanych wyrażeń regularnych. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, najmniej ostatnio używane wyrażenie regularne jest odrzucane, a nowe wyrażenie regularne jest buforowane.  
  
 Aplikacja może korzystać ze wstępnie skompilowanych wyrażeń regularnych na jeden z następujących dwóch sposobów:  
  
- Za pomocą metody statycznej <xref:System.Text.RegularExpressions.Regex> obiektu do definiowania wyrażenia regularnego. Jeśli używasz wzorca wyrażenia regularnego, który został już zdefiniowany w innym wywołaniu metody statycznej, aparat wyrażeń regularnych pobierze go z pamięci podręcznej. Jeśli nie, aparat skompiluje wyrażenie regularne i dodać go do pamięci podręcznej.  
  
- Przez ponowne użycie <xref:System.Text.RegularExpressions.Regex> istniejącego obiektu tak długo, jak jego wzorzec wyrażenia regularnego jest potrzebny.  
  
 Ze względu na obciążenie wystąpienia obiektu i kompilacji wyrażenia regularnego, <xref:System.Text.RegularExpressions.Regex> tworzenie i szybkie niszczenie wielu obiektów jest bardzo kosztowny proces. W przypadku aplikacji, które używają dużej liczby różnych wyrażeń `Regex` regularnych, można zoptymalizować wydajność przy użyciu wywołań metod statycznych i ewentualnie zwiększając rozmiar pamięci podręcznej wyrażeń regularnych.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
