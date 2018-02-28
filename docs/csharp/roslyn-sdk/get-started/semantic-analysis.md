---
title: Wprowadzenie do analizy semantycznego
description: "Ten samouczek zawiera omówienie pracy z semantyczny analizy przy użyciu zestawu SDK kompilatora .NET."
author: billwagner
ms.author: wiwagn
ms.date: 02/06/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 04bd57dfd32a51bf5d7e3a573e34140b0feec90f
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="get-started-with-semantic-analysis"></a>Wprowadzenie do analizy semantycznego

W tym samouczku założono, że znasz API składni. [Wprowadzenie do analizy składni](syntax-analysis.md) artykuł zawiera wprowadzenie wystarczające.

W tym samouczku Eksploruj **Symbol** i **powiązanie interfejsów API**. Te interfejsy API Podaj informacje o _znaczenie semantyczne_ programu. Umożliwiają one pytania i odpowiedzi na pytania dotyczące typów reprezentowany przez dowolny symbol w programie.

## <a name="understanding-compilations-and-symbols"></a>Opis kompilacje i symboli

Więcej pracy przy użyciu zestawu SDK kompilatora .NET należy zapoznać się z różnice między składni interfejsu API i semantyczne interfejsu API. **API składni** pozwala przyjrzeć się _struktury_ programu. Jednak często mają rozbudowane informacje o semantykę lub _znaczenie_ programu. Gdy plik kodu luźnego lub fragment kodu VB lub C# można składniowo analizować w izolacji, nie ma sensu formułowania "co to jest typ tej zmiennej" próżni. Znaczenie nazwy typu może być zależny od odwołania do zestawów, importowane elementy obszaru nazw lub innych plików kodu. Te odpowiedzi na pytania za pomocą **semantycznego API**, w szczególności <xref:Microsoft.CodeAnalysis.Compilation?displayProperty=nameWithType> klasy.

Wystąpienie <xref:Microsoft.CodeAnalysis.Compilation> jest odpowiednikiem pojedynczego projektu widziany przez kompilator i reprezentuje wszystkie elementy potrzebne do kompilacji programu Visual Basic lub C#. **Kompilacji** zawiera zestaw plików źródłowych, które ma być kompilowana, odwołania do zestawów, opcje kompilatora. Można przyczyny, informacje o znaczeniu kod przy użyciu inne informacje w tym kontekście. A <xref:Microsoft.CodeAnalysis.Compilation> umożliwia znalezienie **symbole** -jednostek, takich jak typy, przestrzenie nazw elementów członkowskich i zmiennych, których nazwy i inne wyrażenia odwołują się do. Proces kojarzenia nazwy i wyrażenia z **symbole** jest nazywany **powiązanie**.

Podobnie jak <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType>, <xref:Microsoft.CodeAnalysis.Compilation> jest specyficzny dla języka pochodne klasy abstrakcyjnej. Podczas tworzenia wystąpienia kompilacji, należy wywołać metodę fabryki na <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation?displayProperty=nameWithType> (lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicCompilation?displayProperty=nameWithType>) klasy.

## <a name="querying-symbols"></a>Wykonywanie zapytania symboli

W ramach tego samouczka przyjrzymy się "Hello World" program ponownie. Teraz, zapytania symboli w programie, aby zrozumieć, jakie typy reprezentują te symbole. Zapytanie dla typów w przestrzeni nazw i Dowiedz się znaleźć dostępne metody w typie.

> [!IMPORTANT]
> Poniższe przykłady wymagają **SDK kompilatora .NET** instalowany jako część programu Visual Studio 2017 r. Można znaleźć zestawu .NET SDK kompilatora jako ostatni opcjonalny składnik kategorii **tworzenia rozszerzenia programu Visual Studio** obciążenia. Szablony nie są zainstalowane bez tego składnika.

Można wyświetlić kod zakończenia dla tego przykładu w [przykłady repozytorium GitHub](https://github.com/dotnet/samples/csharp/roslyn-sdk/SemanticQuickStart).

> [!NOTE]
> Typy drzewa składni umożliwia dziedziczenia opisano elementy składni różnych są prawidłowe w różnych miejscach w programie. Za pomocą tych interfejsów API często oznacza, że właściwości rzutowanie lub członków kolekcji do określonych typów pochodnych. W poniższych przykładach rzutowania i przydziału są osobnych instrukcji, korzystając ze zmiennych jawnie typu. Możesz przeczytać kod w celu wyświetlenia zwracane typy interfejsu API i typu środowiska uruchomieniowego zwracanych obiektów. W praktyce jest niejawnie wpisane zmienne i zależą od nazwy interfejsu API do opisu typu obiektów badane częściej.

Tworzenie nowych C# **autonomiczne narzędzie do analizy kodu** projektu:

* W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu** do wyświetlenia w oknie dialogowym Nowy projekt.
* W obszarze **Visual C#** > **rozszerzalności**, wybierz **autonomiczne narzędzie do analizy kodu**.
* Nazwa projektu "**SemanticQuickStart**" i kliknij przycisk OK.

Zamierzasz analizowanie podstawowe "Witaj świecie!" Program przedstawiona wcześniej.
Dodaj tekst program Hello World jako stała w Twojej `Program` klasy:

[!code-csharp[Declare the program test](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod do kompilacji drzewa składni w tekście kodu `programText` stałej.  Dodaj następujący wiersz do Twojej `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#2 "Create the syntax tree")]

Następnie należy utworzyć <xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation> z drzewa już utworzone. Zależy od przykładu "Hello World" <xref:System.String> i <xref:System.Console> typów. Należy odwoływać się do zestawu, który deklaruje tych dwóch typów w Twojej kompilacji. Dodaj następujący wiersz do Twojej `Main` metodę, aby utworzyć zbiór drzewa składni, w tym odwołanie do odpowiedniego zestawu:

[!code-csharp[Create the compilation](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#3 "Create the compilation for the semantic model")]

<xref:Microsoft.CodeAnalysis.CSharp.CSharpCompilation.AddReferences%2A?displayProperty=nameWithType> Metoda dodaje odwołania do kompilacji. <xref:Microsoft.CodeAnalysis.MetadataReference.CreateFromFile(System.String,Microsoft.CodeAnalysis.MetadataReferenceProperties,Microsoft.CodeAnalysis.DocumentationProvider)> Metody ładuje zestaw jako odwołanie. 

## <a name="querying-the-semantic-model"></a>Wykonywanie zapytania semantycznego modelu

Po utworzeniu <xref:Microsoft.CodeAnalysis.Compilation> poprosić go dla <xref:Microsoft.CodeAnalysis.SemanticModel> dla każdego <xref:Microsoft.CodeAnalysis.SyntaxTree> zawarte w tym <xref:Microsoft.CodeAnalysis.Compilation>. Model semantyczny można traktować jako źródło dla wszystkich informacji zazwyczaj otrzymuje z intellisense. A <xref:Microsoft.CodeAnalysis.SemanticModel> można uzyskać odpowiedzi na pytania "Jakie nazwy są w zakresie, w tym miejscu?" "Jakie elementy członkowskie są dostępne z tej metody"? "Zmienne, które są używane w tym bloku tekstu?" i "Co nazwa/wyrażenie odwołuje się do?" Dodaj tych zasad, aby utworzyć model semantyczny:

[!code-csharp[Create the semantic model](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#4 "Create the semantic model")]

## <a name="binding-a-name"></a>Nazwa powiązania

<xref:Microsoft.CodeAnalysis.Compilation> Tworzy <xref:Microsoft.CodeAnalysis.SemanticModel> z <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po utworzeniu modelu, można go znaleźć pierwszego zapytania `using` dyrektywy i pobierania informacji o symbolach dla `System` przestrzeni nazw. Dodaj następujące dwa wiersze do Twojej `Main` metody w celu utworzenia modelu semantycznego i pobrać symboli dla pierwszego za pomocą instrukcji:

[!code-csharp[Find the namespace symbol for the first using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#5 "Find the namespace symbol for the first using")]

Poprzedni kod przedstawia sposób uzyskiwania <xref:Microsoft.CodeAnalysis.SemanticModel> obiektu dla Twojego HelloWorld <xref:Microsoft.CodeAnalysis.SyntaxTree>. Po uzyskaniu modelu z nazwą w pierwszym `using` dyrektywa jest powiązany z pobrać <xref:Microsoft.CodeAnalysis.SymbolInfo?displayProperty=nameWithType> dla `System` przestrzeni nazw. Poprzedni kod ilustruje, że używasz **modelu składni** można znaleźć struktury kodu; używasz **modelu semantycznego** zrozumieć jego znaczenie. **Modelu składni** odnajduje ciąg `System` za pomocą instrukcji. **Modelu semantycznego** ma wszystkie informacje dotyczące typów zdefiniowanych w `System` przestrzeni nazw.

Z <xref:Microsoft.CodeAnalysis.SymbolInfo> obiektu można uzyskać <xref:Microsoft.CodeAnalysis.ISymbol?displayProperty=nameWithType> przy użyciu <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> właściwości. Ta właściwość zwraca symbol, który dotyczy tego wyrażenia. W przypadku wyrażeń, które nie odwołuje się do obiektów (takich jak literałach numerycznych) tej właściwości jest `null`. Gdy <xref:Microsoft.CodeAnalysis.SymbolInfo.Symbol?displayProperty=nameWithType> nie ma wartości null, <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> wskazuje typ symbolu. W tym przykładzie <xref:Microsoft.CodeAnalysis.ISymbol.Kind?displayProperty=nameWithType> jest właściwość <xref:Microsoft.CodeAnalysis.SymbolKind.Namespace?displayProperty=nameWithType>. Dodaj następujący kod do Twojej `Main` metody. Pobiera on symbol `System` przestrzeni nazw, a następnie wyświetla wszystkie podrzędne przestrzenie nazw zadeklarowany w `System` przestrzeni nazw:

[!code-csharp[Display all the child namespaces](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#6 "Display all the child namespaces from this compilation")]

Uruchom program i powinien zostać wyświetlony następujący komunikat:

```
Collections
Configuration
Deployment
Diagnostics
Globalization
IO
Reflection
Resources
Runtime
Security
StubHelpers
Text
Threading
Press any key to continue . . .
```

> [!NOTE]
> Dane wyjściowe nie zawierać każdej przestrzeni nazw, która jest przestrzeń nazw podrzędnych `System` przestrzeni nazw. Wyświetla każdej przestrzeni nazw, która znajduje się w tej kompilacji, który tylko odwołuje się zestaw gdzie `System.String` jest zadeklarowany. Wszystkie przestrzenie nazw, zadeklarowanej w innych zestawów nie są znane w tej kompilacji

### <a name="binding-an-expression"></a>Wyrażenie powiązania

Poprzedni kod przedstawia sposób Znajdź symbol przez powiązanie o nazwie. Istnieją inne wyrażenia w programie C#, który może być powiązana, w których nie ma nazwy. Aby zademonstrować tę możliwość, umożliwia dostęp do powiązania proste literału ciągu.

Program "Hello World" zawiera <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LiteralExpressionSyntax?displayProperty=nameWithType>, "Hello, World!" ciąg wyświetlany w konsoli.

Znajdź tekst "Hello, World!" ciąg dzięki umieszczeniu jednego ciągu literału w programie. Następnie po zlokalizowaniu węzeł składni uzyskać informacji o typie dla tego węzła z modelu semantycznego. Dodaj następujący kod do Twojej `Main` metody:

[!code-csharp[Find the namespace symbol for the only using](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#7 "Find the namespace symbol for the only using")]

<xref:Microsoft.CodeAnalysis.TypeInfo?displayProperty=nameWithType> Zawiera struktury <xref:Microsoft.CodeAnalysis.TypeInfo.Type?displayProperty=nameWithType> właściwość, która umożliwia dostęp do semantycznego informacje o typie dla literału. W tym przykładzie to jest `string` typu. Dodaj deklarację, który przypisuje do zmiennej lokalnej tej właściwości:

[!code-csharp[Find the semantic information about the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#8 "Use the string literal to access the semantic information in the string type.")]

Do zakończenia tego samouczka, utworzymy kwerendy LINQ, która tworzy sekwencję wszystkich publicznych metody zadeklarowane w `string` wpisz zwracające `string`. To zapytanie pobiera złożony, więc warto skompiluj go wiersz po wierszu, rekonstrukcji go jako pojedynczego zapytania. Źródło dla tego zapytania jest sekwencja wszystkich elementów członkowskich zadeklarowanych w `string` typu:

[!code-csharp[Access the sequence of members on the string type](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#9 "Access the sequence of members on the string type.")]

Zawiera sekwencji tego źródła wszystkich elementów członkowskich, w tym właściwości i pola, więc filtrować za pomocą <xref:System.Collections.Immutable.ImmutableArray%601.OfType%2A?displayProperty=nameWithType> metodę, aby znaleźć elementy, które są <xref:Microsoft.CodeAnalysis.IMethodSymbol?diplayProperty=nameWithType> obiektów:

[!code-csharp[Filter the sequence to only methods](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#10 "Find the subset of the collection that is the methods.")]

Następnie dodaj inny filtr, aby zwrócić tylko tych metod, które są publiczne ale zwracany `string`:

[!code-csharp[Filter on return type and accessibility](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#11 "Find only the public methods that return a string.")]

Wybierz właściwość name, a tylko unikatowe nazwy, usuwając wszystkie przeciążenia:

[!code-csharp[find the distinct names.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#12 "Use the string literal to access the semantic information in the string type.")]

Można również tworzyć pełne zapytanie przy użyciu składni zapytań LINQ, a następnie wyświetlić nazwy metody w konsoli:

[!code-csharp[build and display the results of this query.](../../../../samples/csharp/roslyn-sdk/SemanticQuickStart/SemanticQuickStart/Program.cs#12 "Build and display the results of the query.")]

Skompiluj i uruchom program. Powinny być widoczne następujące dane wyjściowe:

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
Używano semantycznego interfejsu API można znaleźć i wyświetlić informacje dotyczące symboli, które są częścią tego programu.
