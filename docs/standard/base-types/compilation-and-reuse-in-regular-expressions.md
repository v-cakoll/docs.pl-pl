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
ms.openlocfilehash: 54f14a4f31bef00dd222686cc523935b2d9dd5fa
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279041"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Aby zoptymalizować wydajność aplikacji, które dzielą użycie wyrażeń regularnych, można zrozumieć, jak aparat wyrażeń regularnych kompiluje wyrażenia i opisując, w jaki sposób są buforowane wyrażenia regularne. W tym temacie omówiono kompilację i pamięć podręczną.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenie regularne w celu uzyskania sekwencji wewnętrznych instrukcji (są to kody wysokiego poziomu, które różnią się od języka pośredniego firmy Microsoft lub MSIL). Gdy aparat wykonuje wyrażenie regularne, interpretuje kody wewnętrzne.  
  
 Jeśli <xref:System.Text.RegularExpressions.Regex> obiekt jest skonstruowany przy użyciu <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> opcji, kompiluje wyrażenie regularne na jawny kod MSIL zamiast ogólnych instrukcji ogólnego wyrażenia regularnego. To umożliwia. Kompilator "just-in-Time" (JIT) w sieci, aby przekonwertować wyrażenie na natywny kod maszynowy w celu zwiększenia wydajności.  Koszt konstruowania <xref:System.Text.RegularExpressions.Regex> obiektu może być wyższy, ale koszt wykonywania dopasowań jest prawdopodobnie dużo mniejszy.

 Alternatywą jest użycie wstępnie skompilowanych wyrażeń regularnych. Wszystkie wyrażenia można kompilować do biblioteki DLL wielokrotnego użytku przy użyciu <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> metody. Pozwala to uniknąć konieczności kompilowania w czasie wykonywania, a jednocześnie korzystać z szybkości kompilowanych wyrażeń regularnych.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych zachowuje pamięć podręczną dla skompilowanych wyrażeń regularnych. W pamięci podręcznej są przechowywane wzorce wyrażeń regularnych, które są używane tylko w wywołaniach metod statycznych. (Wzorce wyrażeń regularnych dostarczone do metod wystąpienia nie są buforowane). Pozwala to uniknąć konieczności ponownej analizy wyrażenia w kodzie bajtowym wysokiego poziomu za każdym razem, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest określana przez wartość `static` `Shared` właściwości (w Visual Basic) <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> . Domyślnie aparat wyrażeń regularnych buforuje do 15 skompilowanych wyrażeń regularnych. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, najmniej ostatnio używane wyrażenie regularne jest odrzucane, a nowe wyrażenie regularne jest buforowane.  
  
 Aplikacja może ponownie używać wyrażeń regularnych na jeden z następujących sposobów:  
  
- Przy użyciu statycznej metody <xref:System.Text.RegularExpressions.Regex> obiektu do definiowania wyrażenia regularnego. Jeśli używasz wzorca wyrażenia regularnego, który został już zdefiniowany przez inne wywołanie metody statycznej, aparat wyrażeń regularnych podejmie próbę pobrania go z pamięci podręcznej. Jeśli nie jest dostępna w pamięci podręcznej, aparat kompiluje wyrażenie regularne i doda je do pamięci podręcznej.
  
- Przez użycie istniejącego <xref:System.Text.RegularExpressions.Regex> obiektu, o ile jest wymagany jego wzorzec wyrażenia regularnego.  
  
 Ze względu na koszty tworzenia wystąpień obiektów i kompilowania wyrażeń regularnych tworzenie i szybkie niszczenie wielu <xref:System.Text.RegularExpressions.Regex> obiektów jest bardzo kosztowne. W przypadku aplikacji, które korzystają z dużej liczby różnych wyrażeń regularnych, można zoptymalizować wydajność przy użyciu wywołań metod statycznych `Regex` i prawdopodobnie przez zwiększenie rozmiaru pamięci podręcznej wyrażeń regularnych.  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia regularne .NET](regular-expressions.md)
