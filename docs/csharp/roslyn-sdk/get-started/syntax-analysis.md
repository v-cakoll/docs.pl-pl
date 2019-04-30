---
title: Rozpoczynanie pracy z usługą analiza składni (interfejsy API Roslyn)
description: Wprowadzenie do przechodzenie przez wykonywanie zapytań i zalet drzewa składni.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: e377fe10e094e958627c3503fc39b7e2d02b3d7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706630"
---
# <a name="get-started-with-syntax-analysis"></a>Rozpoczynanie pracy z usługą analiza składni

W tym samouczku dowiesz się o **API składni**. Składnia interfejsu API zapewnia dostęp do struktur danych, które opisują C# lub programie Visual Basic. Te struktury danych ma wystarczającą ilość szczegółów, aby w pełni reprezentują dowolnego programu o dowolnym rozmiarze. Te struktury można opisać całych programów, które kompilują i działać poprawnie. Zawierają one również opis niekompletne programów, jak zapisać je w edytorze.

Aby włączyć to wyrażenie rozbudowane, API, wchodzące w skład składni interfejsu API i struktur danych są zawsze złożone. Zacznijmy od struktury danych wygląda jak, typowego programu "Hello World":

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

Przyjrzyj się tekst poprzedni program. Możesz rozpoznać dobrze znanych elementów. Cały tekst reprezentuje plik źródłowy lub **jednostki kompilacji**. Pierwsze trzy wiersze tym pliku źródłowym są **dyrektywy using**. Pozostałe źródła znajduje się w **deklarację przestrzeni nazw**. Deklaracja przestrzeni nazw zawiera element podrzędny **deklarację klasy**. Deklaracja klasy zawiera jeden **deklaracji metody**.

Interfejs API składni tworzy strukturę drzewa z certyfikatem głównym, reprezentuje jednostki kompilacji. Węzłów w drzewie reprezentują przy użyciu dyrektyw, deklaracja przestrzeni nazw i inne elementy programu. Struktura drzewa jest kontynuowane do najniższego poziomów: ciąg "Hello World!" jest **token literału ciągu** czyli element podrzędny **argument**. Składnia interfejsu API zapewnia dostęp do struktury programu. Można tworzyć zapytania do rozwiązania konkretnego kodu, zapoznaj się z całego drzewa, że kod i utworzyć nowe drzewa, modyfikując w istniejącym drzewie.

Ten krótki opis zawiera omówienie tego rodzaju informacje przy użyciu interfejsu API składni. Interfejs API składni już nic więcej niż posiadanie interfejsu API, który opisuje dobrze znanych kod tworzy możesz dowiedzieć się z kodu C#. Pełne możliwości zawierają informacje dotyczące sposobu formatowania kodu tym podziałów wiersza, biały i wcięcia. Przy użyciu tych informacji, możesz w pełni reprezentują kodu, jak zostały napisane i odczytywane przez ludzi w programowaniu w języku lub kompilator. Przy użyciu tej struktury można wchodzić w interakcje z kodem źródłowym na poziomie głęboko zrozumiałe. Nie jest już ciągów tekstowych, ale dane, które przedstawiają struktura programu w języku C#.

Aby rozpocząć pracę, musisz zainstalować **zestawu SDK platformy kompilatora .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Opis składni drzew

Użyj interfejsu API składni dla żadnych analizy struktury kodu języka C#. **API składni** udostępnia analizatory składni, drzewa składni i narzędzia do analizowania i Konstruowanie drzewa składni. Jest jak wyszukiwanie kodu dla elementów określonej składni lub odczytać kodu programu.

Drzewo składni jest strukturą danych używaną przez Kompilatory języka C# i Visual Basic, aby zrozumieć programów w języku C# i Visual Basic. Drzewa składni są produkowane przez parser tego samego, który jest uruchamiany, gdy projekt jest kompilowany lub deweloperem, liczba trafień F5. Drzewa składni mają pełnej wierności języka; każdy bit informacji w pliku kodu jest reprezentowany w drzewie. Zapisywanie drzewo składni tekstu odtwarza dokładnie oryginalny tekst, który był analizowany. Drzewa składni są również **niezmienne**; po utworzeniu składni drzewa nigdy nie można zmienić. Konsumenci drzewa można analizować drzew w wielu wątkach, bez blokady lub innych środków współbieżności, wiedząc, że danych nigdy się nie zmienia. Aby utworzyć nowe drzewa, które są wynikiem modyfikowania istniejącego drzewa, można użyć interfejsów API.

Są cztery podstawowe bloki konstrukcyjne drzewa składni:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Klasę, wystąpienie reprezentuje drzewo analizy całego. <xref:Microsoft.CodeAnalysis.SyntaxTree> jest klasą abstrakcyjną, która ma pochodne specyficzny dla języka. Możesz użyć metody parse <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) klasę do analizowania tekstu w języku C# lub VB.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Klasy i wystąpienia, które reprezentują konstrukcji składniowych, takich jak deklaracje, instrukcje, klauzule i wyrażeń.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Struktury, która reprezentuje poszczególne — słowo kluczowe, identyfikator, operator lub znaki interpunkcyjne.
* I wreszcie <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktury, która reprezentuje składniowo nieznaczące bity informacje, takie jak odstępy między tokenami, dyrektywy przetwarzania wstępnego i komentarze.

Elementy towarzyszące składni, tokenów i węzłów składają się hierarchicznie w celu utworzenia drzewa, który całkowicie reprezentuje wszystkie elementy fragment kodu języka Visual Basic lub C#. Możesz zobaczyć ten przy użyciu struktury **Syntax Visualizer** okna. W programie Visual Studio, wybierz **widoku** > **Windows inne** > **Syntax Visualizer**. Na przykład poprzedni plik źródłowy C# bada się **Syntax Visualizer** wygląda podobnie do poniższej ilustracji:

**SyntaxNode**: Blue | **SyntaxToken**: Green | **SyntaxTrivia**: Czerwony ![ C# plik kodu](media/walkthrough-csharp-syntax-figure1.png)

Przechodząc ta struktura drzewa, można znaleźć w pliku kodu instrukcji, wyrażenie, token lub bitowego biały znak.

Możesz niczego znaleźć w pliku kodu za pomocą interfejsów API składni, większości scenariuszy związana z badanie małe fragmenty kodu czy wyszukiwaniu określonej instrukcji lub fragmenty. Dwóch przykładach Pokaż typowe używa do przeglądania struktury kodu lub wyszukiwania dla pojedynczej instrukcji.

## <a name="traversing-trees"></a>Przechodzenie drzewa

Można sprawdzić węzłów w drzewie składni na dwa sposoby. Mogą przechodzić drzewa, aby sprawdzić każdy węzeł lub można wyszukiwać określone elementy lub węzłów.

### <a name="manual-traversal"></a>Ręczne przechodzenia

Zostanie wyświetlony gotowy kod dla tego przykładu w [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy drzewo składni umożliwiają dziedziczenia opisano różne elementy składni, które są prawidłowe w różnych lokalizacjach w programie. Za pomocą tych interfejsów API często oznacza, że właściwości rzutowania lub elementy członkowskie kolekcji dla określonych typów pochodnych. W poniższych przykładach przydziałów i rzutowania są osobnych instrukcji, za pomocą jawnie wpisanych zmiennych. Może odczytywać kod, aby zobaczyć typów zwracanych interfejsu API i typ środowiska uruchomieniowego zwracanych obiektów. W praktyce jest bardziej powszechne, aby używać niejawnie wpisane zmienne i zależą od nazwy interfejsu API do opisu typów obiektów sprawdzane.

Utwórz nowy język C# **narzędzie do analizy kodu autonomicznego** projektu:

* W programie Visual Studio, wybierz **pliku** > **New** > **projektu** Aby wyświetlić okno dialogowe Nowy projekt.
* W obszarze **Visual C#** > **rozszerzalności**, wybierz **narzędzie do analizy kodu autonomicznego**.
* Nazwij swój projekt "**SyntaxTreeManualTraversal**" i kliknij przycisk OK.

Możesz zacząć analizować podstawowe "Hello World!" Program przedstawionej wcześniej.
Dodaj tekst programu Witaj świecie jako stała w swojej `Program` klasy:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod, aby tworzyć **drzewo składni** w tekście kodu `programText` stałej.  Dodaj następujący wiersz do Twojej `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Te dwa wiersze utworzyć drzewo i pobrać węzeł główny w drzewie. Możesz teraz badać węzłów w drzewie. Dodaj następujące wiersze do Twojej `Main` metodę, aby wyświetlić niektórych właściwości węzeł główny drzewa:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Uruchom aplikację, aby wyświetlić kod wykrył o węzła głównego, w tym drzewie.

Zazwyczaj będzie przechodzić drzewa, aby dowiedzieć się więcej o kodzie. W tym przykładzie jest analiza kodu, który znasz, aby zapoznać się z interfejsami API. Dodaj następujący kod do sprawdzenia pierwszego elementu członkowskiego `root` węzła:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Ten element członkowski jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Reprezentuje wszystkie elementy w zakresie `namespace HelloWorld` deklaracji. Dodaj następujący kod, aby sprawdzić, jakie węzły są zadeklarowane wewnątrz `HelloWorld` przestrzeni nazw:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Uruchom program, aby zobaczyć, co wykorzystasz zdobyte umiejętności.

Teraz, gdy wiesz deklaracji jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, Zadeklaruj nowej zmiennej tego typu, aby zbadać deklaracji klasy. Ta klasa zawiera tylko jeden element członkowski: `Main` metody. Dodaj następujący kod, aby znaleźć `Main` metody i obsadź ją <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Węzeł deklaracji metody zawiera wszystkie składni informacje na temat metody. Umożliwia wyświetlanie zwracany typ `Main` metody, liczbę i typy argumentów i tekst treści metody. Dodaj następujący kod:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Uruchom program, aby zobaczyć wszystkie informacje, które już znasz dotyczące tego programu:

```text
The tree is a CompilationUnit node.
The tree has 1 elements in it.
The tree has 4 using statements. They are:
        System
        System.Collections
        System.Linq
        System.Text
The first member is a NamespaceDeclaration.
There are 1 members declared in this namespace.
The first member is a ClassDeclaration.
There are 1 members declared in the Program class.
The first member is a MethodDeclaration.
The return type of the Main method is void.
The method has 1 parameters.
The type of the args parameter is string[].
The body text of the Main method follows:
        {
            Console.WriteLine("Hello, World!");
        }
```

### <a name="query-methods"></a>Metody zapytań

Oprócz przechodzenie drzewa, możesz również zapoznać się z drzewem składni, przy użyciu metody zapytanie zdefiniowane w <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Metody te powinny być znane dla każdego kto zna XPath. Metody te za pomocą LINQ umożliwia szybkie znajdowanie elementów w drzewie. <xref:Microsoft.CodeAnalysis.SyntaxNode> Ma metody zapytań, na przykład <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> i <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Te metody zapytania umożliwia znalezienie argument `Main` metodę jako alternatywę do nawigowania w drzewie. Dodaj następujący kod na końcu Twojej `Main` metody:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

Pierwsza instrukcja używa wyrażenia LINQ oraz <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> metodą lokalizowania tego samego parametru, jak w poprzednim przykładzie.

Uruchom program i widać, że wyrażenie LINQ znaleźć tego samego parametru, jak ręcznie Nawigacja w drzewie.

W przykładzie użyto `WriteLine` instrukcji, aby wyświetlić informacje o drzewa składni, zgodnie z ich-są przenoszone. Można też uzyskać znacznie bardziej, uruchamiając program zakończono w debugerze. Można sprawdzić więcej właściwości i metod, które są częścią drzewa składni utworzonych dla programu Witaj świecie.

## <a name="syntax-walkers"></a>Walkery składni

Często mają być wyszukiwanie węzłów o typie określonym w drzewie składni, na przykład co deklaracja właściwości w pliku. Rozszerzając <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> klasy i zastępowanie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metody są przetwarzane co deklaracja właściwości w drzewie składni bez znajomości wcześniej jego strukturę. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> jest określony rodzaj <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> tym rekursywnie odwiedza węzeł i każdy z jego elementów podrzędnych.

Implementuje w tym przykładzie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> które analizuje drzewa składni. Zbiera `using` dyrektywy znajdzie, nie są importowane `System` przestrzeni nazw.

Utwórz nowy język C# **narzędzie do analizy kodu autonomicznego** projektu; nadaj mu nazwę "**SyntaxWalker**."

Zostanie wyświetlony gotowy kod dla tego przykładu w [repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Przykład w witrynie GitHub zawiera oba projekty, które opisano w tym samouczku.

Jak w poprzednim przykładzie można zdefiniować stałą typu string do przechowywania tekstu programu, który możesz zacząć analizować:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Ten tekst źródłowy zawiera `using` dyrektywy znajdują się na czterech różnych lokalizacji:-poziomie plików, w przestrzeni nazw najwyższego poziomu i dwa zagnieżdżone przestrzenie nazw. W tym przykładzie podkreślono core scenariusz użycia <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> klasy, aby kod zapytania. Byłoby kłopotliwe do odwiedzenia każdego węzła w drzewie składni głównego można znaleźć za pomocą deklaracji. Zamiast tego należy utworzyć klasę pochodną i przesłonić metodę, która jest wywoływana tylko wtedy, gdy bieżący węzeł w drzewie przy użyciu dyrektywy. Osoby odwiedzające sieci wykonać pracę na inne typy węzłów. Ta metoda pojedynczego sprawdza, czy każdy z `using` instrukcji i tworzy kolekcję przestrzeni nazw, które nie znajdują się w `System` przestrzeni nazw. Tworzysz <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> , sprawdza, czy wszystkie `using` instrukcji, ale tylko `using` instrukcji.

Po zdefiniowaniu tekst programu, należy utworzyć `SyntaxTree` i Uzyskaj tego drzewa:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Następnie utwórz nową klasę. W programie Visual Studio, wybierz **projektu** > **Dodaj nowy element**. W **Dodaj nowy element** typ okna dialogowego *UsingCollector.cs* jako nazwę pliku.

Możesz wdrożyć `using` gości funkcji `UsingCollector` klasy. Rozpocznij `UsingCollector` dziedziczyć klasy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Potrzebny jest magazyn do przechowywania węzły przestrzeni nazw, które Trwa zbieranie danych.  Zadeklaruj publiczną właściwość tylko do odczytu w `UsingCollector` klasy; możesz użyć tej zmiennej do przechowywania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> węzłów można znaleźć:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Klasa bazowa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logikę do odwiedzenia każdego węzła w drzewie składni. Klasa pochodna zastępuje metody wywoływane dla określonych węzłów, których interesuje Cię. W tym przypadku interesuje Cię dowolne `using` dyrektywy. Oznacza to, że konieczne jest przesłonięcie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> metody. Jeden argument do tej metody jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> obiektu. Jest ważną zaletą używania gości: wywołują zastąpionych metod z argumentami już rzutowany na typ określonego węzła. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Klasa ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> właściwość, która przechowuje nazwę przestrzeni nazw importowanych. Jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Dodaj następujący kod w <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> zastąpienia:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Zgodnie z wcześniejszym przykładzie dodano szereg `WriteLine` instrukcji, aby ułatwić zrozumienie tej metody. Widać, gdy jest wywoływana, a jakie argumenty są przekazywane do niego każdorazowo.

Na koniec należy dodać dwa wiersze kodu, aby utworzyć `UsingCollector` potem z łatwością można znaleźć węzła głównego, zbierania wszystkich `using` instrukcji. Następnie należy dodać `foreach` pętli, aby wyświetlić wszystkie `using` znaleziono moduł zbierający instrukcji:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Skompiluj i uruchom program. Powinny zostać wyświetlone następujące dane wyjściowe:

```console
        VisitUsingDirective called with System.
        VisitUsingDirective called with System.Collections.Generic.
        VisitUsingDirective called with System.Linq.
        VisitUsingDirective called with System.Text.
        VisitUsingDirective called with Microsoft.CodeAnalysis.
                Success. Adding Microsoft.CodeAnalysis.
        VisitUsingDirective called with Microsoft.CodeAnalysis.CSharp.
                Success. Adding Microsoft.CodeAnalysis.CSharp.
        VisitUsingDirective called with Microsoft.
                Success. Adding Microsoft.
        VisitUsingDirective called with System.ComponentModel.
        VisitUsingDirective called with Microsoft.Win32.
                Success. Adding Microsoft.Win32.
        VisitUsingDirective called with System.Runtime.InteropServices.
        VisitUsingDirective called with System.CodeDom.
        VisitUsingDirective called with Microsoft.CSharp.
                Success. Adding Microsoft.CSharp.
Microsoft.CodeAnalysis
Microsoft.CodeAnalysis.CSharp
Microsoft
Microsoft.Win32
Microsoft.CSharp
Press any key to continue . . .
```

Gratulacje! Wykorzystano **API składni** zlokalizować określonych typów języka C# instrukcje i deklaracje w języku C# kodu źródłowego.
