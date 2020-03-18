---
title: Korzystanie z modelu składni platformy SDK platformy kompilatora .NET
description: Ten przegląd zawiera zrozumienie typów używanych do rozumienia i manipulowania węzłami składni.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: fc1b1f5ae5ec985425c8d6aec49ef7f830ea9162
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740477"
---
# <a name="work-with-syntax"></a>Korzystanie ze składni

**Drzewo składni** jest podstawową strukturą danych uwidacznioną przez interfejsy API kompilatora. Drzewa te reprezentują leksykalne i syntaktyczne struktury kodu źródłowego. Służą one dwóm ważnym celom:

1. Aby umożliwić narzędzia — takie jak IDE, dodatki, narzędzia do analizy kodu i refaktoryzacji — aby wyświetlić i przetworzyć strukturę składni kodu źródłowego w projekcie użytkownika.
2. Aby włączyć narzędzia — takie jak refaktoryzacji i IDE - do tworzenia, modyfikowania i zmiany rozmieszczenia kodu źródłowego w sposób naturalny bez konieczności używania bezpośrednich zmian tekstu. Tworząc i manipulując drzewami, narzędzia można łatwo tworzyć i zmieniać rozmieszczenie kodu źródłowego.

## <a name="syntax-trees"></a>Drzewa składni

Drzewa składni są podstawową strukturą używaną do kompilacji, analizy kodu, wiązania, refaktoryzacji, funkcji IDE i generowania kodu. Żadna część kodu źródłowego nie jest rozumiana bez jego uprzedniego zidentyfikowania i sklasyfikowania w jednym z wielu znanych elementów języka strukturalnego.

Drzewa składni mają trzy kluczowe atrybuty. Pierwszym atrybutem jest to, że drzewa składni posiadają wszystkie informacje źródłowe w pełnej wierności. Oznacza to, że drzewo składni zawiera wszystkie informacje znalezione w tekście źródłowym, każdą konstrukcję gramatyczną, każdy token leksykalne i wszystko inne pomiędzy, w tym biały znak, komentarze i dyrektywy preprocesora. Na przykład każdy dosłowny wymieniony w źródle jest reprezentowany dokładnie tak, jak został wpisany. Drzewa składni reprezentują również błędy w kodzie źródłowym, gdy program jest niekompletny lub nieprawidłowo sformułowany przez reprezentowanie pominiętych lub brakujących tokenów w drzewie składni.

Umożliwia to drugi atrybut drzewa składni. Drzewo składni uzyskane z analizatora może spowodować, że tekst został przeanalizowany. Z dowolnego węzła składni można uzyskać reprezentację tekstu poddrzewa zakorzenionew tym węźle. Oznacza to, że drzewa składni mogą służyć jako sposób konstruowania i edytowania tekstu źródłowego. Tworząc drzewo, które zostały utworzone przez domniemanie równoważny tekst i edytując drzewo składni, tworząc nowe drzewo ze zmian w istniejącym drzewie, skutecznie edytowałeś tekst.

Trzeci atrybut drzewa składni jest, że są one niezmienne i wątku bezpieczne.  Oznacza to, że po drzewo jest uzyskiwany, jest migawką bieżącego stanu kodu i nigdy się nie zmienia. Dzięki temu wielu użytkowników do interakcji z tym samym drzewem składni w tym samym czasie w różnych wątków bez blokowania lub powielania. Ponieważ drzewa są niezmienne i nie można wprowadzać żadnych modyfikacji bezpośrednio do drzewa, metody fabryki pomagają tworzyć i modyfikować drzewa składni, tworząc dodatkowe migawki drzewa. Drzewa są wydajne w sposobie ponownego wykorzystania podstawowych węzłów, dzięki czemu nowa wersja może być szybko przebudowana i z niewielką ilością dodatkowej pamięci.

Drzewo składni jest dosłownie strukturą danych drzewa, w której niekońcowe elementy konstrukcyjne są nadrzędne dla innych elementów. Każde drzewo składni składa się z węzłów, tokenów i ciekawostek.

## <a name="syntax-nodes"></a>Węzły składni

Węzły składni są jednym z podstawowych elementów drzew składni. Te węzły reprezentują konstrukcje składni, takie jak deklaracje, instrukcje, klauzule i wyrażenia. Każda kategoria węzłów składni jest reprezentowana przez oddzielną klasę wyprowadzoną z <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Zestaw klas węzłów nie jest rozszerzalny.

Wszystkie węzły składni są węzłami niekońcowymw drzewie składni, co oznacza, że zawsze mają inne węzły i tokeny jako podrzędne. Jako element podrzędny innego węzła każdy węzeł ma węzeł nadrzędny, do których można uzyskać dostęp za pośrednictwem <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> właściwości. Ponieważ węzły i drzewa są niezmienne, element nadrzędny węzła nigdy się nie zmienia. Katalog główny drzewa ma null nadrzędnego.

Każdy węzeł ma <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodę, która zwraca listę węzłów podrzędnych w kolejności na podstawie ich pozycji w tekście źródłowym. Ta lista nie zawiera tokenów. Każdy węzeł ma również metody do zbadania <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>Descendants, takich jak , , lub <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> - które reprezentują listę wszystkich węzłów, tokenów lub ciekawostki, które istnieją w poddrzewie zakorzenione w tym węźle.

Ponadto każda podklasa węzła składni udostępnia wszystkie te same właściwości podrzędne za pośrednictwem właściwości silnie typowane. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa węzła ma trzy dodatkowe właściwości <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>specyficzne <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>dla <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>operatorów binarnych: , , i . Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> typ <xref:Microsoft.CodeAnalysis.SyntaxToken>jest .

Niektóre węzły składni mają opcjonalne elementy podrzędne. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> ma opcjonalny <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Jeśli dziecko nie jest obecny, właściwość zwraca null.

## <a name="syntax-tokens"></a>Tokeny składni

Tokeny składni są terminalami gramatyki językowej, reprezentującymi najmniejsze fragmenty składni kodu. Nigdy nie są rodzicami innych węzłów lub tokenów. Tokeny składni składają się ze słów kluczowych, identyfikatorów, literałów i znaków interpunkcyjnych.

Dla celów wydajności <xref:Microsoft.CodeAnalysis.SyntaxToken> typ jest typem wartości CLR. W związku z tym w przeciwieństwie do węzłów składni, istnieje tylko jedna struktura dla wszystkich rodzajów tokenów z kombinacją właściwości, które mają znaczenie w zależności od rodzaju tokenu, który jest reprezentowany.

Na przykład token literału całkowitego reprezentuje wartość liczbową. Oprócz nieprzetworzonego tekstu źródłowego, który obejmuje token, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> token literału ma właściwość, która informuje o dokładnej wartości zdekodowanej liczby całkowitej. Ta właściwość jest <xref:System.Object> wpisana jako, ponieważ może być jednym z wielu typów pierwotnych.

Właściwość <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> informuje o tych samych informacjach, <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> co właściwość; jednak ta właściwość jest <xref:System.String>zawsze wpisana jako . Identyfikator w tekście źródłowym Języka C# może zawierać znaki ucieczki Unicode, ale składnia samej sekwencji ucieczki nie jest uważana za część nazwy identyfikatora. Tak więc, mimo że nieprzetworzony tekst łączony przez <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> token zawiera sekwencję ucieczki, właściwość nie. Zamiast tego zawiera znaki Unicode identyfikowane przez escape. Na przykład jeśli tekst źródłowy zawiera `\u03C0`identyfikator <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> napisany jako , `π`a następnie właściwość dla tego tokenu zwróci .

## <a name="syntax-trivia"></a>Ciekawostki składni

Ciekawostki składni reprezentują części tekstu źródłowego, które są w dużej mierze nieistotne dla normalnego zrozumienia kodu, takie jak białe pole, komentarze i dyrektywy preprocesora. Podobnie jak tokeny składni, ciekawostki są typami wartości. Pojedynczy <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ jest używany do opisania wszelkiego rodzaju ciekawostek.

Ponieważ ciekawostki nie są częścią składni języka normalnego i mogą być wyświetlane w dowolnym miejscu między dowolnymi dwoma tokenami, nie są one uwzględniane w drzewie składni jako element podrzędny węzła. Jednak ponieważ są one ważne podczas implementowania funkcji, takich jak refaktoryzacji i zachować pełną wierność z tekstem źródłowym, istnieją one jako część drzewa składni.

Możesz uzyskać dostęp do ciekawostek, sprawdzając token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekcje. Gdy tekst źródłowy jest analizowany, sekwencje ciekawostki są skojarzone z tokenami. Ogólnie rzecz biorąc token jest właścicielem wszelkich ciekawostek po nim w tym samym wierszu do następnego tokenu. Wszelkie ciekawostki po tym wierszu jest skojarzony z następującym tokenem. Pierwszy token w pliku źródłowym pobiera wszystkie początkowe ciekawostki, a ostatnia sekwencja ciekawostek w pliku jest przyklejona do tokenu końca pliku, który w przeciwnym razie ma zerową szerokość.

W przeciwieństwie do węzłów składni i tokenów, ciekawostki składni nie mają właściwości rodziców. Jednak ponieważ są one częścią drzewa i każdy jest skojarzony z pojedynczym tokenem, można uzyskać dostęp do tokenu, który jest skojarzony z przy użyciu <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> właściwości.

## <a name="spans"></a>Obejmuje

Każdy węzeł, token lub ciekawostki zna jego pozycję w tekście źródłowym i liczbę znaków, na których się składa. Pozycja tekstowa jest reprezentowana jako 32-bitowa liczba całkowita, która jest indeksem zerowym. `char` Obiekt <xref:Microsoft.CodeAnalysis.Text.TextSpan> jest pozycją początku i liczbą znaków, oba reprezentowane jako liczby całkowite. Jeśli <xref:Microsoft.CodeAnalysis.Text.TextSpan> ma długość zerową, odnosi się do lokalizacji między dwoma znakami.

Każdy węzeł ma <xref:Microsoft.CodeAnalysis.Text.TextSpan> dwie <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> właściwości: i <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>.

Właściwość <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> jest zakres tekstu od początku pierwszego tokenu w poddrzewie węzła do końca ostatniego tokenu. Zakres ten nie zawiera żadnych wiodących lub końcowych ciekawostki.

Właściwość <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> jest zakres tekstu, który zawiera normalny zakres węzła, plus zakres wszelkich wiodących lub końcowych ciekawostki.

Przykład:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Węzeł instrukcji wewnątrz bloku ma zakres wskazany przez pojedyncze pionowe pręty (|). Zawiera znaki `throw new Exception("Not right.");`. Pełny zakres jest oznaczony podwójnymi pionowymi prętami (||). Zawiera te same znaki, co zakres i znaki związane z wiodącymi i kończącymi się ciekawostkami.

## <a name="kinds"></a>Rodzaje

Każdy węzeł, token lub ciekawostki <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> ma <xref:System.Int32?displayProperty=nameWithType>właściwość typu , która identyfikuje dokładny element składni reprezentowany. Tę wartość można rzutować na wyliczenie specyficzne dla języka. Każdy język, C# lub Visual `SyntaxKind` Basic, ma<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>pojedyncze wyliczenie ( i , odpowiednio), który zawiera listę wszystkich możliwych węzłów, tokenów i elementów ciekawostki w gramatyki. Ta konwersja może być wykonana <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> automatycznie, uzyskując dostęp do metod lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType> rozszerzenia.

Właściwość <xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> umożliwia łatwe rozróżnianie typów węzłów składni, które mają tę samą klasę węzła. Dla tokenów i ciekawostki ta właściwość jest jedynym sposobem, aby odróżnić jeden typ elementu od innego.

Na przykład jedna <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> , i jako dzieci. Właściwość <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A> <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>rozróżnia, czy <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>jest <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> to , , lub rodzaj węzła składni.

## <a name="errors"></a>Errors

Nawet jeśli tekst źródłowy zawiera błędy składni, pełne drzewo składni, które można w obie strony do źródła jest narażony. Gdy analizator napotka kod, który nie jest zgodny ze zdefiniowaną składnią języka, używa jednej z dwóch technik do utworzenia drzewa składni.

Po pierwsze, jeśli analizator oczekuje określonego rodzaju tokenu, ale go nie znajdzie, może wstawić brakujący token do drzewa składni w lokalizacji, której oczekiwano tokenu. Brakujący token reprezentuje rzeczywisty token, który był oczekiwany, ale ma <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> pusty `true`zakres, a jego właściwość zwraca .

Po drugie analizator może pominąć tokeny, dopóki nie znajdzie jeden, gdzie można kontynuować analizowanie. W takim przypadku pominięte tokeny są dołączone jako węzeł ciekawostki z rodzaju <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
