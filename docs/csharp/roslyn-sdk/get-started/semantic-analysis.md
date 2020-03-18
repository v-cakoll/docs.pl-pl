---
title: Wprowadzenie do analizy semantycznej
description: Ten samouczek zawiera omówienie pracy z analizą semantyczną przy użyciu zestawu SDK kompilatora .NET.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: a6dcaeeb86acb5c0e1602f01dc5952ffd9d5e3f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240513"
---
# <a name="get-started-with-semantic-analysis"></a>Wprowadzenie do analizy semantycznej

W tym samouczku przyjęto założenie, że znasz interfejs API składni. Wprowadzenie [do analizy składni](syntax-analysis.md) artykuł zawiera wystarczające wprowadzenie.

W tym samouczku można zapoznać **się z symboli** **i powiązań interfejsów API**. Te interfejsy API zawierają informacje o _znaczeniu semantycznym_ programu. Umożliwiają one zadawanie pytań i odpowiadanie na pytania dotyczące typów reprezentowanych przez dowolny symbol w programie.

Musisz zainstalować zestaw **SDK platformy kompilatora .NET:**

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Opis kompilacji i symboli

Podczas pracy z zestawem SDK kompilatora .NET zapoznaj się z rozróżnieniem między interfejsem API składni a interfejsem API semantycznego. **Interfejs API składni** umożliwia przyjrzenie się _strukturze_ programu. Jednak często chcesz bogatsze informacje o semantyce lub _znaczeniu_ programu. Podczas gdy plik kodu luźnego lub fragment kodu języka Visual Basic lub C# może być analizowany syntaktycznie w izolacji, nie ma sensu zadawać pytań, takich jak "jaki jest typ tej zmiennej" w próżni. Znaczenie nazwy typu może być zależne od odwołań do zestawu, importu obszaru nazw lub innych plików kodu. Odpowiedzi na te pytania są udzielane przy użyciu <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> **interfejsu API semantycznego,** w szczególności klasy.

Wystąpienie <xref:Microsoft.CodeAnalysis.Compilation> jest analogiczne do pojedynczego projektu, jak widać przez kompilator i reprezentuje wszystko, co potrzebne do skompilowania programu Visual Basic lub C#. **Kompilacja** zawiera zestaw plików źródłowych do skompilowania, odwołania do zestawu i opcje kompilatora. Można powód o znaczeniu kodu przy użyciu wszystkich innych informacji w tym kontekście. A <xref:Microsoft.CodeAnalysis.Compilation> umożliwia **znajdowanie symboli** — jednostek, takich jak typy, przestrzenie nazw, elementy członkowskie i zmienne, do których odnoszą się nazwy i inne wyrażenia. Proces kojarzenia nazw i wyrażeń z **symbolami** nosi nazwę **Binding**.

Like <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.Compilation> , jest klasą abstrakcyjną z pochodnymi specyficznymi dla języka. Podczas tworzenia wystąpienia kompilacji, należy wywołać metodę <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> fabryki <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>na (lub ) klasy.

## <a name="querying-symbols"></a>Wykonywanie zapytań dotyczących symboli

W tym samouczku ponownie spojrzysz na program "Hello World". Tym razem kwerendy symbole w programie, aby zrozumieć, jakie typy te symbole reprezentują. Kwerenda dla typów w przestrzeni nazw i dowiedzieć się, aby znaleźć metody dostępne dla typu.

Gotowy kod dla tego przykładu można zobaczyć w [naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy Drzewa składni używają dziedziczenia do opisywania różnych elementów składni, które są prawidłowe w różnych lokalizacjach w programie. Korzystanie z tych interfejsów API często oznacza właściwości rzutowania lub członków kolekcji do określonych typów pochodnych. W poniższych przykładach przypisania i rzutowania są oddzielne instrukcje, przy użyciu jawnie wpisane zmienne. Można odczytać kod, aby zobaczyć typy zwracane interfejsu API i typu wykonywania zwróconych obiektów. W praktyce jest bardziej powszechne do używania niejawnie wpisane zmienne i polegać na nazwy interfejsu API do opisania typu obiektów badane.

Utwórz nowy projekt narzędzia do **analizy kodu autonomicznego** języka C#:

* W programie Visual Studio wybierz pozycję **Plik** > **nowy** > **projekt,** aby wyświetlić okno dialogowe Nowy projekt.
* W obszarze**Rozszerzalność** **języka Visual C#** > wybierz pozycję **Autonomiczne narzędzie do analizy kodu**.
* Nazwij swój projekt "**SemanticQuickStart**" i kliknij przycisk OK.

Będziesz analizować podstawowe "Hello World!" program pokazany wcześniej.
Dodaj tekst programu Hello World jako stałą w swojej `Program` klasie:

[!code-csharp[Declare the program test](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod, aby utworzyć drzewo składni `programText` dla tekstu kodu w stałej.  Dodaj następujący wiersz `Main` do metody:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Następnie zbuduj <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> z drzewa, które zostały już utworzone. "Hello World" próbki opiera <xref:System.String> <xref:System.Console> się na i typów. Należy odwołać się do zestawu, który deklaruje te dwa typy w kompilacji. Dodaj następujący wiersz `Main` do metody, aby utworzyć kompilację drzewa składni, w tym odwołanie do odpowiedniego zestawu:

[!code-csharp[Create the compilation](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

Metoda <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> dodaje odwołania do kompilacji. Metoda <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> ładuje zespół jako odniesienie.

## <a name="querying-the-semantic-model"></a>Wykonywanie zapytań dotyczących modelu semantycznego

Gdy masz <xref:Microsoft.CodeAnalysis.Compilation> można poprosić o <xref:Microsoft.CodeAnalysis.SemanticModel> for <xref:Microsoft.CodeAnalysis.SyntaxTree> any zawarte <xref:Microsoft.CodeAnalysis.Compilation>w tym . Można myśleć o modelu semantycznym jako źródło wszystkich informacji, które normalnie można uzyskać z intellisense. A <xref:Microsoft.CodeAnalysis.SemanticModel> może odpowiadać na pytania takie jak "Jakie nazwy mają miejsce w tej lokalizacji?", "Jakie elementy członkowskie są dostępne z tej metody?", "Jakie zmienne są używane w tym bloku tekstu?" i "Do czego odnosi się ta nazwa/wyrażenie?" Dodaj tę instrukcję, aby utworzyć model semantyczny:

[!code-csharp[Create the semantic model](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Powiązanie nazwy

Tworzy <xref:Microsoft.CodeAnalysis.Compilation> z <xref:Microsoft.CodeAnalysis.SemanticModel> . <xref:Microsoft.CodeAnalysis.SyntaxTree> Po utworzeniu modelu można zbadać go, aby znaleźć pierwszą `using` `System` dyrektywę i pobrać informacje o symbolu obszaru nazw. Dodaj te dwa `Main` wiersze do metody, aby utworzyć model semantyczny i pobrać symbol dla pierwszego using instrukcji:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Poprzedni kod pokazuje, jak powiązać nazwę `using` w pierwszej dyrektywie, aby pobrać <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> dla obszaru `System` nazw. Poprzedni kod ilustruje również, że za pomocą **modelu składni,** aby znaleźć strukturę kodu; używasz **modelu semantycznego,** aby zrozumieć jego znaczenie. **Model składni** znajdzie `System` ciąg w using instrukcji. **Model semantyczny** ma wszystkie informacje o typach `System` zdefiniowanych w przestrzeni nazw.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> obiektu można uzyskać <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> przy <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> użyciu właściwości. Ta właściwość zwraca symbol, do który odwołuje się to wyrażenie. W przypadku wyrażeń, które nie odwołują się `null`do niczego (np. literały liczbowe), ta właściwość jest . Gdy <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> nie ma wartości <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> null, oznacza typ symbolu. W tym przykładzie <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> właściwość <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>jest . Dodaj następujący kod `Main` do metody. Pobiera symbol obszaru nazw, `System` a następnie wyświetla wszystkie podrzędne `System` przestrzenie nazw zadeklarowane w obszarze nazw:

[!code-csharp[Display all the child namespaces](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Uruchom program i powinieneś zobaczyć następujące dane wyjściowe:

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
> Dane wyjściowe nie obejmują każdego obszaru nazw, który `System` jest podrzędnym obszarem nazw obszaru nazw. Wyświetla każdy obszar nazw, który jest obecny w tej `System.String` kompilacji, która odwołuje się tylko do zestawu, gdzie jest zadeklarowany. Wszystkie przestrzenie nazw zadeklarowane w innych zestawach nie są znane tej kompilacji

### <a name="binding-an-expression"></a>Powiązanie wyrażenia

Poprzedni kod pokazuje, jak znaleźć symbol przez powiązanie z nazwą. Istnieją inne wyrażenia w programie C#, które mogą być powiązane, które nie są nazwy. Aby zademonstrować tę możliwość, przejdźmy do powiązania z literałem prostego ciągu.

Program "Hello World" <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>zawiera program "Hello, World!" ciąg wyświetlany na konsoli.

Znajdziesz "Cześć, Świat!" przez zlokalizowanie pojedynczego ciągu literał w programie. Następnie po zlokalizowaniu węzła składni pobierz informacje o typie tego węzła z modelu semantycznego. Dodaj następujący kod `Main` do metody:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

Struktura <xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> zawiera <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> właściwość, która umożliwia dostęp do informacji semantycznych o typie literału. W tym przykładzie jest `string` to typ. Dodaj deklarację, która przypisuje tę właściwość do zmiennej lokalnej:

[!code-csharp[Find the semantic information about the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Aby zakończyć ten samouczek, skompilujmy kwerendę LINQ, która `string` tworzy sekwencję wszystkich metod publicznych zadeklarowanych na typie, który zwraca plik `string`. Ta kwerenda staje się złożona, więc skompilujmy je wiersz po wierszu, a następnie zrekonstruujmy jako pojedynczą kwerendę. Źródłem tej kwerendy jest sekwencja wszystkich `string` elementów członkowskich zadeklarowanych na typie:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Ta sekwencja źródłowa zawiera wszystkie elementy członkowskie, <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> w tym właściwości <xref:Microsoft.CodeAnalysis.IMethodSymbol?displayProperty=nameWithType> i pola, więc przefiltruj ją za pomocą metody, aby znaleźć elementy, które są obiektami:

[!code-csharp[Filter the sequence to only methods](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Następnie dodaj inny filtr, aby zwrócić tylko te `string`metody, które są publiczne i zwracają:

[!code-csharp[Filter on return type and accessibility](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Zaznacz tylko właściwość name i tylko różne nazwy, usuwając wszelkie przeciążenia:

[!code-csharp[find the distinct names.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Można również utworzyć pełną kwerendę przy użyciu składni kwerendy LINQ, a następnie wyświetlić wszystkie nazwy metod w konsoli:

[!code-csharp[build and display the results of this query.](../../../../samples/snippets/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

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

Interfejs API semantycznego służy do znajdowania i wyświetlania informacji o symbolach, które są częścią tego programu.
