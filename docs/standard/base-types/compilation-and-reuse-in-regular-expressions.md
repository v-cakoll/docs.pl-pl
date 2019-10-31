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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091733"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Aby zoptymalizować wydajność aplikacji, które dzielą użycie wyrażeń regularnych, można zrozumieć, jak aparat wyrażeń regularnych kompiluje wyrażenia i opisując, w jaki sposób są buforowane wyrażenia regularne. W tym temacie omówiono kompilację i pamięć podręczną.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenie regularne w celu uzyskania sekwencji wewnętrznych instrukcji (są to kody wysokiego poziomu, które różnią się od języka pośredniego firmy Microsoft lub MSIL). Gdy aparat wykonuje wyrażenie regularne, interpretuje kody wewnętrzne.  
  
 Jeśli obiekt <xref:System.Text.RegularExpressions.Regex> jest konstruowany przy użyciu opcji <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, kompiluje wyrażenie regularne na jawny kod MSIL zamiast zwykłych instrukcji wyrażenia regularnego na poziomie. To umożliwia. Kompilator "just-in-Time" (JIT) w sieci, aby przekonwertować wyrażenie na natywny kod maszynowy w celu zwiększenia wydajności.  
  
Nie można jednak zwolnić wygenerowanego MSIL. Jedynym sposobem zwolnienia kodu jest zwolnienie całej domeny aplikacji (czyli do zwolnienia wszystkich kodów aplikacji). Efektywnie, gdy wyrażenie regularne jest kompilowane przy użyciu opcji <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, nigdy nie zwalnia zasobów używanych przez skompilowane wyrażenie, nawet jeśli wyrażenie regularne zostało utworzone przez obiekt <xref:System.Text.RegularExpressions.Regex>, który jest samego zwalniany do wyrzucania elementów bezużytecznych.  
  
 Należy zachować ostrożność, aby ograniczyć liczbę różnych wyrażeń regularnych kompilowanych przy użyciu opcji <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>, aby uniknąć zużywania zbyt wielu zasobów. Jeśli aplikacja musi używać dużej lub nieograniczonej liczby wyrażeń regularnych, każde wyrażenie powinno być interpretowane, Nieskompilowane. Jednakże w przypadku wielokrotnego użycia niewielkiej liczby wyrażeń regularnych należy je skompilować przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> w celu uzyskania lepszej wydajności. Alternatywą jest użycie wstępnie skompilowanych wyrażeń regularnych. Wszystkie wyrażenia można kompilować do biblioteki DLL wielokrotnego użytku przy użyciu metody <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A>. Pozwala to uniknąć konieczności kompilowania w czasie wykonywania, a jednocześnie korzystać z szybkości kompilowanych wyrażeń regularnych.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych zachowuje pamięć podręczną dla skompilowanych wyrażeń regularnych. W pamięci podręcznej są przechowywane wzorce wyrażeń regularnych, które są używane tylko w wywołaniach metod statycznych. (Wzorce wyrażeń regularnych dostarczone do metod wystąpienia nie są buforowane). Pozwala to uniknąć konieczności ponownej analizy wyrażenia w kodzie bajtowym wysokiego poziomu za każdym razem, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest określana przez wartość `static` (`Shared` w Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> właściwość. Domyślnie aparat wyrażeń regularnych buforuje do 15 skompilowanych wyrażeń regularnych. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, najmniej ostatnio używane wyrażenie regularne jest odrzucane, a nowe wyrażenie regularne jest buforowane.  
  
 Twoja aplikacja może korzystać z wstępnie skompilowanych wyrażeń regularnych na jeden z następujących sposobów:  
  
- Użycie statycznej metody obiektu <xref:System.Text.RegularExpressions.Regex> w celu zdefiniowania wyrażenia regularnego. Jeśli używasz wzorca wyrażenia regularnego, który został już zdefiniowany w innym wywołaniu metody statycznej, aparat wyrażeń regularnych pobierze go z pamięci podręcznej. Jeśli nie, aparat kompiluje wyrażenie regularne i doda je do pamięci podręcznej.  
  
- Za pomocą tego obiektu <xref:System.Text.RegularExpressions.Regex>, o ile jest wymagany jego wzorzec wyrażenia regularnego.  
  
 Ze względu na koszty tworzenia wystąpień obiektów i kompilowania wyrażeń regularnych tworzenie i szybkie niszczenie wielu <xref:System.Text.RegularExpressions.Regex> obiektów jest bardzo kosztowne. W przypadku aplikacji, które korzystają z dużej liczby różnych wyrażeń regularnych, można zoptymalizować wydajność przy użyciu wywołań do statycznych metod `Regex` i ewentualnie przez zwiększenie rozmiaru pamięci podręcznej wyrażeń regularnych.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](../../../docs/standard/base-types/regular-expressions.md)
