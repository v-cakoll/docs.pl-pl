---
title: Wprowadzenie do analizy składni (Roslyn API)
description: Wprowadzenie do przechodzenie, zapytań i przejście drzewa składni.
author: billwagner
ms.author: wiwagn
ms.date: 02/05/2018
ms.topic: conceptual
ms.prod: .net
ms.technology: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 90d6542122dd8c579c63f5f003441ce63a7ca5e9
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="get-started-with-syntax-analysis"></a>Wprowadzenie do analizy składni

W tym samouczku będziesz Eksploruj **API składni**. Interfejs API składni zapewnia dostęp do struktur danych, które opisują C# lub Visual Basic programu. Te struktury danych ma za mało szczegółów, że pełni reprezentują dowolnego programu o dowolnym rozmiarze. Te struktury można opisać pełną programy, które skompilować i działa poprawnie. Niekompletne programy można opisano również podczas pisania je w edytorze.

Aby włączyć ten wyrażeń, są zawsze złożone struktur danych i interfejsów API, która składa się z interfejsu API składni. Zacznijmy od wygląd struktury danych typowego programu "Hello World":

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

Spójrz na tekst poprzedniego programu. Rozpoznajesz elementy. Plik źródłowy pojedynczego reprezentuje cały tekst lub **jednostki kompilacji**. Pierwsze trzy wiersze pliku źródłowego są **przy użyciu dyrektyw**. Pozostałe źródła znajduje się w **deklaracji przestrzeni nazw**. Deklaracja przestrzeni nazw zawiera element podrzędny **deklaracji klasy**. Deklaracja klasy zawiera jeden **deklaracji metody**.

Interfejs API składni tworzy struktury drzewa z elementem głównym reprezentujący jednostki kompilacji. Reprezentuje węzłów w drzewie przy użyciu dyrektyw, deklaracji przestrzeni nazw i inne elementy programu. Struktura drzewa będzie kontynuowane do najniższego poziomów: ciąg "Hello World!" jest **token literału ciągu** będący elementem podrzędnym **argument**. Interfejs API składni zapewnia dostęp do struktury programu. Można wyszukać określonego kodu rozwiązania, przeprowadź całego drzewa, że kod i tworzenia nowego drzew przez zmodyfikowanie istniejącego drzewa.

Ten krótki opis zawiera omówienie tego rodzaju informacje dostępne przy użyciu interfejsu API składni. Interfejs API składni jest nic więcej niż posiadanie interfejs API, który opisuje znanego kodu tworzy należy znać w języku C#. Pełne możliwości zawierają informacje o sposób formatowania kodu m.in. podziały wierszy, odstępy i wcięcia. Korzystając z tych informacji, możesz pełni reprezentują kod napisany i odczytu przez programistów człowieka lub kompilatora. Przy użyciu tej struktury pozwala na współdziałanie z kodem źródłowym na poziomie głęboko łatwy do rozpoznania. Nie jest już ciągów tekstowych, ale dane, które reprezentują struktura programu w języku C#.

Aby rozpocząć pracę, musisz zainstalować **zestawu SDK platformy kompilatora .NET**:

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Opis drzewa składni

Używasz składni interfejsu API dla dowolnego analizy struktury kodu C#. **API składni** przedstawia analizatory składni, drzewa składni i narzędzia do analizowania i tworzenia drzewa składni. Jest sposób wyszukiwania kod elementy składni lub odczytać kodu programu.

Drzewo składni jest strukturą danych używaną przez Kompilatory języka C# i Visual Basic, aby zrozumieć programów C# i Visual Basic. Drzewa składni są produkowane przez tego samego analizator uruchamiany po utworzeniu projektu lub deweloperem trafienia F5. Drzewa składni ma pełnej wierności języka; każdy bit informacji w pliku kodu jest reprezentowany w drzewie. Drzewo składni zapisywania tekstu powtarza dokładne oryginalny tekst, który zostanie przeanalizowany. Drzewa składni są również **niezmienne**; po utworzeniu składnię drzewa nigdy nie można zmienić. Konsumenci drzew można analizować drzew na wiele wątków bez blokady lub inne środki współbieżności, wiedząc, że nigdy nie zmieniają się dane. Interfejsy API umożliwia utworzenie nowego drzew, będące wynikiem modyfikowania istniejącego drzewa.

Są cztery podstawowe bloki drzewa składni:

* <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> Klasy drzewo analizy całego reprezentuje wystąpienie. <xref:Microsoft.CodeAnalysis.SyntaxTree> jest klasą abstrakcyjną, zawierający pochodne specyficzny dla języka. Użyj metody parse <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> (lub <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>) klasy można przeanalizować tekstu w językach C# i VB.
* <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> Klasy wystąpień, które reprezentują konstrukcje składni takich jak deklaracje, instrukcje klauzule i wyrażenia.
* <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> Struktury, która reprezentuje pojedyncze słowo kluczowe, identyfikator, operator lub znaki interpunkcyjne.
* I na końcu <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktury, która reprezentuje składniowo nieznaczne bity informacje, takie jak odstępów między tokeny, dyrektywy preprocesora i komentarze.

Elementy towarzyszące składni, tokeny i węzły składają się hierarchicznie Aby utworzyć drzewo reprezentujący całkowicie wszystko w fragment kodu języka Visual Basic lub C#. Widać, za pomocą tej struktury **wizualizatora składni** okna. W programie Visual Studio, wybierz **widoku** > **inne okna** > **wizualizatora składni**. Na przykład poprzedniego pliku źródłowego C# zbadać za pomocą **wizualizatora składni** wygląda podobnie do poniższej ilustracji:

**SyntaxNode**: niebieski | **SyntaxToken**: zielony | **SyntaxTrivia**: czerwony ![plik kodu C#](media/walkthrough-csharp-syntax-figure1.png)

Przechodząc ta struktura drzewa, można znaleźć w pliku kodu instrukcji, wyrażenie, token lub bitowego odstępu.

Możesz niczego znaleźć w pliku kodu za pomocą interfejsów API składni, większości scenariuszy związana badanie małych fragmentów kodu lub wyszukiwanie określonego instrukcji lub fragmenty. Dwa przykłady, które należy wykonać typowe Pokaż używa do przeglądania struktury kodu lub wyszukiwania dla jednej instrukcji.

## <a name="traversing-trees"></a>Przechodzenie drzew

Można sprawdzić węzłów w drzewie składni na dwa sposoby. Można przechodzenia drzewa do sprawdzenia każdego węzła lub może wyszukiwać określone elementy lub być węzłami.

### <a name="manual-traversal"></a>Przechodzenie ręczne

Można wyświetlić kod zakończenia dla tego przykładu w [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy drzewa składni umożliwia dziedziczenia opisano elementy składni różnych są prawidłowe w różnych miejscach w programie. Za pomocą tych interfejsów API często oznacza, że właściwości rzutowanie lub członków kolekcji do określonych typów pochodnych. W poniższych przykładach rzutowania i przydziału są osobnych instrukcji, korzystając ze zmiennych jawnie typu. Możesz przeczytać kod w celu wyświetlenia zwracane typy interfejsu API i typu środowiska uruchomieniowego zwracanych obiektów. W praktyce jest niejawnie wpisane zmienne i zależą od nazwy interfejsu API do opisu typu obiektów badane częściej.

Tworzenie nowych C# **autonomiczne narzędzie do analizy kodu** projektu:

* W programie Visual Studio, wybierz **pliku** > **nowy** > **projektu** do wyświetlenia w oknie dialogowym Nowy projekt.
* W obszarze **Visual C#** > **rozszerzalności**, wybierz **autonomiczne narzędzie do analizy kodu**.
* Nazwa projektu "**SyntaxTreeManualTraversal**" i kliknij przycisk OK.

Zamierzasz analizowanie podstawowe "Witaj świecie!" Program przedstawiona wcześniej.
Dodaj tekst program Hello World jako stała w Twojej `Program` klasy:

[!code-csharp[Declare the program text](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod do kompilacji **drzewa składni** w tekście kodu `programText` stałej.  Dodaj następujący wiersz do Twojej `Main` metody:

[!code-csharp[Create the tree](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Te dwa wiersze tworzenia drzewa i pobierania węzła głównego tego drzewa. Teraz można zbadać węzłów w drzewie. Dodaj następujące wiersze do Twojej `Main` metodę, aby wyświetlić niektórych właściwości węzła głównego drzewa:

[!code-csharp[Examine the root node](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Uruchom aplikację, aby wyświetlić kod wykrył o węzła głównego w tym drzewie.

Zazwyczaj pomijałby drzewa, aby dowiedzieć się więcej na temat kodu. W tym przykładzie jest analiza kodu wiesz, aby zapoznać się z interfejsów API. Dodaj następujący kod do sprawdzenia pierwszego elementu członkowskiego z `root` węzła:

[!code-csharp[Find the first member](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Ten element członkowski jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>. Reprezentuje wszystkie elementy w zakresie `namespace HelloWorld` deklaracji. Dodaj następujący kod, aby sprawdzić, jakie węzły są deklarowane w `HelloWorld` przestrzeni nazw:

[!code-csharp[Find the class declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Uruchom program, aby wyświetlić podsumowanie samouczka.

Teraz, znając deklaracja jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>, Zadeklaruj nową zmienną typu do sprawdzenia deklaracji klasy. Ta klasa zawiera tylko jeden element członkowski: `Main` metody. Dodaj następujący kod, aby znaleźć `Main` metody i rzutować obiekt <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>.

[!code-csharp[Find the main declaration](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Węzeł deklaracji metody zawiera wszystkie składni informacje na temat metody. Umożliwia wyświetlanie zwracany typ `Main` — metoda, liczbę i typy argumentów i treści metody. Dodaj następujący kod:

[!code-csharp[Examine the syntax of the main method](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Uruchom program, aby zobaczyć wszystkie informacje, które zostały odnalezione o tym programie:

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

### <a name="query-methods"></a>Metody zapytania

Oprócz przechodzenie drzewa, można również zapoznać się przy użyciu metody query zdefiniowane w drzewie składni <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>. Te metody powinny być znane osobom zapoznać się z XPath. Za pomocą tych metod i LINQ do szybkiego wyszukiwania elementów w drzewie. <xref:Microsoft.CodeAnalysis.SyntaxNode> Ma metody zapytań, na przykład <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>, <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> i <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>.

Te metody query Umożliwia znalezienie argument `Main` metody zamiast przechodzenia drzewa. Dodaj następujący kod do dołu Twojej `Main` metody:

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

Pierwsza instrukcja korzysta z wyrażenia LINQ i <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> metodą lokalizowania tego samego parametru co w poprzednim przykładzie.

Uruchom program i widać, że wyrażenie LINQ znaleźć tego samego parametru jako ręcznie poruszanie się w drzewie.

W przykładzie użyto `WriteLine` instrukcje, aby wyświetlić informacje o drzewa składni, ponieważ są one przechodzić. Można też uzyskać bardziej, uruchamiając program zakończono w debugerze. Należy zbadać więcej właściwości i metod, które są częścią drzewa składni tworzone programu hello world.

## <a name="syntax-walkers"></a>Składnia walkers

Często chcesz znaleźć wszystkie węzły określonego typu w drzewie składni, na przykład co deklaracja właściwości w pliku. Rozszerzając <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> klasy i zastępowanie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metody, są przetwarzane co deklaracja właściwości w drzewie składni bez uprzedniego uzyskania informacji o jego struktury wcześniej. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> jest określony rodzaj <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> tego rekursywnie odwiedza węzła oraz wszystkich jego obiektów podrzędnych.

W tym przykładzie implementuje <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> która sprawdza drzewa składni. Zbiera `using` dyrektywy znajdzie nie są importowane `System` przestrzeni nazw.

Tworzenie nowych C# **autonomiczne narzędzie do analizy kodu** projektu; nadaj mu nazwę "**SyntaxWalker**."

Można wyświetlić kod zakończenia dla tego przykładu w [repozytorium GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/roslyn-sdk/SyntaxQuickStart). Przykładem w witrynie GitHub zawiera oba projekty opisane w tym samouczku.

Jak poprzedni przykład można zdefiniować stałą typu string do przechowywania tekstu programu, który będzie analizować:

[!code-csharp[Define the code text to analyzer](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Ten tekst źródłowy zawiera `using` dyrektywy znajdują się na czterech różnych lokalizacji: poziomie plików, w przestrzeni nazw najwyższego poziomu, a w dwóch zagnieżdżonych obszarów nazw. W tym przykładzie wyróżniono core scenariusz użycia <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> klasy kod zapytania. Byłoby skomplikowane, aby odwiedzić każdy węzeł w drzewie składni głównego można znaleźć za pomocą deklaracji. Zamiast tego należy utworzyć klasy pochodnej i przesłonić metodę, która jest wywoływana tylko wtedy, gdy bieżący węzeł w drzewie using dyrektywy. Osoby odwiedzające sieci wykonać pracę na inne typy węzłów. Ta metoda pojedynczego sprawdza, czy każdy z `using` instrukcje i tworzy kolekcję obszarów nazw, które nie znajdują się w `System` przestrzeni nazw. Tworzenia <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> która sprawdza, czy wszystkie `using` instrukcji, ale tylko `using` instrukcje.

Teraz, zdefiniowany przez użytkownika tekstu program, należy utworzyć `SyntaxTree` i uzyskać katalogu głównego tego drzewa:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Następnie utwórz nową klasę. W programie Visual Studio, wybierz **projektu** > **Dodaj nowy element**. W **Dodaj nowy element** typu okna dialogowego *UsingCollector.cs* jako nazwę pliku.

Można zaimplementować `using` funkcji odwiedzający `UsingCollector` klasy. Rozpocznij `UsingCollector` klasa pochodzi od <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>.

[!code-csharp[Declare the base class for the using collector](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Potrzebny jest magazyn do przechowywania węzłów przestrzeni nazw, które zbierasz.  Deklarowanie publiczną właściwość tylko do odczytu w `UsingCollector` klasy; możesz użyć tej zmiennej do przechowywania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> węzłów możesz znaleźć:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Klasa podstawowa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logika odwiedź każdy węzeł w drzewie składni. Klasa pochodna zastępuje metody wywołane dla określonych węzłów interesujący Cię w. W takim przypadku Cię w żadnym `using` dyrektywy. Oznacza to, że konieczne jest przesłonięcie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> metody. Jeden argument do tej metody jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> obiektu. Jest ważne zaletą używania gości: wywołują przesłoniętych metod z argumentami już rzutowany na typ określonego węzła. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> Klasa ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> właściwość, która przechowuje nazwę importowanych przestrzeni nazw. Jest <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Dodaj następujący kod w <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> zastąpienia:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Zgodnie z poprzedniego przykładu, dodano szereg `WriteLine` instrukcje w celu pomocy w wiedzę na temat tej metody. Widać, gdy jest wywoływana, i jakie argumenty przekazywane do niej zawsze.

Na koniec należy dodać dwa wiersze kodu do utworzenia `UsingCollector` i jego można znaleźć węzła głównego zbierania wszystkich `using` instrukcje. Następnie należy dodać `foreach` pętli, aby wyświetlić wszystkie `using` instrukcje znaleziono z modułu zbierającego:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

Skompiluj i uruchom program. Powinny być widoczne następujące dane wyjściowe:

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

Gratulacje! Używano **API składni** zlokalizować określonych rodzajów C# instrukcje i deklaracje w języku C# kod źródłowy.
