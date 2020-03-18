---
title: Wprowadzenie do analizy składni (interfejsy API Roslyn)
description: Wprowadzenie do przechodzenia, wykonywania zapytań i przechodzenia drzew składni.
ms.date: 02/05/2018
ms.custom: mvc
ms.openlocfilehash: 22d1303c9daa2ae35cf130b0c857cd7a5efdbe76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240522"
---
# <a name="get-started-with-syntax-analysis"></a>Wprowadzenie do analizy składni

W tym samouczku zapoznajesz się z **interfejsem API składni**. Interfejs API składni zapewnia dostęp do struktur danych, które opisują program Języka C# lub Visual Basic. Te struktury danych mają wystarczająco dużo szczegółów, że mogą w pełni reprezentować dowolny program o dowolnym rozmiarze. Te struktury można opisać kompletne programy, które kompilują i działają poprawnie. Mogą również opisywać niekompletne programy, jak je piszesz, w edytorze.

Aby włączyć to wyrażenie sformatowane, struktury danych i interfejsy API, które tworzą składni interfejsu API są koniecznie złożone. Zacznijmy od tego, jak wygląda struktura danych dla typowego programu "Hello World":

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

Spójrz na tekst poprzedniego programu. Rozpoznajesz znane elementy. Cały tekst reprezentuje pojedynczy plik źródłowy lub **jednostkę kompilacji**. Pierwsze trzy wiersze tego pliku źródłowego **używają dyrektyw**. Pozostałe źródło znajduje się w **deklaracji obszaru nazw**. Deklaracja obszaru nazw zawiera **deklarację klasy**podrzędnej . Deklaracja klasy zawiera **jedną deklarację metody**.

Interfejs API składni tworzy strukturę drzewa z katalogiem głównym reprezentującym jednostkę kompilacji. Węzły w drzewie reprezentują using dyrektyw, deklaracji obszaru nazw i wszystkie inne elementy programu. Struktura drzewa nadal do najniższych poziomów: ciąg "Hello World!" jest **tokenem literału ciągu,** który jest potomkiem **argumentu**. Interfejs API składni zapewnia dostęp do struktury programu. Można zapytań dla określonych praktyk kodu, chodzić całe drzewo, aby zrozumieć kod i utworzyć nowe drzewa, modyfikując istniejące drzewo.

Ten krótki opis zawiera omówienie rodzaju informacji dostępnych przy użyciu interfejsu API składni. Interfejs API składni jest niczym więcej niż formalnyinterfejs API, który opisuje znane konstrukcje kodu znane z języka C#. Pełne możliwości obejmują informacje o sposobie formatowania kodu, w tym podziały wierszy, odstępy i wcięcia. Korzystając z tych informacji, można w pełni reprezentować kod jako napisany i odczytany przez programistów lub kompilatora. Za pomocą tej struktury umożliwia interakcję z kodem źródłowym na poziomie głęboko znaczące. Nie jest to już ciągi tekstowe, ale dane reprezentujące strukturę programu C#.

Aby rozpocząć, należy zainstalować **zestaw SDK platformy kompilatora .NET:**

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="understanding-syntax-trees"></a>Opis drzew składni

Interfejs API składni służy do dowolnej analizy struktury kodu C#. **Interfejs API składni** udostępnia analizatory, drzewa składni i narzędzia do analizowania i konstruowania drzew składni. W ten sposób można wyszukać kod dla określonych elementów składni lub odczytać kod programu.

Drzewo składni to struktura danych używana przez kompilatory Języka C# i Visual Basic do zrozumienia programów Języka C# i Visual Basic. Drzewa składni są tworzone przez ten sam analizator, który jest uruchamiany, gdy projekt jest zbudowany lub deweloper uderza F5. Drzewa składni mają pełną wierność z językiem; każdy bit informacji w pliku kodu jest reprezentowany w drzewie. Zapis drzewa składni na tekst odtwarza dokładnie oryginalny tekst, który został przeanalizowany. Drzewa składni są również **niezmienne;** po utworzeniu drzewa składni nigdy nie można zmienić. Konsumenci drzew można analizować drzewa na wiele wątków, bez blokad lub innych środków współbieżności, wiedząc, że dane nigdy się nie zmienia. Za pomocą interfejsów API można tworzyć nowe drzewa, które są wynikiem modyfikowania istniejącego drzewa.

Cztery podstawowe bloki składni drzew składni to:

* Klasa, <xref:Microsoft.CodeAnalysis.SyntaxTree?displayProperty=nameWithType> której wystąpienie reprezentuje całe drzewo analizy. <xref:Microsoft.CodeAnalysis.SyntaxTree>jest klasą abstrakcyjną, która ma instrumenty pochodne specyficzne dla języka. Metody analizy (lub) <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxTree?displayProperty=nameWithType> <xref:Microsoft.CodeAnalysis.VisualBasic.VisualBasicSyntaxTree?displayProperty=nameWithType>klasy do analizowania tekstu w języku C# lub Visual Basic.
* Klasa, <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType> których wystąpienia reprezentują konstrukcje składniowe, takie jak deklaracje, instrukcje, klauzule i wyrażenia.
* Struktura, <xref:Microsoft.CodeAnalysis.SyntaxToken?displayProperty=nameWithType> która reprezentuje pojedyncze słowo kluczowe, identyfikator, operator lub znaki interpunkcyjne.
* I wreszcie <xref:Microsoft.CodeAnalysis.SyntaxTrivia?displayProperty=nameWithType> struktura, która reprezentuje syntaktycznie nieistotne bity informacji, takie jak biały znak między tokenami, dyrektywy przetwarzania wstępnego i komentarze.

Ciekawostki, tokeny i węzły składają się hierarchicznie, tworząc drzewo, które całkowicie reprezentuje wszystko w fragmencie kodu Języka Visual Basic lub C#. Tę strukturę można zobaczyć za pomocą okna **Wizualizator składni.** W programie Visual Studio wybierz pozycję **Wyświetl** > inny**wizualizator składni****systemu Windows** > . Na przykład poprzedni plik źródłowy Języka C# zbadany przy użyciu **wizualizatora składni** wygląda następująco:

**Węzeł składni**: Niebieski | **SkładniaToken**: Zielony | **Składnia Trivia:** Czerwony ![plik kodu C#](media/walkthrough-csharp-syntax-figure1.png)

Nawigując po tej strukturze drzewa, można znaleźć dowolną instrukcję, wyrażenie, token lub bit odstępu w pliku kodu.

Chociaż można znaleźć wszystko w pliku kodu przy użyciu składni interfejsów API, większość scenariuszy obejmuje badanie małych fragmentów kodu lub wyszukiwanie określonych instrukcji lub fragmentów. Dwa przykłady, które należy wykonać pokaż typowe zastosowania do przeglądania struktury kodu lub wyszukiwania pojedynczych instrukcji.

## <a name="traversing-trees"></a>Przemierzanie drzew

Węzły w drzewie składni można sprawdzić na dwa sposoby. Można przechodzić przez drzewo, aby zbadać każdy węzeł lub można zapytań dla określonych elementów lub węzłów.

### <a name="manual-traversal"></a>Ręczne przechodzenie

Gotowy kod dla tego przykładu można zobaczyć w [naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart).

> [!NOTE]
> Typy Drzewa składni używają dziedziczenia do opisywania różnych elementów składni, które są prawidłowe w różnych lokalizacjach w programie. Korzystanie z tych interfejsów API często oznacza właściwości rzutowania lub członków kolekcji do określonych typów pochodnych. W poniższych przykładach przypisania i rzutowania są oddzielne instrukcje, przy użyciu jawnie wpisane zmienne. Można odczytać kod, aby zobaczyć typy zwracane interfejsu API i typu wykonywania zwróconych obiektów. W praktyce jest bardziej powszechne do używania niejawnie wpisane zmienne i polegać na nazwy interfejsu API do opisania typu obiektów badane.

Utwórz nowy projekt narzędzia do **analizy kodu autonomicznego** języka C#:

* W programie Visual Studio wybierz pozycję **Plik** > **nowy** > **projekt,** aby wyświetlić okno dialogowe Nowy projekt.
* W obszarze**Rozszerzalność** **języka Visual C#** > wybierz pozycję **Autonomiczne narzędzie do analizy kodu**.
* Nazwij swój projekt "**SyntaxTreeManualTraversal**" i kliknij przycisk OK.

Będziesz analizować podstawowe "Hello World!" program pokazany wcześniej.
Dodaj tekst programu Hello World jako stałą w swojej `Program` klasie:

[!code-csharp[Declare the program text](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#1 "Declare a constant string for the program text to analyze")]

Następnie dodaj następujący kod, aby utworzyć **drzewo składni** `programText` dla tekstu kodu w stałej.  Dodaj następujący wiersz `Main` do metody:

[!code-csharp[Create the tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#2 "Create the syntax tree")]

Te dwie linie tworzą drzewo i pobierają węzeł główny tego drzewa. Teraz można sprawdzić węzły w drzewie. Dodaj te wiersze do metody, `Main` aby wyświetlić niektóre właściwości węzła głównego w drzewie:

[!code-csharp[Examine the root node](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#3 "Examine the root node")]

Uruchom aplikację, aby zobaczyć, co kod został odnaleziony o węźle głównym w tym drzewie.

Zazwyczaj należy przejść przez drzewo, aby dowiedzieć się o kodzie. W tym przykładzie analizujesz kod, który znasz, aby eksplorować interfejsy API. Dodaj następujący kod, aby sprawdzić `root` pierwszy element członkowski węzła:

[!code-csharp[Find the first member](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#4 "Find the first member")]

Ten członek <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NamespaceDeclarationSyntax?displayProperty=nameWithType>jest . Reprezentuje wszystko w zakresie `namespace HelloWorld` deklaracji. Dodaj następujący kod, aby sprawdzić, które `HelloWorld` węzły są zadeklarowane w obszarze nazw:

[!code-csharp[Find the class declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#5 "Find the class declaration")]

Uruchom program, aby zobaczyć, czego się nauczyłeś.

Teraz, gdy wiesz, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.ClassDeclarationSyntax?displayProperty=nameWithType>że deklaracja jest , zadeklarować nową zmienną tego typu, aby zbadać deklarację klasy. Ta klasa zawiera tylko `Main` jeden element członkowski: metodę. Dodaj następujący kod, `Main` aby znaleźć metodę i <xref:Microsoft.CodeAnalysis.CSharp.Syntax.MethodDeclarationSyntax?displayProperty=nameWithType>oddać ją do pliku .

[!code-csharp[Find the main declaration](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#6 "Find the main declaration")]

Węzeł deklaracji metody zawiera wszystkie informacje składniowe dotyczące metody. Wyświetlmy zwracany typ `Main` metody, liczbę i typy argumentów oraz tekst podstawowy metody. Dodaj następujący kod:

[!code-csharp[Examine the syntax of the main method](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#7 "Display information about the main method")]

Uruchom program, aby wyświetlić wszystkie informacje, które zostały wykryte na temat tego programu:

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

### <a name="query-methods"></a>Metody kwerendy

Oprócz przechodzenia przez drzewa można również eksplorować drzewo składni <xref:Microsoft.CodeAnalysis.SyntaxNode?displayProperty=nameWithType>przy użyciu metod kwerendy zdefiniowanych na . Metody te powinny być natychmiast znane każdemu zaznajomienizi z XPath. Za pomocą tych metod z LINQ szybko znaleźć rzeczy w drzewie. Ma <xref:Microsoft.CodeAnalysis.SyntaxNode> metody kwerend, <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A>takie <xref:Microsoft.CodeAnalysis.SyntaxNode.AncestorsAndSelf%2A> <xref:Microsoft.CodeAnalysis.SyntaxNode.ChildNodes%2A>jak , i .

Za pomocą tych metod kwerendy można `Main` znaleźć argument do metody jako alternatywa dla nawigacji drzewa. Dodaj następujący kod do dolnej części metody: `Main`

[!code-csharp[Query the tree for the arguments to Main](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/HelloSyntaxTree/Program.cs#8 "Query the tree for the arguments to Main")]

Pierwsza instrukcja używa wyrażenia LINQ i <xref:Microsoft.CodeAnalysis.SyntaxNode.DescendantNodes%2A> metody, aby zlokalizować ten sam parametr, co w poprzednim przykładzie.

Uruchom program i widać, że wyrażenie LINQ znaleziono ten sam parametr, co ręczne poruszanie się po drzewie.

Przykład używa `WriteLine` instrukcji do wyświetlania informacji o drzewach składni podczas ich przechodzenia. Można również dowiedzieć się znacznie więcej, uruchamiając gotowy program w ramach debugera. Można zbadać więcej właściwości i metod, które są częścią drzewa składni utworzonego dla programu hello world.

## <a name="syntax-walkers"></a>Spacerowicze składni

Często chcesz znaleźć wszystkie węzły określonego typu w drzewie składni, na przykład każdą deklarację właściwości w pliku. Rozszerzając <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker?displayProperty=nameWithType> klasę i zastępując <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitPropertyDeclaration(Microsoft.CodeAnalysis.CSharp.Syntax.PropertyDeclarationSyntax)> metodę, przetwarzasz każdą deklarację właściwości w drzewie składni, nie znając wcześniej jej struktury. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>jest specyficznym <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor> rodzajem tego cyklicznego odwiedza węzeł i każde z jego dzieci.

W tym przykładzie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje, który sprawdza drzewo składni. Zbiera `using` dyrektyw, które stwierdza, że nie `System` są importowane obszaru nazw.

Utwórz nowy projekt narzędzia do **analizy kodu autonomicznego** języka C#; nazwa **"SyntaxWalker**"

Gotowy kod dla tego przykładu można zobaczyć w [naszym repozytorium GitHub](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/SyntaxQuickStart). Przykład na GitHub zawiera oba projekty opisane w tym samouczku.

Podobnie jak w poprzednim przykładzie, można zdefiniować stałą ciągu do przechowywania tekstu programu, który zamierzasz przeanalizować:

[!code-csharp[Define the code text to analyzer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#1 "Define the program text to analyze")]

Ten tekst `using` źródłowy zawiera dyrektywy rozproszone w czterech różnych lokalizacjach: na poziomie pliku, w obszarze nazw najwyższego poziomu i w dwóch zagnieżdżonych przestrzeniach nazw. W tym przykładzie wyróżniono <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> podstawowy scenariusz używania klasy do wykonywania zapytań kodu. Byłoby kłopotliwe, aby odwiedzić każdy węzeł w drzewie składni katalogu głównego, aby znaleźć przy użyciu deklaracji. Zamiast tego należy utworzyć klasę pochodną i zastąpić metodę, która jest wywoływana tylko wtedy, gdy bieżący węzeł w drzewie jest using dyrektywy. Użytkownik nie wykonuje żadnej pracy nad innymi typami węzłów. Ta pojedyncza metoda sprawdza `using` każdą z instrukcji i tworzy kolekcję przestrzeni `System` nazw, które nie są w przestrzeni nazw. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> Tworzysz, który sprawdza `using` wszystkie instrukcje, `using` ale tylko instrukcje.

Po zdefiniowaniu tekstu programu należy utworzyć `SyntaxTree` katalog główny tego drzewa:

[!code-csharp[Create the Syntax tree and access the root](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#2 "Create the Syntax tree and access the root node.")]

Następnie utwórz nową klasę. W programie Visual Studio wybierz pozycję **Project** > **Add New Item**. W oknie dialogowym **Dodawanie nowego elementu** *UsingCollector.cs* jako nazwa pliku.

Zaimplementujesz `using` funkcjonalność odwiedzającego `UsingCollector` w klasie. Zacznij od `UsingCollector` tego, aby <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker>klasa pochodziła od .

[!code-csharp[Declare the base class for the using collector](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#3 "Declare the base class for the UsingCollector")]

Magazyn jest potrzebny do przechowywania zbieraczy węzłów obszaru nazw.  Zadeklarować publiczną właściwość tylko `UsingCollector` do odczytu w klasie; ta zmienna służy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> do przechowywania węzłów, które można znaleźć:

[!code-csharp[Declare storage for the using syntax nodes](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#4 "Declare storage for the using syntax nodes")]

Klasa podstawowa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxWalker> implementuje logikę, aby odwiedzić każdy węzeł w drzewie składni. Klasa pochodna zastępuje metody wywoływane dla określonych węzłów, które Cię interesują. W takim przypadku jesteś zainteresowany `using` dowolną dyrektywą. Oznacza to, że <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> należy zastąpić metodę. Jeden argument do tej <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> metody jest obiektem. Jest to ważna zaleta korzystania z odwiedzających: nazywają zastąpione metody z argumentami już oddanych do określonego typu węzła. Klasa <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax?displayProperty=nameWithType> ma <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.Name> właściwość, która przechowuje nazwę importowanego obszaru nazw. Jest to <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>. Dodaj następujący kod <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor.VisitUsingDirective(Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax)> w zastąpieniu:

[!code-csharp[Examine using nodes for the System namespace](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/UsingCollector.cs#5 "Examine all using nodes for the System namespace.")]

Podobnie jak we wcześniejszym przykładzie, dodano wiele `WriteLine` instrukcji, aby pomóc w zrozumieniu tej metody. Można zobaczyć, kiedy jest wywoływana i jakie argumenty są przekazywane do niego za każdym razem.

Na koniec należy dodać dwa wiersze `UsingCollector` kodu, aby utworzyć i go odwiedzić `using` węzeł główny, zbierając wszystkie instrukcje. Następnie dodaj `foreach` pętlę, aby `using` wyświetlić wszystkie instrukcje znalezione przez moduł zbierający:

[!code-csharp[Create the UsingCollector and visit the root node.](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxQuickStart/SyntaxWalker/Program.cs#6 "Create the UsingCollector and visit the root node.")]

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

Gratulacje! Interfejs **API składni** został użyty do zlokalizowania określonych rodzajów instrukcji c# i deklaracji w kodzie źródłowym języka C#.
