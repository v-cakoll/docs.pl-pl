---
title: Użyj zestawu SDK platformy kompilatora .NET modelu składni
description: Ten przegląd zawiera opis typów, używaną do zrozumienia i manipulowania składni węzłów.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a48d48168dffdb439c984f5b4209019514b3b970
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="work-with-syntax"></a>Praca z składni

**Drzewa składni** to struktura danych podstawowych udostępnianych przez kompilator interfejsów API. Drzewa te reprezentuje strukturę leksykalne i składni kodu źródłowego. Służą one ważne do dwóch celów:

1. Umożliwia narzędzia — takie jak IDE dodatków, kodu narzędzi analizy i refaktoryzacje — Zobacz i przetwarzać składni struktury kodu źródłowego w projekcie użytkownika.
2. Aby włączyć narzędzia — takie jak refaktoryzacje i IDE — do tworzenia, modyfikowania i rozmieszczanie kodu źródłowego w sposób fizycznych bez konieczności edytowanych wartości tekstowych bezpośredniego użycia. Tworzenie i manipulowanie drzewa, narzędzia łatwo tworzyć i rozmieszczanie kodu źródłowego.

## <a name="syntax-trees"></a>Drzewa składni

Drzewa składni są podstawowej struktury używany dla kompilacji, analizy kodu, powiązanie, refaktoryzacji funkcje IDE i generowania kodu. Żadna część kod źródłowy jest rozpoznawany bez najpierw są zidentyfikowane i przydzielone do jednego z wielu elementów dobrze znanego strukturalnych języka. 

Drzewa składni ma trzy atrybuty klucza. Pierwszy atrybut jest, że drzewa składni przechowywać wszystkie informacje o źródle w pełnej rozdzielczości. Oznacza to, że drzewa składni zawiera każdą informacji zamieszczonych w tekst źródłowy, co gramatyczne konstrukcja co leksykalne token i wszystkie inne w między, w tym biały znak, komentarze i dyrektywy preprocesora. Na przykład każdy literał wymienionych w źródle jest reprezentowany dokładnie tak, jak została zapisana. Gdy program jest niekompletna lub nieprawidłowo sformułowany przez reprezentujący pominięto lub brak tokenów w drzewie składni drzewa składni także reprezentować błędów w kodzie źródłowym.  

Dzięki temu drugi atrybut drzewa składni. Drzewo składni uzyskane z analizatora może wygenerować dokładne tekst, który został zanalizowany z. Z poziomu każdego węzła składni jest możliwość uzyskania Reprezentacja tekstowa typu poddrzewa początek w tym węźle. Oznacza to, że drzewa składni mogą być używane jako sposobu konstruowania i edytować tekst źródłowy. Tworząc drzewa posiadanego co za tym idzie utworzone równoważne tekstu i edytując drzewo składni, co nowego drzew zmiany poza do istniejącego drzewa, należy skutecznie edytować tekst. 

Trzeci atrybutu drzewa składni te są niezmienne i bezpieczne wątkowo.  Oznacza to, że po uzyskaniu drzewa jest migawką bieżącego stanu kodu i nie ulega zmianie. Dzięki temu wielu użytkownikom na interakcję z tym samym drzewie składni w tym samym czasie w różnych wątkach bez blokowania lub dublowania. Ponieważ drzewa są niezmienne i żadne zmiany nie jest możliwe bezpośrednio do drzewa, metodami factory pomóc tworzyć i modyfikować drzewa składni przez tworzenie migawek dodatkowe drzewa. Drzewa są wydajne w sposób ich ponowne użycie węzłów podrzędnych, nowa wersja może zostać również przebudowany szybko i z niewielkim dodatkową pamięć.

Drzewo składni jest dosłownie drzewa strukturą danych, gdy inny niż końcowy elementy nadrzędne inne elementy. Każdy drzewa składni składa się z węzłów, tokeny i elementy towarzyszące składni.  

## <a name="syntax-nodes"></a>Składnia węzłów

Składnia węzły są jednym z podstawowe elementy drzewa składni. Te węzły reprezentują konstrukcje składni takich jak deklaracje, instrukcje klauzule i wyrażenia. Każda kategoria węzłów składni jest reprezentowana przez oddzielne klasy pochodzącej od <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Zestaw klas węzeł nie jest rozszerzony. 

Wszystkie węzły składni jest inny niż końcowy węzłów w drzewie składni, co oznacza, że mają one zawsze innych węzłów i tokenów jako elementy podrzędne. Jako element podrzędny innego węzła, każdy węzeł ma węzła nadrzędnego, który jest możliwy za pośrednictwem <xref:Microsoft.CodeAnalysis.SyntaxNode.Parent?displayProperty=nameWithType> właściwości. Ponieważ węzły i drzew są niezmienne, nadrzędnego węzła nigdy nie zmienia się. Korzeń drzewa ma element nadrzędny wartości null.  

Każdy węzeł ma <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes?displayProperty=nameWithType> metodę, która zwraca listę węzłów podrzędnych w kolejności sekwencyjnej, na podstawie ich położenia w tekście źródła. Ta lista nie zawiera tokenów. Każdy węzeł ma również metody do sprawdzenia elementów podrzędnych, takich jak <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTokens%2A>, lub <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantTrivia%2A> -reprezentujące listę wszystkich węzłów, tokeny lub elementy towarzyszące składni, który istnieje w poddrzewie odblokowany dostęp do tego węzła.  

Ponadto te same elementy podrzędne za pośrednictwem właściwości jednoznacznie przedstawia każdego podklasy węzeł składni. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa węzła ma trzy dodatkowe właściwości specyficzne dla operatorów binarnych: <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right>. Typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left> i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ExpressionSyntax>, a typ <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken> jest <xref:Microsoft.CodeAnalysis.SyntaxToken>.

Niektóre węzły składni mają opcjonalne elementy podrzędne. Na przykład <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IfStatementSyntax> ma opcjonalny <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ElseClauseSyntax>. Jeśli nie ma elementu podrzędnego, właściwość zwraca wartość null. 

## <a name="syntax-tokens"></a>Tokeny składni

Składnia tokeny są terminali gramatyki języka, reprezentująca najmniejszą składni fragmentów kodu. Nigdy nie są one nadrzędnych innych węzłów lub tokenów. Tokeny składni składają się z słów kluczowych, identyfikatory, literały i znaków interpunkcyjnych. 

Ze względów wydajności <xref:Microsoft.CodeAnalysis.SyntaxToken> typem jest typ wartości CLR. W związku z tym w przeciwieństwie do węzłów składni istnieje tylko jeden struktury dla wszystkich rodzajów tokenów z różnymi właściwości, które mają znaczenie w zależności od rodzaju token, który jest reprezentowanego.

Na przykład token literału liczby całkowitej reprezentuje wartość numeryczną. Oprócz tekst źródłowy raw obejmuje tokenu, token literału ma <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> właściwości, które pozwalają określić dokładnie zdekodować wartości całkowitej. Ta właściwość jest typu <xref:System.Object> ponieważ może to być jeden z wielu typów pierwotnych.

<xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> Właściwości informuje te same informacje co <xref:Microsoft.CodeAnalysis.SyntaxToken.Value> właściwości; jednak ta właściwość jest zawsze typu jako <xref:System.String>. Identyfikator w C# tekst źródłowy może zawierać znaki specjalne Unicode, ale składni sekwencji unikowej sam nie jest uznawany za część nazwy identyfikatora. Tak, chociaż nieprzetworzony tekst objęte token zawiera sekwencji unikowej <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> nie obsługuje właściwości. Zamiast tego zawiera znaków Unicode, identyfikowane przez ucieczki. Na przykład, jeśli tekst źródłowy zawiera identyfikator zapisywane jako `\u03C0`, a następnie <xref:Microsoft.CodeAnalysis.SyntaxToken.ValueText> zwróci właściwości dla tego tokena `π`.

## <a name="syntax-trivia"></a>Elementy towarzyszące składni składni

Elementy towarzyszące składni składni reprezentują części tekstu źródłowego, które przede wszystkim nieważny do normalnej wiedzę na temat kodu, na przykład biały znak, komentarze i dyrektywy preprocesora. Podobnie jak tokeny składni elementy towarzyszące składni są typów wartości. Pojedynczy <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> typ jest używany do opisania wszystkich rodzajów elementy towarzyszące składni.

Ponieważ elementy towarzyszące składni nie są częścią składni języka normalne i może występować w dowolnym miejscu między dwoma tokenów, ich nie znajdują się w drzewie składni jako element podrzędny węzła. Jeszcze ponieważ są one ważne podczas wykonywania funkcji, takich jak refaktoryzacji i obsługa pełnej rozdzielczości na tekst źródłowy, są dostępne jako część drzewa składni.

Elementy towarzyszące składni można uzyskać dostęp, sprawdzając token <xref:Microsoft.CodeAnalysis.SyntaxToken.LeadingTrivia?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.SyntaxToken.TrailingTrivia?displayProperty=nameWithType> kolekcji. Gdy zostanie przeanalizowany tekst źródłowy, sekwencje elementy towarzyszące składni są skojarzone z tokenów. Ogólnie rzecz biorąc token jest właścicielem wszystkie elementy towarzyszące składni po nim w tym samym wierszu do następnego tokenu. Wszystkie elementy towarzyszące składni po tym wierszu jest skojarzony z następującego tokenu. Pierwszym tokenie w pliku źródłowym pobiera wszystkie początkowej elementy towarzyszące składni i przyczepiana jest ostatnią sekwencję elementy towarzyszące składni w pliku na token końca pliku, które w przeciwnym razie ma zerowej szerokości.

W przeciwieństwie do węzłów składni i tokeny składni elementy towarzyszące składni nie mają elementów nadrzędnych. Jeszcze, ponieważ są one częścią drzewa, a każdy jest skojarzony z jednym token, użytkownik może uzyskać dostępu do tokenu nie jest skojarzona z przy użyciu <xref:Microsoft.CodeAnalysis.SyntaxTrivia.Token?displayProperty=nameWithType> właściwości.

## <a name="spans"></a>Zakresy

Wszystkie węzły, token i elementy towarzyszące składni wie jej położenie w obrębie tekst źródłowy i liczbę znaków, który składa się z. Położenie tekstu jest reprezentowany jako liczba całkowita 32-bitowy, który jest liczony od zera `char` indeksu. A <xref:Microsoft.CodeAnalysis.Text.TextSpan> obiekt jest położenie początku i liczbę znaków, zarówno prezentowane w postaci liczb całkowitych. Jeśli <xref:Microsoft.CodeAnalysis.Text.TextSpan> ma zerową długość, odnosi się do lokalizacji między znakami.

Każdy węzeł ma dwa <xref:Microsoft.CodeAnalysis.Text.TextSpan> właściwości: <xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> i <xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*>. 

<xref:Microsoft.CodeAnalysis.SyntaxNode.Span*> Właściwość jest zakres tekstu od początku pierwszym tokenie w poddrzewie węzła na końcu ostatniego tokena. Ten zakres nie obejmuje żadnych wiodących lub końcowych elementy towarzyszące składni.

<xref:Microsoft.CodeAnalysis.SyntaxNode.FullSpan*> Właściwość jest zakres tekstu, zawierający zakres normalnej węzła, a także zakres dowolnego wiodących lub końcowych elementy towarzyszące składni.

Na przykład: 

``` csharp
      if (x > 3)
      {
||        // this is bad
          |throw new Exception("Not right.");|  // better exception?||
      }
```

Węzeł instrukcji wewnątrz bloku ma należy do zakresu wskazanej przez pojedynczy pionowych słupków (|). Zawiera on znaki `throw new Exception("Not right.");`. Pełny zakres jest określane przez dwa razy pionowych słupków (|). Zawiera te same znaki jako zakres i skojarzone z elementy towarzyszące składni wiodące i końcowe znaki.

## <a name="kinds"></a>Typy

Każdy węzeł, token lub elementy towarzyszące składni ma <xref:Microsoft.CodeAnalysis.SyntaxNode.RawKind?displayProperty=nameWithType> właściwość typu <xref:System.Int32?displayProperty=nameWithType>, który identyfikuje element dokładna składnia reprezentowany. Ta wartość mogą być rzutowane na wyliczenie specyficzny dla języka; każdego języka C# i VB, ma jeden `SyntaxKind` — wyliczenie (<xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind?displayProperty=nameWithType> i <xref:Microsoft.CodeAnalysis.VisualBasic.SyntaxKind?displayProperty=nameWithType>odpowiednio) która wyświetla listę wszystkich możliwych węzłów, tokeny i elementy towarzyszące składni elementów, w gramatyce. Ta konwersja może odbywać się automatycznie po zalogowaniu się do <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*?displayProperty=nameWithType> lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicExtensions.Kind*?displayProperty=nameWithType> metody rozszerzenia.

<xref:Microsoft.CodeAnalysis.SyntaxToken.RawKind> Właściwości umożliwia łatwe ujednoznacznienia składni węzeł typów, które korzystać z tej samej klasy węzła. Tokeny i elementy towarzyszące składni ta właściwość jest jedynym sposobem, aby odróżnić jeden typ elementu z innej. 

Na przykład, jeden <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax> klasa ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Left>, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.OperatorToken>, i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.BinaryExpressionSyntax.Right> jako elementy podrzędne. <xref:Microsoft.CodeAnalysis.CSharp.CSharpExtensions.Kind*> Właściwości odróżnia czy jest <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.AddExpression>, <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SubtractExpression>, lub <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.MultiplyExpression> rodzaj węzła składni.

## <a name="errors"></a>błędy

Nawet wtedy, gdy tekst źródłowy zawiera błędy składni, drzewa pełnej składni, który jest round-wysyłanych i zwracanych jest ze źródłem jest widoczne. Gdy analizator napotka kod, który jest niezgodny ze zdefiniowanym składni języka, użyto jednego z dwóch metod można utworzyć drzewa składni.

Najpierw jeśli analizator oczekuje określonego rodzaju token, ale nie zostanie znaleziona, jego może wstawić Brak tokenu do drzewa składni w lokalizacji oczekiwany token. Brak tokenu reprezentuje rzeczywisty tokenu, który był oczekiwany, ale ma pusty zakres, a jego <xref:Microsoft.CodeAnalysis.SyntaxNode.IsMissing?displayProperty=nameWithType> zwraca właściwość `true`.

Po drugie analizator pominąć tokeny aż do znalezienia punktu, gdzie można kontynuować, analizowanie. W takim przypadku pominięto tokeny są dołączone jako węzeł elementy towarzyszące składni o rodzaju <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.SkippedTokensTrivia>.
