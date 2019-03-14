---
title: Wprowadzenie do składni przekształcania (interfejsy API Roslyn)
description: Wprowadzenie do przechodzenie przez wykonywanie zapytań i zalet drzewa składni.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 3ca6ba19f84366b4e1f74ac4a0dea1edef3cee05
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57788443"
---
# <a name="get-started-with-syntax-transformation"></a>Wprowadzenie do składni przekształcania

Ten samouczek opiera się na pojęcia i techniki przedstawione w [Rozpoczynanie pracy z usługą analiza składni](syntax-analysis.md) i [wprowadzenie do analizy semantycznej](semantic-analysis.md) przewodników Szybki Start. Jeśli jeszcze nie, należy wykonać te przewodniki Szybki Start, przed rozpoczęciem tego.

W tym przewodniku Szybki Start możesz eksplorować techniki służące do tworzenia i przekształcanie drzewa składni. W połączeniu z technik, które przedstawiono w poprzednim przewodników Szybki Start możesz utworzyć Twoje pierwsze refaktoryzacji wiersza polecenia!

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Niezmienność i platformie kompilatora .NET

**Niezmienność** jest podstawowe główną o platformę kompilatora programu .NET. Nie można zmienić struktury niezmienialnymi danymi, po ich utworzeniu. Struktury danych niezmienne może być bezpiecznie udostępniane i analizowane przez wielu odbiorców jednocześnie. Nie ma ryzyka tego jednego konsumenta wpływ na inny w właściwie nieprzewidywalnych sposobów. Twoje Analizator nie musi, blokady lub innych środków współbieżności. Ta zasada ma zastosowanie do drzewa składni, kompilacje, symbole, modeli semantycznych i co inne struktury danych, które wystąpić. Zamiast modyfikowania istniejących struktur, interfejsów API tworzyć nowe obiekty, w zależności od określonego różnice, by starych. Pojęcie to dotyczy drzewa składni do utworzenia nowego drzewa za pomocą przekształcenia.

## <a name="create-and-transform-trees"></a>Tworzenie i przekształcanie drzew

Możesz wybrać jedną z dwóch strategii dla przekształceń składni. **Metodami Factory** najlepiej są używane, gdy szukasz określonych węzłów w celu zastąpienia lub określone lokalizacje, w którym chcesz wstawić nowy kod. **Rewriters** są najlepiej, gdy użytkownik chce całego projektu podczas skanowania w poszukiwaniu wzorców kodu, które mają zostać zamienione.

### <a name="create-nodes-with-factory-methods"></a>Utwórz węzły z metodami factory

Pierwsza transformacja składnia pokazuje, metodach fabryki. Zamierzasz zamienić `using System.Collections;` instrukcję, określając `using System.Collections.Generic;` instrukcji. W tym przykładzie przedstawiono, jak utworzyć <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> obiektów przy użyciu <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metodach fabryki. Dla każdego rodzaju elementu **węzła**, **tokenu**, lub **elementy towarzyszące składni** nie istnieje metoda fabryki, który tworzy wystąpienie tego typu. Można utworzyć drzewa składni za tworzenie węzłów hierarchicznie w czasie od dołu do góry. Następnie można przekształcać istniejące program można zastępując istniejące węzły nowego drzewa, które zostały utworzone.

Uruchom program Visual Studio i Utwórz nowy język C# **narzędzie do analizy kodu autonomicznego** projektu. W programie Visual Studio, wybierz **pliku** > **New** > **projektu** Aby wyświetlić okno dialogowe Nowy projekt. W obszarze **Visual C#** > **rozszerzalności** wybierz **narzędzie do analizy kodu autonomicznego**. Ten przewodnik Szybki Start zawiera dwa projekty przykładu, więc nazwa rozwiązania **SyntaxTransformationQuickStart**i nazwij projekt **ConstructionCS**. Kliknij przycisk **OK**.

Ten projekt używa <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> metody do konstruowania klasy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> reprezentujący `System.Collections.Generic` przestrzeni nazw.

Dodaj następujące za pomocą dyrektywy do góry `Program.cs` plik do zaimportowania metod fabryki <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> klasy i metody <xref:System.Console> tak, aby można je później użyć bez ich kwalifikowania:

[!code-csharp[import the SyntaxFactory class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Utworzysz **nazwy węzłów składni** tworzyć drzewo, które reprezentuje `using System.Collections.Generic;` instrukcji. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> jest klasą bazową dla cztery typy nazw, które są wyświetlane w języku C#. Te cztery typy nazw, aby utworzyć dowolną nazwę, która może pojawić się w języku C# redagowania:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, która reprezentuje prostym identyfikatorem jednej nazwy, takie jak `System` i `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, która reprezentuje takich jak nazwy typu lub metody rodzajowej `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, która reprezentuje kwalifikowana nazwa formularza `<left-name>.<right-identifier-or-generic-name>` takich jak `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, która reprezentuje nazwę za pomocą zestawu extern alias takich `LibraryV2::Foo`.

Możesz użyć <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)> metodę w celu utworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> węzła. Dodaj następujący kod w swojej `Main` method in Class metoda `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Powyższy kod tworzy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> obiektu, a następnie przypisuje go do zmiennej `name`. Wiele interfejsów API Roslyn zwracają klasy bazowe w celu ułatwienia pracy z powiązanych typów. Zmienna `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, mogą zostać ponownie użyte podczas tworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nie należy używać wnioskowania o typie, podczas tworzenia przykładu. Będziesz zautomatyzować tego kroku w tym projekcie.

Utworzono nazwę. Teraz nadszedł czas na utworzenie większą liczbę węzłów w drzewie, tworząc <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Używa nowego drzewa `name` jako po lewej stronie nazwy i nowego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> dla `Collections` obszaru nazw po prawej stronie <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Dodaj następujący kod do `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Ponownie uruchom kod i wyświetlić wyniki. W przypadku tworzenia drzewa węzłów, która przedstawia kod. Nadal będzie tego wzorca, aby tworzyć <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> dla przestrzeni nazw `System.Collections.Generic`. Dodaj następujący kod do `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Uruchom program ponownie, aby zobaczyć, że po kompilacji drzewa dla kodu w celu dodania.

### <a name="create-a-modified-tree"></a>Utwórz zmodyfikowane drzewa

Gdy masz utworzoną drzewo składni małe, które zawiera jedną instrukcję. Interfejsy API w celu utworzenia nowych węzłów są właściwym wyborem, aby utworzyć pojedyncze instrukcje lub innych małych blokach kodu. Jednak tworzenie większych blokach kodu, należy użyć metody Zastąp węzłów lub wstawianie węzłów na istniejącym drzewie. Należy pamiętać, że drzewa składni są niezmienne. **API składni** nie zapewnia żadnych mechanizm do modyfikowania istniejących drzewo składni po konstrukcji. Zamiast tego zawiera metody, które tworzą nowe drzewa, na podstawie zmian do istniejących. `With*` metody są zdefiniowane w klas konkretnych wywodzących się z <xref:Microsoft.CodeAnalysis.SyntaxNode> lub rozszerzenia metod zadeklarowanych w <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions> klasy. Te metody Utwórz nowy węzeł, wprowadzając zmiany w istniejących węzłów podrzędnych właściwości. Ponadto <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> — metoda rozszerzenia może służyć do zastąpienia węzeł podrzędny w poddrzewa. Ta metoda również aktualizuje element nadrzędny, aby wskazać nowo utworzony element podrzędny i powtarza ten proces w górę całe drzewo — proces ten jest znany jako _re spining_ drzewa.

Następnym krokiem jest utworzyć drzewo, który reprezentuje cały (mały) program, a następnie zmodyfikować go. Dodaj następujący kod na początku `Program` klasy:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Przykładowy kod używa `System.Collections` przestrzeni nazw i nie `System.Collections.Generic` przestrzeni nazw.

Następnie dodaj następujący kod do dolnej części `Main` metody, które można przeanalizować tekstu i utworzyć drzewo:

[!code-csharp[create a parse tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

W tym przykładzie użyto <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType> metodę, aby zastąpić nazwę w <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> węzłów na zestaw zbudowany w poprzednim kodzie.

Utwórz nową <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> za pomocą węzła <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)> metodę, aby zaktualizować `System.Collections` nazwę nazwą utworzonego w poprzednim kodzie. Dodaj następujący kod na końcu `Main` metody:

[!code-csharp[create a new subtree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Uruchom program i sprawdź dokładnie dane wyjściowe. `newusing` Nie została umieszczona w drzewie katalogu głównego. Oryginalny drzewa nie został zmodyfikowany.

Dodaj następujący kod za pomocą <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metodę rozszerzenia, aby utworzyć nowe drzewo. Nowe drzewo jest wynikiem zastępując istniejące importu zaktualizowanego `newUsing` węzła. Przypisywanie tego nowego drzewa do istniejących `root` zmiennej:

[!code-csharp[create a new root tree](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Ponownie uruchom program. Tym razem drzewa teraz poprawnie importuje `System.Collections.Generic` przestrzeni nazw.

### <a name="transform-trees-using-syntaxrewriters"></a>Przekształcanie drzewa za pomocą `SyntaxRewriters`

`With*` i <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> metody zapewniają wygodny sposób przekształcania poszczególnych gałęzi drzewa składni. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Klasy wykonuje wiele przekształceń na drzewie składni. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> Klasy jest podklasą <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> Stosuje przekształcenia do określonego typu <xref:Microsoft.CodeAnalysis.SyntaxNode>. Przekształcenia można zastosować do wielu typów <xref:Microsoft.CodeAnalysis.SyntaxNode> obiekty wszędzie tam, gdzie są wyświetlane w drzewie składni. Drugi projekt, w tym przewodniku Szybki Start tworzy wiersza polecenia refaktoryzacji, która usuwa jawnie typów w deklaracjach zmiennych lokalnych, może być używane tam, gdzie wnioskowanie o typie.

Utwórz nowy język C# **narzędzie do analizy kodu autonomicznego** projektu. W programie Visual Studio, kliknij prawym przyciskiem myszy `SyntaxTransformationQuickStart` węzła rozwiązania. Wybierz **Dodaj** > **nowy projekt** do wyświetlenia **okna dialogowego Nowy projekt**. W obszarze **Visual C#** > **rozszerzalności**, wybierz **narzędzie do analizy kodu autonomicznego**. Nazwij swój projekt `TransformationCS` i kliknij przycisk OK.

Pierwszym krokiem jest utworzenie klasy, która pochodzi od klasy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> do wykonania przekształceń. Dodaj nowy plik klasy do projektu. W programie Visual Studio, wybierz **projektu** > **Dodaj klasę...** . W **Dodaj nowy element** typ okna dialogowego `TypeInferenceRewriter.cs` jako nazwę pliku.

Dodaj następujące dyrektywy using `TypeInferenceRewriter.cs` pliku:

[!code-csharp[add necessary usings](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Następnie upewnij `TypeInferenceRewriter` rozszerzyć klasy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> klasy:

[!code-csharp[add base class](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Dodaj następujący kod, aby zadeklarować prywatnego pola tylko do odczytu do przechowywania <xref:Microsoft.CodeAnalysis.SemanticModel> i zainicjować go w konstruktorze. Będą potrzebne później, aby określić, gdzie można wnioskowanie o typie:

[!code-csharp[initialize members](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Zastąp <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metody:

```C#
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Wiele interfejsów API Roslyn Zadeklaruj typy zwracane, które są klasy bazowe typy rzeczywiste środowiska uruchomieniowego, zwracany. W wielu scenariuszach jeden rodzaj węzła może być zastąpiony przez inny rodzaj węzła całkowicie — lub nawet usunąć. W tym przykładzie <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> metoda zwraca <xref:Microsoft.CodeAnalysis.SyntaxNode>, a nie typ pochodny <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Ta dysków zwraca nowy <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> węzła oparte na istniejącą grupę.

Ten przewodnik szybkiego startu obsługuje deklaracje zmiennych lokalnych. Można rozszerzyć do innych deklaracji takich jak `foreach` pętli, `for` pętle, wyrażenia LINQ i wyrażeń lambda. Ponadto to dysków spowoduje przekształcenie tylko deklaracje najprostszej postaci:

```csharp
Type variable = expression;
```

Jeśli chcesz rozpocząć eksplorowanie na własną, należy wziąć pod uwagę rozszerzanie Zakończono przykład tego rodzaju deklaracji zmiennych:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Dodaj następujący kod do treści `VisitLocalDeclarationStatement` metodę, aby pominąć ponowne napisanie te rodzaje deklaracje:

[!code-csharp[exclude other declarations](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metody oznacza, że nie ponownego zapisywania adresów odbywa się, zwracając `node` parametru w niezmienionej postaci. Jeśli żadna z tych `if` wyrażenia mają wartość true, węzeł reprezentuje możliwe deklaracji z inicjowania. Dodaj tych instrukcji do wyodrębnienia nazwę typu, określonym w deklaracji i powiąż go przy użyciu <xref:Microsoft.CodeAnalysis.SemanticModel> pola, aby uzyskać symbol typu:

[!code-csharp[extract type name](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Teraz Dodaj tej instrukcji, aby powiązać wyrażenia inicjatora:

[!code-csharp[bind initializer](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Na koniec należy dodać następujące `if` instrukcję, aby zastąpić istniejącą nazwę typu z `var` — słowo kluczowe, jeśli określony typ pasuje do typu wyrażenia inicjatora:

[!code-csharp[ReplaceNode](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Warunkowe jest wymagana, ponieważ deklaracja może oddać wyrażenia inicjatora do klasy bazowej lub interfejsu. W razie potrzeby, typy po lewej i prawej stronie przypisania nie są zgodne. Usuwanie typu jawnego w tych przypadkach zmieniłby semantykę programu. `var` Określony identyfikator zamiast słowa kluczowego, ponieważ `var` jest kontekstowym słowem kluczowym. Początkowe i końcowe elementy towarzyszące składni (biały) są przekazywane z starej nazwy typu `var` — słowo kluczowe do zachowania biały znak pionowej i wcięcia. Jest łatwiejszy w obsłudze `ReplaceNode` zamiast `With*` do przekształcania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> ponieważ nazwa typu jest faktycznie podwójnym instrukcji deklaracji.

Masz Zakończono `TypeInferenceRewriter`. Teraz wróć do usługi `Program.cs` pliku, aby zakończyć w przykładzie. Tworzenie testu <xref:Microsoft.CodeAnalysis.Compilation> i uzyskać <xref:Microsoft.CodeAnalysis.SemanticModel> z niego. Użycie <xref:Microsoft.CodeAnalysis.SemanticModel> do wypróbowania usługi `TypeInferenceRewriter`. Należy to zrobić w tym kroku ostatnio. W międzyczasie zadeklarować zmienną symbol zastępczy reprezentujący kompilacji testu:

[!code-csharp[DeclareCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po wstrzymaniu chwilę, powinien zostać wyświetlony wężyk błędów, które pojawiają się raporty nie `CreateTestCompilation` istnieje metoda. Naciśnij klawisz **Ctrl + kropka** Otwórz ikony żarówki, a następnie naciśnij klawisz Enter, aby wywołać **generowania szkieletu metody** polecenia. To polecenie spowoduje wygenerowanie szkieletu metody dla `CreateTestCompilation` method in Class metoda `Program` klasy. Można będzie wrócić do wypełnienia w tej metodzie później:

![C# Generowanie metody z użycia](./media/syntax-transformation/generate-from-usage.png)

Napisać następujący kod w celu iteracyjnego <xref:Microsoft.CodeAnalysis.SyntaxTree> w teście <xref:Microsoft.CodeAnalysis.Compilation>. Dla każdego z nich, zainicjować nowy `TypeInferenceRewriter` z <xref:Microsoft.CodeAnalysis.SemanticModel> dla tego drzewa:

[!code-csharp[IterateTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Wewnątrz `foreach` instrukcji, które zostały utworzone, Dodaj następujący kod do wykonania przekształcenia w każdym drzewie źródła. Ten kod warunkowo zapisuje się nowego drzewa przekształcone, jeśli zostały wprowadzone zmiany. Twoje dysków powinny być modyfikowane tylko drzewo, jeśli wykryje nieważną co najmniej jeden lokalny deklaracji zmiennych, które można uproszczenie przy użyciu wnioskowanie o typie:

[!code-csharp[TransformTrees](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

Powinny być widoczne faliste linie w obszarze `File.WriteAllText` kodu. Wybierz żarówki, a następnie dodać niezbędne `using System.IO;` instrukcji.

Prawie gotowe! To po kroku po lewej: tworzenie testu <xref:Microsoft.CodeAnalysis.Compilation>. Ponieważ jeszcze nie używasz wnioskowania o typie w ogóle w tym przewodniku Szybki Start, czy ma on doskonałe przypadek testowy. Niestety tworzenie kompilacji z pliku projektu C# jest poza zakresem tego przewodnika. Ale na szczęście Jeśli wykonywano instrukcje uważnie, mamy nadzieję, że. Zastąp zawartość `CreateTestCompilation` metoda następującym kodem. Tworzy kompilacji testu, która odpowiada przypadkowo projektu opisanych w tym przewodniku Szybki Start:

[!code-csharp[CreateTestCompilation](../../../../samples/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Krzyżowe palcami i uruchomić projekt. W programie Visual Studio, wybierz **debugowania** > **Rozpocznij debugowanie**. Powinien pojawić się monit przez program Visual Studio, które zostały zmienione pliki w projekcie. Kliknij przycisk "**tak na wszystko**" Aby ponownie załadować zmodyfikowanych plików. Sprawdź je do obserwowania swojej funkcji w programie. Uwaga jak znacznie bardziej przejrzysty kod wygląda bez tych specyfikatorów typu jawnego i nadmiarowe.

Gratulacje! Wykorzystano **interfejsów API kompilatora** napisać własne refaktoryzacji, która wyszukuje wszystkie pliki w projekcie języka C# dla pewnych składni wzorców analizuje semantykę kodu źródłowego, który odpowiada tym wzorcom i przekształca je. Teraz masz oficjalnie refaktoryzacji Autor!
