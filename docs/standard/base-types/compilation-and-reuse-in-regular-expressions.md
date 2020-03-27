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
ms.openlocfilehash: b89f7f88233ecdab25ba2a74647aafeb4d8b74af
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344193"
---
# <a name="compilation-and-reuse-in-regular-expressions"></a>Kompilacja i ponowne użycie w wyrażeniach regularnych
Można zoptymalizować wydajność aplikacji, które szeroko korzystają z wyrażeń regularnych, rozumiejąc, jak aparat wyrażeń regularnych kompiluje wyrażenia i rozumiejąc, jak wyrażenia regularne są buforowane. W tym temacie omówiono zarówno kompilacji i buforowania.  
  
## <a name="compiled-regular-expressions"></a>Skompilowane wyrażenia regularne  
 Domyślnie aparat wyrażeń regularnych kompiluje wyrażenie regularne do sekwencji instrukcji wewnętrznych (są to kody wysokiego poziomu, które różnią się od języka pośredniego firmy Microsoft lub MSIL). Gdy aparat wykonuje wyrażenie regularne, interpretuje kody wewnętrzne.  
  
 Jeśli <xref:System.Text.RegularExpressions.Regex> obiekt jest skonstruowany <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> z opcją, kompiluje wyrażenie regularne do jawnego kodu MSIL zamiast instrukcji wewnętrznych wyrażeń regularnych wysokiego poziomu. Pozwala to . Net's just-in-time (JIT) kompilator do konwersji wyrażenia na natywny kod maszyny dla wyższej wydajności.  Koszt konstruowania <xref:System.Text.RegularExpressions.Regex> obiektu może być wyższa, ale koszt wykonywania dopasowań z nim może być znacznie mniejsza.

 Alternatywą jest użycie wstępnie skompilowanych wyrażeń regularnych. Można skompilować wszystkie wyrażenia do biblioteki DLL <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A> wielokrotnego użycia przy użyciu metody. Pozwala to uniknąć konieczności kompilowania w czasie wykonywania, a jednocześnie korzystających z szybkości skompilowanych wyrażeń regularnych.  
  
## <a name="the-regular-expressions-cache"></a>Pamięć podręczna wyrażeń regularnych  
 Aby zwiększyć wydajność, aparat wyrażeń regularnych utrzymuje ogólnoaunikową pamięć podręczną skompilowanych wyrażeń regularnych. Pamięć podręczna przechowuje wzorce wyrażeń regularnych, które są używane tylko w wywołaniach metod statycznych. (Wzorce wyrażeń regularnych dostarczane do metod wystąpienia nie są buforowane.) Pozwala to uniknąć konieczności ponownego połączenia wyrażenia do kodu bajtów wysokiego poziomu za każdym razem, gdy jest używany.  
  
 Maksymalna liczba buforowanych wyrażeń regularnych jest `static` określana przez wartość właściwości (w`Shared` języku Visual Basic). <xref:System.Text.RegularExpressions.Regex.CacheSize%2A?displayProperty=nameWithType> Domyślnie aparat wyrażeń regularnych buforuje do 15 skompilowanych wyrażeń regularnych. Jeśli liczba skompilowanych wyrażeń regularnych przekracza rozmiar pamięci podręcznej, najrzadziej używane wyrażenie regularne jest odrzucane, a nowe wyrażenie regularne jest buforowane.  
  
 Aplikacja może ponownie użyć wyrażeń regularnych na jeden z następujących dwóch sposobów:  
  
- Za pomocą metody statycznej <xref:System.Text.RegularExpressions.Regex> obiektu do definiowania wyrażenia regularnego. Jeśli używasz wzorca wyrażenia regularnego, który został już zdefiniowany przez inne wywołanie metody statycznej, aparat wyrażeń regularnych spróbuje pobrać go z pamięci podręcznej. Jeśli nie jest dostępna w pamięci podręcznej, aparat skompiluje wyrażenie regularne i doda je do pamięci podręcznej.
  
- Przez ponowne przywykczenie istniejącego <xref:System.Text.RegularExpressions.Regex> obiektu tak długo, jak jego wzorzec wyrażenia regularnego jest potrzebne.  
  
 Ze względu na obciążenie wystąpienia obiektu i kompilacji wyrażeń regularnych, <xref:System.Text.RegularExpressions.Regex> tworzenie i szybkie niszczenie wielu obiektów jest bardzo kosztowny proces. W przypadku aplikacji, które używają dużej liczby różnych wyrażeń regularnych, `Regex` można zoptymalizować wydajność przy użyciu wywołań do metod statycznych i ewentualnie przez zwiększenie rozmiaru pamięci podręcznej wyrażeń regularnych.  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia regularne platformy .NET](../../../docs/standard/base-types/regular-expressions.md)
