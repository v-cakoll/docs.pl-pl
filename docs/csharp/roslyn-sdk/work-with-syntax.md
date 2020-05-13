---
title: Użyj modelu składni .NET Compiler Platform SDK
description: To omówienie zawiera opis typów używanych do zrozumienia i manipulowania węzłami składni.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: fdb13095c2b91e54d58988a51a51b05652e57ea6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208398"
---
# <a name="work-with-syntax"></a>Korzystanie ze składni

*Drzewo składni* jest podstawową strukturą danych uwidocznioną przez interfejsy API kompilatora. Te drzewa reprezentują strukturę leksykalną i składnię kodu źródłowego. Służą one do dwóch istotnych celów:

- Aby umożliwić korzystanie z narzędzi, takich jak środowisko IDE, dodatki, narzędzia do analizy kodu i refaktoryzacje — aby zobaczyć i przetworzyć strukturę składni kodu źródłowego w projekcie użytkownika.
- Aby włączyć narzędzia — takie jak refaktoryzacje i środowisko IDE — do tworzenia, modyfikowania i ponownego rozmieszczania kodu źródłowego w naturalny sposób bez konieczności używania bezpośredniej edycji tekstu. Tworząc i manipulowania drzewami, narzędzia mogą łatwo tworzyć i zmieniać rozmieszczenie kodu źródłowego.

## <a name="syntax-trees"></a>Drzewa składni

Drzewa składni są podstawową strukturą używaną do kompilowania, analizy kodu, powiązania, refaktoryzacji, funkcji środowiska IDE i generowania kodu. Żadna część kodu źródłowego nie jest zrozumiała bez jej pierwszego zidentyfikowania i sklasyfikowania do jednego z wielu dobrze znanych elementów języka strukturalnego.

Drzewa składni mają trzy atrybuty klucza. Pierwszym atrybutem jest to, że drzewa składni przechowują wszystkie informacje źródłowe z pełną dokładnością. Pełna wierność oznacza, że drzewo składni zawiera wszystkie informacje znajdujące się w tekście źródłowym, każda konstrukcja gramatyczna, każdy token leksykalny i wszystkie inne elementy między, w tym białe miejsce, komentarze i dyrektywy preprocesora. Na przykład każdy literał wymieniony w źródle jest reprezentowany dokładnie w takiej postaci, w jakiej został wprowadzony. Drzewa składni również przechwytują błędy w kodzie źródłowym, gdy program jest niekompletny lub nieprawidłowo sformułowany przez reprezentowanie pominiętych lub brakujących tokenów.

Drugim atrybutem drzew składni jest to, że mogą one generować dokładny tekst, z którego zostały przeanalizowane. Z dowolnego węzła składni można uzyskać tekstową reprezentację poddrzewa znajdującego się w tym węźle. Ta możliwość oznacza, że drzewa składni mogą służyć jako sposób konstruowania i edytowania tekstu źródłowego. Tworząc drzewo posiadane przez program, aby utworzyć odpowiedni tekst, i edytując drzewo składni, wprowadzając nowe drzewo poza zmianami w istniejącym drzewie, możesz efektywnie edytować tekst.

Trzeci atrybut drzew składni polega na tym, że są one niezmienne i bezpieczne wątkowo. Po uzyskaniu drzewa jest on migawką bieżącego stanu kodu i nigdy nie ulega zmianie. Dzięki temu wielu użytkowników może jednocześnie korzystać z tego samego drzewa składni w różnych wątkach bez blokowania ani duplikowania. Ponieważ drzewa są niezmienne i nie można wprowadzać modyfikacji bezpośrednio do drzewa, metody fabryki ułatwiają tworzenie i modyfikowanie drzew składniowych przez tworzenie dodatkowych migawek drzewa. Drzewa są wydajne w sposób, w jaki ponownie korzystają z węzłów źródłowych, więc nową wersję można skompilować szybko i przy użyciu małej ilości dodatkowej pamięci.

Drzewo składni jest dosłownie strukturą danych drzewa, w której elementy strukturalne niebędące elementami nadrzędnymi innych elementów są nadrzędne. Każde drzewo składni składa się z węzłów, tokenów i kwizy.

## <a name="syntax-nodes"></a>Węzły składni

Węzły składni są jednym z głównych elementów drzew składni. Te węzły reprezentują konstrukcje składniowe, takie jak deklaracje, instrukcje, klauzule i wyrażenia. Każda kategoria węzłów składni jest reprezentowana przez oddzielną klasę pochodną od <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> . Zestaw klas węzłów nie jest rozszerzalny.

Wszystkie węzły składni nie są węzłami terminalu w drzewie składni, co oznacza, że zawsze mają inne węzły i tokeny jako elementy podrzędne. Jako element podrzędny innego węzła każdy węzeł ma węzeł nadrzędny, do którego można uzyskać dostęp za pomocą <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> właściwości. Ponieważ węzły i drzewa są niezmienne, nadrzędny węzeł nigdy nie ulega zmianie. Katalog główny drzewa ma element nadrzędny o wartości null.

Każdy węzeł ma <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodę, która zwraca listę węzłów podrzędnych w kolejności sekwencyjnej na podstawie ich położenia w tekście źródłowym. Ta lista nie zawiera tokenów. Każdy węzeł ma także metody do badania elementów podrzędnych, takich jak <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> , <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A> , lub <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> reprezentujące listę wszystkich węzłów, tokenów lub kwizy, które istnieją w poddrzewie głównym, które znajdują się w tym węźle.

Ponadto każda podklasa węzłów węzła uwidacznia wszystkie te same elementy podrzędne za pomocą właściwości silnie wpisanych. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> Klasa węzła ma trzy dodatkowe właściwości specyficzne dla operatorów binarnych: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> , i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> . Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax> , i typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> to <xref:Microsoft.CodeAnalysis.SyntaxToken> .

Niektóre węzły składni mają opcjonalne elementy podrzędne. Na przykład, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> ma opcjonalnie <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax> . Jeśli element podrzędny nie istnieje, właściwość zwraca wartość null.

## <a name="syntax-tokens"></a>Tokeny składni

Tokeny składni to terminale gramatyki języka, reprezentujące najmniejsze fragmenty składni kodu. Nigdy nie są nadrzędne w stosunku do innych węzłów lub tokenów. Tokeny składni składają się z słów kluczowych, identyfikatorów, literałów i znaków interpunkcyjnych.

W celu zapewnienia wydajności <xref:Microsoft.CodeAnalysis.SyntaxToken> Typ jest typem wartości CLR. W związku z tym w przeciwieństwie do węzłów składni istnieje tylko jedna struktura dla wszystkich rodzajów tokenów z mieszaniem właściwości, które mają znaczenie w zależności od rodzaju reprezentowanego tokenu.

Na przykład token literału Integer reprezentuje wartość liczbową. Oprócz pierwotnego tekstu źródła, który obejmuje token, token literału ma <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> Właściwość, która informuje o dokładnej zdekodowanej wartości całkowitej. Ta właściwość jest wpisana jako <xref:System.Object> ponieważ może być jednym z wielu typów pierwotnych.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText>Właściwość informuje o tym te same informacje, co <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> Właściwość; jednak ta właściwość zawsze jest wpisana jako <xref:System.String> . Identyfikator w tekście źródłowym języka C# może zawierać znaki ucieczki Unicode, a mimo to składnia sekwencji unikowej nie jest uważana za część nazwy identyfikatora. Mimo że nieprzetworzony tekst objęty tokenem zawiera sekwencję ucieczki, <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Właściwość nie jest. Zamiast tego zawiera znaki Unicode identyfikowane przez Escape. Na przykład, jeśli tekst źródłowy zawiera identyfikator zapisany jako `\u03C0` , wówczas <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Właściwość dla tego tokenu zwróci wartość `π` .

## <a name="syntax-trivia"></a>Kwizy składni

Składnia kwizy reprezentuje części tekstu źródłowego, które są w znacznym stopniu nieważne do normalnego poznania kodu, takie jak białe znaki, komentarze i dyrektywy preprocesora. Podobnie jak tokeny składniowe, kwizy są typami wartości. Pojedynczy <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> Typ jest używany do opisywania wszystkich rodzajów kwizy.

Ponieważ kwizy nie są częścią standardowej składni języka i mogą znajdować się w dowolnym miejscu między dwoma tokenami, nie są uwzględniane w drzewie składni jako element podrzędny węzła. Jeszcze ponieważ są one ważne podczas implementowania funkcji, takiej jak Refaktoryzacja i aby zachować pełną wierność z tekstem źródłowym, są one dostępne jako część drzewa składni.

Dostęp do kwizy można uzyskać, sprawdzając token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekcje. Po przeanalizowaniu tekstu źródłowego sekwencje kwizy są skojarzone z tokenami. Ogólnie rzecz biorąc, token jest własnością dowolnego kwizy po tej samej linii do następnego tokenu. Wszystkie kwizy po tym wierszu są skojarzone z poniższym tokenem. Pierwszy token w pliku źródłowym pobiera wszystkie początkowe kwizy, a Ostatnia sekwencja kwizy w pliku jest prostopadła do tokenu końca pliku, w przeciwnym razie ma zerową szerokość.

W przeciwieństwie do węzłów składni i tokenów składnia kwizy nie ma elementów nadrzędnych. Jeszcze ponieważ są one częścią drzewa, a każda z nich jest skojarzona z pojedynczym tokenem, można uzyskać dostęp do tokenu skojarzonego z użyciem <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> właściwości.

## <a name="spans"></a>Obejmuje

Każdy węzeł, token lub kwizy wie swoją pozycję w tekście źródłowym oraz liczbę znaków, które zawiera. Pozycja tekstowa jest reprezentowana jako 32-bitowa liczba całkowita, która jest indeksem liczonym od zera `char` . <xref:Microsoft.CodeAnalysis.Text.TextSpan>Obiekt jest pozycją początkową i liczbą znaków, reprezentowanych jako liczby całkowite. Jeśli <xref:Microsoft.CodeAnalysis.Text.TextSpan> ma zerową długość, odnosi się do lokalizacji między dwoma znakami.

Każdy węzeł ma dwie <xref:Microsoft.CodeAnalysis.Text.TextSpan> Właściwości: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A> i <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A> .

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span%2A>Właściwość jest zakresem tekstu od początku pierwszego tokenu w poddrzewie węzła do końca ostatniego tokenu. Ten zakres nie obejmuje żadnych kwizy wiodących ani końcowych.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan%2A>Właściwość jest zakresem tekstu, który obejmuje normalny zakres węzła oraz zakres wszystkich wiodących lub końcowych kwizy.

Przykład:

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Węzeł instrukcji wewnątrz bloku ma zakres wskazany przez pojedyncze pionowe słupki (|). Zawiera znaki `throw new Exception("Not right.");` . Pełny zakres jest wskazywany przez podwójne pionowe słupki (| |). Zawiera te same znaki, jak zakres i znaki skojarzone z kwizy wiodące i końcowe.

## <a name="kinds"></a>Rodzaje

Każdy węzeł, token lub kwizy ma <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> Właściwość typu <xref:System.Int32?displayProperty=nameWithType> , która identyfikuje dokładnie przedstawiony element składni. Ta wartość może być rzutowana na Wyliczenie specyficzne dla języka. Każdy język, C# lub Visual Basic, ma pojedyncze `SyntaxKind` Wyliczenie ( <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType> odpowiednio), które wyświetla listę wszystkich możliwych węzłów, tokenów i elementów kwizy w gramatyce. Tę konwersję można wykonać automatycznie, uzyskując dostęp do <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind%2A?displayProperty=nameWithType> metod rozszerzenia lub.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind>Właściwość umożliwia łatwe Uściślanie typów węzłów składni, które współużytkują tę samą klasę węzła. W przypadku tokenów i kwizy ta właściwość jest jedynym sposobem odróżnienia jednego typu elementu od innego.

Na przykład pojedyncza <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> Klasa ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> , <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> , i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako elementy podrzędne. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind%2A>Właściwość określa, czy jest to <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression> <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression> węzeł składni, czy też <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> .

## <a name="errors"></a>Errors

Nawet wtedy, gdy tekst źródłowy zawiera błędy składni, ujawniane jest pełne drzewo składni, które jest dwustronnie obsługiwane dla źródła. Gdy analizator napotka kod, który nie jest zgodny ze zdefiniowaną składnią języka, używa jednej z dwóch technik do tworzenia drzewa składni:

- Jeśli analizator oczekuje określonego rodzaju tokenu, ale nie znajdzie go, może wstawić brakującego tokenu do drzewa składni w lokalizacji, w której Oczekiwano tokenu. Brakujący token reprezentuje rzeczywisty token, który był oczekiwany, ale ma pusty zakres, a jego <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> Właściwość zwraca `true` .

- Analizator może pominąć tokeny do momentu znalezienia, gdzie można kontynuować analizowanie. W takim przypadku pominięte tokeny są dołączane jako węzeł kwizy o rodzaju <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia> .
