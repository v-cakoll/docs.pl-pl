---
title: Rozpoczynanie pracy z usługą analiza semantyki
description: Ten samouczek zawiera omówienie pracy z semantycznego analizy przy użyciu zestawu .NET SDK kompilatora.
ms.date: 02/06/2018
ms.custom: mvc
ms.openlocfilehash: 4b021ed2a27da754e2ac5af01716868e41e72738
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484621"
---
# <a name="get-started-with-semantic-analysis"></a>Rozpoczynanie pracy z usługą analiza semantyki

W tym samouczku przyjęto założenie, że znasz składnię interfejsu API. [Rozpoczynanie pracy z usługą analiza składni](syntax-analysis.md) artykuł zawiera wprowadzenie wystarczające.

W ramach tego samouczka, możesz zapoznać się z **Symbol** i **powiązanie interfejsów API**. Te interfejsy API, podaj informacje o _znaczenia semantycznego_ programu. Umożliwiają one pytania i odpowiedzi na pytania dotyczące typów reprezentowanych przez dowolny symbol w programie.

Należy zainstalować **zestawu SDK platformy kompilatora .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-compilations-and-symbols"></a>Opis kompilacji i symboli

Więcej pracy przy użyciu zestawu .NET SDK kompilatora zapoznanie się ze różnice między API składni i semantyczne interfejsu API. **API składni** pozwala przyjrzeć się _struktury_ programu. Jednak często potrzebują więcej informacji na temat semantykę lub _znaczenie_ programu. Gdy plik luźne kodu lub fragment kodu w języku VB lub C# mogą być syntaktycznie analizowane w izolacji, nie ma sensu zadawać pytania, takie jak "co to jest typ zmiennej" w odkurzający. Znaczenie Nazwa typu, który może być zależny od odwołania do zestawów, importowanej przestrzeni nazw lub innych plików kodu. Te odpowiedzi na pytania za pomocą **semantycznego API**, konkretnie <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> klasy.

Wystąpienie <xref:Microsoft.CodeAnalysis.Compilation> jest porównywalna do pojedynczego projektu widziany przez kompilator i reprezentuje wszystkie elementy potrzebne do kompilowania programów Visual Basic lub C#. **Kompilacji** zawiera zestaw plików źródłowych do skompilowania, odwołania do zestawów i opcje kompilatora. Można przyczyny, informacje o znaczeniu kod przy użyciu wszystkie pozostałe informacje w tym kontekście. A <xref:Microsoft.CodeAnalysis.Compilation> umożliwia znalezienie **symbole** -jednostki, takie jak typy, przestrzenie nazw, składowych i zmiennych, które nazwy i inne wyrażenia odnoszą się do. Proces przypisywania nazw oraz wyrażenia z **symbole** nosi nazwę **powiązanie**.

Podobnie jak <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> jest specyficzny dla języka pochodne klasy abstrakcyjnej. Podczas tworzenia wystąpienia obiektu kompilacji, należy wywołać metodę fabryki na <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) klasy.

## <a name="querying-symbols"></a>Tworzenie zapytań symboli

W tym samouczku przyjrzymy się programu "Hello World" ponownie. Tym razem zapytania symbole w programie, aby zrozumieć, jakie typy reprezentują te symbole. Zapytanie dla typów w przestrzeni nazw i Dowiedz się, jak znaleźć dostępnych metod w danym typie.

Zostanie wyświetlony gotowy kod dla tego przykładu w [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy drzewo składni umożliwiają dziedziczenia opisano różne elementy składni, które są prawidłowe w różnych lokalizacjach w programie. Za pomocą tych interfejsów API często oznacza, że właściwości rzutowania lub elementy członkowskie kolekcji dla określonych typów pochodnych. W poniższych przykładach przydziałów i rzutowania są osobnych instrukcji, za pomocą jawnie wpisanych zmiennych. Może odczytywać kod, aby zobaczyć typów zwracanych interfejsu API i typ środowiska uruchomieniowego zwracanych obiektów. W praktyce jest bardziej powszechne, aby używać niejawnie wpisane zmienne i zależą od nazwy interfejsu API do opisu typów obiektów sprawdzane.

Utwórz nowy język C# **narzędzie do analizy kodu autonomicznego** projektu:

* W programie Visual Studio, wybierz **pliku** > **New** > **projektu** Aby wyświetlić okno dialogowe Nowy projekt.
* W obszarze **Visual C#** > **rozszerzalności**, wybierz **narzędzie do analizy kodu autonomicznego**.
* Nazwij swój projekt "**SemanticQuickStart**" i kliknij przycisk OK.

Możesz zacząć analizować podstawowe "Hello World!" Program przedstawionej wcześniej.
Dodaj tekst programu Witaj świecie jako stała w swojej `Program` klasy:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod do drzewa składni tekstu kodu w kompilacji `programText` stałej.  Dodaj następujący wiersz do Twojej `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Następnie kompilacji <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> z drzewa już utworzony. Zależy od przykładu "Hello World" <xref:System.String> i <xref:System.Console> typów. Należy odwoływać się do zestawu, który deklaruje tych dwóch typów w kompilacji. Dodaj następujący wiersz do Twojej `Main` metodę, aby utworzyć zbiór drzewo składni, w tym odwołanie do zestawu, odpowiednie:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda dodaje odwołania do kompilacji. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile%2A?displayProperty=nameWithType> Metoda ładuje zestaw jako odwołanie. 

## <a name="querying-the-semantic-model"></a>Zapytania semantycznego modelu analizy biznesowej

Po utworzeniu <xref:Microsoft.CodeAnalysis.Compilation> możesz poprosić go dla <xref:Microsoft.CodeAnalysis.SemanticModel> dla każdego <xref:Microsoft.CodeAnalysis.SyntaxTree> zawarte w tym <xref:Microsoft.CodeAnalysis.Compilation>. Model semantyczny można traktować jako źródło dla wszystkich informacji, które normalnie otrzymamy od funkcji intellisense. Element <xref:Microsoft.CodeAnalysis.SemanticModel> może odpowiedzieć na pytania "Co nazw znajdują się w zakresie, w tym miejscu?", "jakie elementy członkowskie są dostępne z tej metody?", "jakie zmienne są używane w tym bloku tekstu?" i "Co to nazwa/wyrażenie odwołuje się do?" Dodaj ten instrukcję, aby utworzyć model semantyczny:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Nazwa powiązania

<xref:Microsoft.CodeAnalysis.Compilation> Tworzy <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po utworzeniu modelu, można je w celu znalezienia pierwszego zapytania `using` dyrektywy i pobieranie informacji o symbolach dla `System` przestrzeni nazw. Dodaj następujące dwa wiersze do Twojej `Main` metodę, aby utworzyć model semantyczny i pobrać symboli dla pierwszego instrukcję using:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Poprzedni kod pokazuje jak powiązać nazwę w pierwszym `using` dyrektywy do pobrania <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> dla `System` przestrzeni nazw. Powyższy kod ilustruje także użycie **składnia model** można znaleźć struktury kodu; możesz użyć **semantycznego modelu analizy biznesowej** zrozumienie jego znaczenie. **Składnia model** odnajduje ciąg `System` za pomocą instrukcji. **Semantycznego modelu analizy biznesowej** zawiera wszystkie informacje dotyczące typów zdefiniowanych w `System` przestrzeni nazw.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> obiektu można uzyskać <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> przy użyciu <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> właściwości. Ta właściwość zwraca symbol, którego to wyrażenie odwołuje się. W wyrażeniach, które nie odwołuje się do obiektów (np. literały numeryczne) tej właściwości jest `null`. Gdy <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> nie ma wartości null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> wskazuje typ symbolu. W tym przykładzie <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> właściwość <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Dodaj następujący kod, aby Twoje `Main` metody. Pobiera symbol `System` przestrzeni nazw, a następnie wyświetla wszystkie podrzędne przestrzenie nazw zadeklarowanych w `System` przestrzeni nazw:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Uruchom program i powinien zostać wyświetlony następujący komunikat:

```
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
> Dane wyjściowe będą zawierać każdej przestrzeni nazw, który jest podrzędna przestrzeń nazw z `System` przestrzeni nazw. Wyświetla każdej przestrzeni nazw, który znajduje się w tej kompilacji, który odwołuje się tylko do zestawu gdzie `System.String` jest zadeklarowana. Wszystkie przestrzenie nazw zadeklarowanych w innych zestawach nie są znane w tej kompilacji

### <a name="binding-an-expression"></a>Powiązanie wyrażenia

Poprzedni kod pokazuje, jak znaleźć symboli przez powiązanie z nazwą. Istnieją inne wyrażenia w programie C#, która może być powiązana, których nie ma nazwy. Aby zademonstrować tę możliwość, umożliwia dostęp do powiązania do prostych literału ciągu.

Program "Hello World" zawiera <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" ciąg wyświetlany w konsoli.

Znajdź "Hello, World!" ciąg, umieszczając pojedynczy ciąg literału w programie. Następnie po zlokalizowaniu węzeł składni, uzyskać informacje dotyczące typu dla tego węzła z modelu semantycznego. Dodaj następujący kod, aby Twoje `Main` metody:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Struktura zawiera <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> właściwość, która umożliwia dostęp do informacji semantycznych o typie literału. W tym przykładzie to `string` typu. Dodaj deklarację, że ta właściwość umożliwia przypisanie do zmiennej lokalnej:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Aby ukończyć ten samouczek, utworzymy kwerenda LINQ, która tworzy sekwencję wszystkich metod publicznych zadeklarowanych w `string` wpisz zwracające `string`. To zapytanie pobiera złożony, więc ją skompilować wiersz po wierszu, odtworzyć go jako pojedynczego zapytania. Źródło dla tego zapytania jest sekwencja wszystkich elementów członkowskich zadeklarowanych w `string` typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Tego źródła sekwencja zawiera wszystkie elementy członkowskie, w tym jej właściwości i pola, więc filtrować za pomocą <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> metodę, aby znaleźć elementy, które są <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> obiektów:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Następnie dodaj inny filtr, aby zwrócić tylko tych metod, które są publiczne ale zwracane `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Wybierz tylko właściwości name i tylko unikatowych nazw, usuwając wszystkie przeciążenia:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Możesz również tworzyć pełne zapytanie przy użyciu składni zapytań LINQ i następnie wyświetlić nazwy metody, w konsoli:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/Program.cs#13 "Build and display the results of the query.")]

Skompiluj i uruchom program. Powinny zostać wyświetlone następujące dane wyjściowe:

```
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
Semantyczne interfejsu API został użyty do znalezienia i wyświetlać informacje na temat symboli, które są dostępne w ramach tego programu.
