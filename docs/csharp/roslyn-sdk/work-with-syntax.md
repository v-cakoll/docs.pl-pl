---
title: Użyj modelu składni zestawu SDK platformy kompilatora .NET
description: Ten przegląd zawiera opis typów, używaną do manipulowania składni węzłów.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a48d48168dffdb439c984f5b4209019514b3b970
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706601"
---
# <a name="work-with-syntax"></a>Korzystanie ze składni

**Drzewo składni** to struktura danych podstawowych udostępnianych przez kompilator interfejsów API. Drzewa te reprezentują leksykalne i składniowych struktury kodu źródłowego. Służą one dwie ważne do celów:

1. Umożliwia narzędzi — takich jak środowisko IDE dodatków, kodu narzędzi do analizy i operacje refaktoryzacji — Aby wyświetlić i przetworzyć strukturę składni kodu źródłowego w projekcie użytkownika.
2. Aby włączyć narzędzia — takie jak operacje refaktoryzacji i środowisko IDE — do tworzenia, modyfikowania i rozmieszczanie kodu źródłowego w naturalny sposób bez konieczności zmiany tekstu bezpośredniego użycia. Tworzenie i manipulowanie drzewa, narzędzia łatwo można tworzyć i rozmieszczanie kodu źródłowego.

## <a name="syntax-trees"></a>Drzewa składni

Drzewa składni są podstawowej struktury używany dla kompilacji, analizy kodu, powiązanie, refaktoryzacji i generowanie kodu funkcji środowiska IDE. Żadna część kodu źródłowego jest zrozumiałe bez niego najpierw jest zidentyfikowany i dzieli na jeden z wielu elementów dobrze znanego języka strukturalnych. 

Drzewa składni ma trzy atrybuty kluczy. Pierwszy atrybut jest, że drzewa składni przechowywać wszystkie informacje o źródle w pełnej rozdzielczości. Oznacza to, że drzewo składni zawiera każdy fragment informacji w tekst źródłowy, co gramatyczne konstrukcji, każdy token leksykalne i wszystkie inne się między tym biały znak, komentarze i dyrektywy preprocesora. Na przykład każdy literał wymienione w źródle jest reprezentowany dokładnie tak, jak została zapisana. Drzewa składni również reprezentować błędów w kodzie źródłowym, gdy program jest niekompletny lub uszkodzony, poprzez reprezentowanie pominięto lub brak tokenów w drzewie składni.  

Dzięki temu drugi atrybut drzewa składni. Drzewo składni, uzyskany z analizatora może wygenerować tekstu do dokładnego dopasowania, który był analizowany z. Z poziomu każdego węzła składnia jest można uzyskać tekstowa reprezentacja poddrzewie na tym węźle. Oznacza to, że składnia drzewa mogą być używane jako sposobu konstruowania i edytować tekst źródłowy. Tworząc drzewo posiadanych przez domniemanie, utworzony tekst równoważnym i edytując drzewo składni wprowadzanie nowego drzewa poza zmiany w istniejącym drzewie, edytowano skutecznie tekstu. 

Trzeci atrybut drzewa składni jest są niezmienne i metodą o bezpiecznych wątkach.  Oznacza to, że po uzyskaniu drzewa jest migawką bieżącego stanu kod i nigdy się nie zmienia. To umożliwia wielu użytkownikom na interakcję z tym samym drzewie składni w tym samym czasie w różnych wątkach, bez blokowania lub dublowania. Ponieważ drzewa są niezmienne i żadnych modyfikacji nie jest możliwe bezpośrednio do drzewa, metodach fabryki pomagają tworzyć i modyfikować drzewa składni, tworząc dodatkowe migawek drzewa. Drzewa są efektywne w sposób ich ponownego użycia węzłów podrzędnych, więc nowej wersji można ponownie skompilować szybko i przy niewielkim dodatkową pamięć.

Drzewo składni jest dosłownie struktury drzewa danych, której elementy strukturalne-terminal nadrzędnego inne elementy. Każdy drzewo składni składa się z węzłów, tokenów i elementy towarzyszące składni.  

## <a name="syntax-nodes"></a>Składnia węzłów

Składnia węzły są jednym z podstawowe elementy drzewa składni. Węzły te reprezentują konstrukcji składniowych, takich jak deklaracje, instrukcje, klauzule i wyrażeń. Każda kategoria węzłów składnia jest reprezentowany przez oddzielne klasy pochodzącej od <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Zestaw klas węzeł nie jest rozszerzalny. 

Wszystkie węzły składni są-terminal węzłów w drzewie składni, co oznacza, że mają one zawsze inne węzły i tokenów jako elementy podrzędne. Jako element podrzędny innego węzła, każdy węzeł ma węzła nadrzędnego, który jest możliwy za pośrednictwem <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> właściwości. Ponieważ węzłów i drzewa są niezmienne, element nadrzędny węzła nigdy się nie zmienia. Główny drzewa ma element nadrzędny o wartości null.  

Każdy węzeł ma <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metody, która zwraca listę węzłów podrzędnych w kolejności sekwencyjnej, w oparciu o ich pozycji w tekście źródłowym. Ta lista nie zawiera tokenów. Każdy węzeł ma również metody, aby sprawdzić elementy podrzędne, takie jak <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, lub <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> — reprezentujące listy wszystkich węzłów, tokenów i elementy towarzyszące składni, która istnieje w poddrzewie odblokowany dostęp do tego węzła.  

Ponadto każda podklasa węzeł składni udostępnia te same elementy podrzędne za pośrednictwem silnie typizowane właściwości. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa węzła ma trzy dodatkowe właściwości specyficzne dla operatorów binarnych: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>oraz typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> jest <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Niektóre węzły składni mają opcjonalne elementy podrzędne. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> ma opcjonalny <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Jeśli nie ma elementu podrzędnego, właściwości zwracają wartość zero. 

## <a name="syntax-tokens"></a>Składnia tokenów

Składnia tokeny są terminali gramatyki języka, reprezentująca najmniejszą składni fragmentów kodu. Nigdy nie są one elementy nadrzędne w innych węzłach lub tokenów. Tokeny składni składają się z słów kluczowych, identyfikatory, literałów i znaki interpunkcyjne. 

Ze względów wydajności <xref:Microsoft.CodeAnalysis.SyntaxToken> typ jest typem wartości CLR. W związku z tym w przeciwieństwie do składni węzłów, istnieje tylko jedna struktura dla wszystkich rodzajów tokenów przy użyciu kombinacji właściwości, które mają znaczenie w zależności od rodzaju token, który jest reprezentowanego.

Na przykład tokenu literał liczby całkowitej reprezentuje wartość numeryczną. Oprócz tekst źródłowy pierwotne tokenu zakresy, token literału ma <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> właściwość, która informuje, dokładną zdekodować wartości całkowitej. Ta właściwość jest wpisana jako <xref:System.Object> ponieważ może to być jeden z wielu typów pierwotnych.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Właściwość zawiera informacje, te same informacje co <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> właściwości; jednak ta właściwość jest zawsze jako wpisana <xref:System.String>. Identyfikator w C# tekst źródłowy może zawierać znaków ucieczki Unicode jeszcze składnia sekwencji ucieczki, sama nie jest uważany za część nazwy identyfikatora. Tak, mimo że nieprzetworzony tekst objęte token obejmują sekwencja unikowa <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> nie obsługuje właściwości. Zamiast tego zawiera znaki Unicode, identyfikowany przez znak ucieczki. Na przykład, jeśli tekst źródłowy zawiera identyfikator zapisywane jako `\u03C0`, a następnie <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> właściwość dla tego tokenu będzie zwracać `π`.

## <a name="syntax-trivia"></a>Elementy towarzyszące składni składni

Elementy towarzyszące składni składni reprezentują części tekst źródłowy, które są w dużym stopniu nieznaczące normalne zrozumienie kodu, takich jak biały znak, komentarze i dyrektywy preprocesora. Podobnie jak tokeny składni elementy towarzyszące składni są typami wartości. Pojedynczy <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ jest używany do opisania wszelkiego rodzaju elementy towarzyszące składni.

Ponieważ elementy towarzyszące składni nie są częścią składni języka normalne i może występować w dowolnym miejscu między wszystkie dwa tokeny, są one nie uwzględnione w drzewie składni jako element podrzędny węzła. Jeszcze ponieważ są one ważne podczas implementowania funkcji, takich jak Refaktoryzacja i zapewnić pełną zgodność z tekst źródłowy, są dostępne jako część drzewa składni.

Elementy towarzyszące składni można uzyskać dostęp, sprawdzając, czy token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekcji. Gdy zostanie przeanalizowany tekst źródłowy, sekwencji elementy towarzyszące składni są skojarzone z tokenami. Ogólnie rzecz biorąc token jest właścicielem wszelkie elementy towarzyszące składni po nim w tym samym wierszu, aż do następnego tokenu. Wszystkie elementy towarzyszące składni po tym wierszu jest skojarzony z następującego tokenu. Pierwszy token w pliku źródłowym pobiera wszystkie początkowe elementy towarzyszące składni i kumulowany jest ostatnią sekwencję elementy towarzyszące składni w pliku na token końca pliku, która w przeciwnym razie ma zerowej szerokości.

W przeciwieństwie do składni węzłów i tokenów składnia elementy towarzyszące składni nie mają elementów nadrzędnych. Jeszcze, ponieważ są one częścią drzewa, a każda jest skojarzony z pojedynczy token, dostęp można uzyskać tokenu jest skojarzony z przy użyciu <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> właściwości.

## <a name="spans"></a>Zakresy

Każdy węzeł, token lub elementy towarzyszące składni zna jego pozycja w tekście źródłowym i liczbę znaków, który składa się z. Położenie tekstu jest reprezentowany jako 32-bitową liczbę całkowitą, która jest liczony od zera `char` indeksu. Element <xref:Microsoft.CodeAnalysis.Text.TextSpan> obiektu pozycję początkową i liczba znaków, zarówno w postaci liczb całkowitych. Jeśli <xref:Microsoft.CodeAnalysis.Text.TextSpan> ma zerową długość, odwołuje się do lokalizacji między dwoma znakami.

Każdy węzeł ma dwa <xref:Microsoft.CodeAnalysis.Text.TextSpan> właściwości: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> i <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Właściwość jest zakres tekstu od początku pierwszym tokenem w poddrzewie węzła do końca ostatni token. Ten zakres nie obejmuje żadnych wiodących ani końcowych elementy towarzyszące składni.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Właściwość jest obszaru tekstu, który obejmuje podrzędnego span normalne oraz zakres dowolnego wiodących ani końcowych elementy towarzyszące składni.

Na przykład: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Węzeł instrukcji wewnątrz bloku zawiera zakres wskazywany przez pojedynczy pionowych słupków (|). Zawiera on znaki `throw new Exception("Not right.");`. Pełny zakres jest wskazywany przez podwójne paski pionowej (|). Zawiera te same znaki, jako zakres i znaków skojarzonych elementy towarzyszące składni początkowe i końcowe.

## <a name="kinds"></a>Rodzaje

Każdy węzeł, token lub elementy towarzyszące składni ma <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> właściwość typu <xref:System.Int32?displayProperty=nameWithType>, który identyfikuje element dokładna składnia reprezentowany. Ta wartość może być rzutowany na wyliczenie specyficzny dla języka; Każdy język C# lub VB, ma jeden `SyntaxKind` wyliczenia (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> i <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>odpowiednio), zawiera listę wszystkich możliwych węzłów, tokenów i elementy towarzyszące składni elementów, w gramatyce. Ta konwersja może odbywać się automatycznie, uzyskując dostęp do <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> metody rozszerzenia.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Właściwość zezwala na Uściślanie proste typy węzłów składni, które mają tej samej klasie w węźle. Tokeny i elementy towarzyszące składni ta właściwość jest jedynym sposobem, aby odróżnić jeden typ elementu z innego. 

Na przykład pojedynczy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako elementy podrzędne. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Właściwość różnic między usługą, czy jest ono <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, lub <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> rodzaj węzła składni.

## <a name="errors"></a>błędy

Nawet wtedy, gdy tekst źródłowy zawiera błędy składni, jest udostępniany drzewa pełną składnię, która jest wysyłanych do źródła. Gdy analizator składni napotka kod, który jest niezgodny ze zdefiniowanych składni języka, używa jednego z dwóch technik tworzenia drzewa składni.

Po pierwsze Jeśli parser oczekuje określonego rodzaju token, ale nie zostanie znaleziona, jego może Wstawianie Brak tokenu drzewa składni w lokalizacji, oczekiwany token. Brak tokenu reprezentuje rzeczywisty token, który był oczekiwany, ale ma pusty zakres i jego <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> właściwość zwraca `true`.

Po drugie analizator może pominąć tokenów, dopóki nie zostanie znaleziony taki, gdzie można kontynuować, analizowanie. W tym przypadku pominiętych tokeny są dołączone jako węzeł elementy towarzyszące składni z rodzajem <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
