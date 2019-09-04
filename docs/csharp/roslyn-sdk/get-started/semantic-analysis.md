---
title: Wprowadzenie do analizy semantycznej
description: Ten samouczek zawiera omówienie pracy z analizą semantyczną przy użyciu zestawu SDK kompilatora platformy .NET.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 80a814054ab95a5b6585289e8580a725b18ca44e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252935"
---
# <a name="get-started-with-semantic-analysis"></a>Wprowadzenie do analizy semantycznej

W tym samouczku założono, że znasz interfejs API składni. Artykuł Wprowadzenie [do analizy składni](syntax-analysis.md) zawiera wystarczające wprowadzenie.

W tym samouczku przedstawiono interfejsy API **symboli** i **powiązań**. Te interfejsy API zawierają informacje o _semantycznym znaczeniu_ programu. Umożliwiają one zadawanie pytań i odpowiedzi na pytania dotyczące typów reprezentowanych przez dowolny symbol w programie.

Musisz zainstalować **zestaw SDK .NET compiler platform**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Informacje o kompilacjach i symbolach

Podczas pracy z zestawem SDK kompilatora .NET można zapoznać się z różnicami między interfejsem API składni i semantycznym interfejsem API. **Interfejs API składni** umożliwia przeglądanie _struktury_ programu. Jednak często potrzebujesz bardziej szczegółowych informacji na temat semantyki lub _znaczenia_ programu. Chociaż luźny plik kodu lub fragment kodu VB lub C# kod może być syntaktycznie analizowany w izolacji, nie ma znaczenia, aby zadawać pytania, takie jak "jaki jest typ tej zmiennej" w próżni. Znaczenie nazwy typu może być zależne od odwołań do zestawów, importowanych przestrzeni nazw lub innych plików kodu. Odpowiedzi na te pytania są udzielane przy użyciu **semantyki interfejsu API**, a w odróżnieniu od <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> klasy.

Wystąpienie <xref:Microsoft.CodeAnalysis.Compilation> jest analogiczne do pojedynczego projektu, który jest widoczny dla kompilatora i reprezentuje wszystko, co jest potrzebne do skompilowania C# Visual Basic lub programu. **Kompilacja** obejmuje zestaw plików źródłowych do skompilowania, odwołań do zestawów i opcji kompilatora. Możesz przyczynić się do znaczenia kodu przy użyciu wszystkich innych informacji w tym kontekście. A <xref:Microsoft.CodeAnalysis.Compilation> umożliwia znalezienie **symboli** — jednostek takich jak typy, przestrzenie nazw, elementy członkowskie i zmienne, do których odwołują się nazwy i inne wyrażenia. Proces kojarzenia nazw i wyrażeń z **symbolami** nazywa się **wiązaniem**.

Podobnie <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>jak <xref:Microsoft.CodeAnalysis.Compilation> , jest klasą abstrakcyjną z pochodnymi specyficznymi dla języka. Podczas tworzenia wystąpienia kompilacji należy wywołać metodę fabryki dla <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> klasy (lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>).

## <a name="querying-symbols"></a>Wykonywanie zapytań względem symboli

W tym samouczku ponownie przyjrzyjsz programowi "Hello world". Tym razem można zbadać symbole w programie, aby zrozumieć, jakie typy reprezentują te symbole. Kwerenda dotycząca typów w przestrzeni nazw i Dowiedz się, jak znaleźć metody dostępne dla danego typu.

Gotowy kod dla tego przykładu można zobaczyć w [naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy drzewa składni używają dziedziczenia do opisywania różnych elementów składni, które są prawidłowe w różnych lokalizacjach w programie. Użycie tych interfejsów API często oznacza rzutowanie właściwości lub członków kolekcji na określone typy pochodne. W poniższych przykładach przypisanie i rzutowania są oddzielnymi instrukcjami przy użyciu jawnie wpisanych zmiennych. Kod można odczytać, aby wyświetlić typy zwracane przez interfejs API i typ środowiska uruchomieniowego zwracanych obiektów. W rzeczywistości jest to bardziej powszechne użycie niejawnie wpisanych zmiennych i poleganie na nazwach interfejsów API do opisywania typu badanych obiektów.

Utwórz nowy C# projekt **Narzędzia do analizy kodu autonomicznego** :

* W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt** , aby wyświetlić okno dialogowe Nowy projekt.
*  > W obszarze **rozszerzalność** **wizualizacji C#** wybierz opcję **autonomiczne narzędzie do analizy kodu**.
* Nadaj projektowi nazwę "**SemanticQuickStart**" i kliknij przycisk OK.

Zamierzasz analizować podstawową "Hello world!" pokazany wcześniej program.
Dodaj tekst dla programu Hello World jako stałą w swojej `Program` klasie:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie Dodaj następujący kod, aby skompilować drzewo składni dla tekstu kodu w `programText` stałej.  Dodaj następujący wiersz do `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Następnie Skompiluj <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> z poziomu drzewa, które zostało już utworzone. Przykład "Hello World" opiera się <xref:System.String> na typach i. <xref:System.Console> Należy odwołać się do zestawu, który deklaruje te dwa typy w kompilacji. Dodaj następujący wiersz do `Main` metody, aby utworzyć kompilację drzewa składni, łącznie z odwołaniem do odpowiedniego zestawu:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda dodaje odwołania do kompilacji. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Metoda ładuje zestaw jako odwołanie.

## <a name="querying-the-semantic-model"></a>Wykonywanie zapytania dotyczącego modelu semantycznego

Gdy masz <xref:Microsoft.CodeAnalysis.Compilation> <xref:Microsoft.CodeAnalysis.SyntaxTree> , możesz poszukać w <xref:Microsoft.CodeAnalysis.Compilation> odniesieniudodowolnegozawartegownimelementu.<xref:Microsoft.CodeAnalysis.SemanticModel> Model semantyczny można traktować jako źródło wszystkich informacji, które zwykle są uzyskiwane z IntelliSense. <xref:Microsoft.CodeAnalysis.SemanticModel> Może odpowiedzieć na pytania, takie jak "Jakie są nazwy w tym miejscu?", "jakie elementy członkowskie są dostępne w tej metodzie?", "jakie zmienne są używane w tym bloku tekstu?" i "do czego odnosi się ta nazwa/wyrażenie?". Dodaj tę instrukcję, aby utworzyć model semantyczny:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Powiązanie nazwy

<xref:Microsoft.CodeAnalysis.Compilation> Tworzy z.<xref:Microsoft.CodeAnalysis.SemanticModel> <xref:Microsoft.CodeAnalysis.SyntaxTree> Po utworzeniu modelu można wykonać zapytanie w celu znalezienia pierwszej `using` dyrektywy i pobrać informacje o symbolach `System` dla przestrzeni nazw. Dodaj te dwa wiersze do `Main` metody, aby utworzyć semantyczny model i pobrać symbol dla pierwszej instrukcji using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Poprzedni kod pokazuje, jak powiązać nazwę w pierwszej `using` dyrektywie w celu <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> pobrania dla `System` przestrzeni nazw. Powyższy kod również ilustruje użycie **modelu składni** do znajdowania struktury kodu; **model semantyczny** jest używany do zrozumienia jego znaczenia. **Model składni** znajduje ciąg `System` w instrukcji using. **Model semantyczny** ma wszystkie informacje o typach zdefiniowanych w `System` przestrzeni nazw.

Z obiektu można <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> uzyskać za pomocą <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> właściwości. <xref:Microsoft.CodeAnalysis.SymbolInfo> Ta właściwość zwraca symbol, do którego odwołuje się wyrażenie. Dla wyrażeń, które nie odwołują się do żadnych elementów (takich jak literały numeryczne), ta właściwość jest `null`. Gdy wartość nie <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> jest równa null, oznacza typ symbolu. W tym przykładzie <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> Właściwość <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>jest. Dodaj następujący kod do `Main` metody. Pobiera symbol dla `System` przestrzeni nazw, a następnie wyświetla wszystkie podrzędne przestrzenie nazw zadeklarowane `System` w przestrzeni nazw:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Uruchom program i powinien zostać wyświetlony następujący wynik:

```output
System.Collections
System.Configuration
System.Deployment
System.Diagnostics
System.Globalization
System.IO
System.Numerics
System.Reflection
System.Resources
System.Runtime
System.Security
System.StubHelpers
System.Text
System.Threading
Press any key to continue . . .
```

> [!NOTE]
> Dane wyjściowe nie obejmują każdej przestrzeni nazw, która jest podrzędną przestrzenią `System` nazw. Wyświetla on każdą przestrzeń nazw, która jest obecna w tej kompilacji, która odwołuje `System.String` się tylko do zestawu, w którym jest zadeklarowana. Wszystkie przestrzenie nazw zadeklarowane w innych zestawach nie są znane dla tej kompilacji

### <a name="binding-an-expression"></a>Tworzenie powiązania wyrażenia

Poprzedni kod pokazuje, jak znaleźć symbol przez powiązanie z nazwą. W C# programie istnieją inne wyrażenia, które mogą być powiązane, ale nie są nazwami. Aby zademonstrować tę możliwość, przyjrzyjmy się do prostego literału ciągu.

Program "Hello World" zawiera a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" ciąg wyświetlany w konsoli.

Znajdziesz "Hello, World!" ciąg przez znalezienie pojedynczego literału ciągu w programie. Następnie po zlokalizowaniu węzła składni Pobierz informacje o typie dla tego węzła z modelu semantycznego. Dodaj następujący kod do `Main` metody:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura<xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> zawiera właściwość, która umożliwia dostęp do informacji semantycznych o typie literału. W tym przykładzie jest `string` to typ. Dodaj deklarację, która przypisuje tę właściwość do zmiennej lokalnej:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Aby ukończyć ten samouczek, Utwórzmy zapytanie LINQ, które tworzy sekwencję wszystkich metod publicznych zadeklarowanych w `string` typie, który `string`zwraca. To zapytanie jest złożone, więc kompilujemy go, aby skompilować wiersz po wierszu, a następnie odtworzyć go jako pojedyncze zapytanie. Źródłem tego zapytania jest sekwencja wszystkich elementów członkowskich zadeklarowanych w `string` typie:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Ta sekwencja źródłowa zawiera wszystkie elementy członkowskie, w tym właściwości i pola, dlatego należy <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> je odfiltrować za pomocą <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> metody, aby znaleźć elementy, które są obiektami:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Następnie Dodaj inny filtr, aby zwrócić tylko te metody, które są publiczne i zwracają `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Wybierz tylko właściwość Name i tylko unikatowe nazwy, usuwając wszystkie przeciążenia:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Możesz również utworzyć pełne zapytanie przy użyciu składni zapytania LINQ, a następnie wyświetlić wszystkie nazwy metod w konsoli programu:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Skompiluj i uruchom program. Powinny zostać wyświetlone następujące dane wyjściowe:

```output
Join
Substring
Trim
TrimStart
TrimEnd
Normalize
PadLeft
PadRight
ToLower
ToLowerInvariant
ToUpper
ToUpperInvariant
ToString
Insert
Replace
Remove
Format
Copy
Concat
Intern
IsInterned
Press any key to continue . . .
```

Semantyczny interfejs API służy do znajdowania i wyświetlania informacji o symbolach, które są częścią tego programu.
