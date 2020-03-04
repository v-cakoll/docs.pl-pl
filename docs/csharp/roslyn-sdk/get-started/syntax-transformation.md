---
title: Wprowadzenie do transformacji składni (interfejsy API Roslyn)
description: Wprowadzenie do przechodzenia, wykonywania zapytań i eksplorowania drzew składni.
ms.date: 06/01/2018
ms.custom: mvc
ms.openlocfilehash: 5045dca839daba1070b34720e72cc9c4f7b94828
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240613"
---
# <a name="get-started-with-syntax-transformation"></a>Wprowadzenie do transformacji składni

W tym samouczku przedstawiono koncepcje i techniki omówione w temacie [Rozpoczynanie pracy z analizą składni](syntax-analysis.md) i rozpoczynanie pracy z przewodnikiem Szybki Start [analizy semantycznej](semantic-analysis.md) . Jeśli jeszcze tego nie zrobiono, przed rozpoczęciem tego procesu należy wykonać te Przewodniki Szybki Start.

W tym przewodniku szybki start przedstawiono techniki tworzenia i przekształcania drzew składni. W połączeniu z technikami, które znasz w poprzednich przewodnikach Szybki Start, tworzysz pierwsze Refaktoryzacja wiersza polecenia.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

## <a name="immutability-and-the-net-compiler-platform"></a>Niezmienności i platforma kompilatora .NET

**Niezmienności** to podstawowy cechą platformy kompilatora .NET. Niezmienne struktury danych nie mogą być zmieniane po ich utworzeniu. Niezmienne struktury danych mogą być bezpiecznie udostępniane i analizowane przez wielu użytkowników jednocześnie. Nie ma żadnych zagrożeń, które jeden z nich ma wpływ na inny sposób na nieprzewidywalny sposób. Analizator nie wymaga blokad ani innych miar współbieżności. Ta reguła ma zastosowanie do drzew składni, kompilacji, symboli, modeli semantycznych i każdej innej obsługiwanej struktury danych. Zamiast modyfikować istniejące struktury, interfejsy API tworzą nowe obiekty na podstawie określonych różnic do starych. To pojęcie jest stosowane do drzew składni w celu utworzenia nowych drzew przy użyciu transformacji.

## <a name="create-and-transform-trees"></a>Tworzenie i przekształcanie drzew

Do przekształceń składni należy wybrać jedną z dwóch strategii. **Metody fabryki** są najlepiej używane podczas wyszukiwania określonych węzłów w celu zastąpienia lub określonych lokalizacji, w których ma zostać wstawiony nowy kod. Odwzorowania najlepiej sprawdzają **się w** przypadku, gdy chcesz skanować cały projekt dla wzorców kodu, które chcesz zastąpić.

### <a name="create-nodes-with-factory-methods"></a>Tworzenie węzłów przy użyciu metod fabrycznych

Pierwsze przekształcenie składni ilustruje metody fabryki. Zamierzasz zastąpić instrukcję `using System.Collections;` instrukcją `using System.Collections.Generic;`. Ten przykład ilustruje sposób tworzenia <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxNode?displayProperty=nameWithType> obiektów przy użyciu metod fabryki <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType>. Dla każdego rodzaju **węzła**, **tokenu**lub **kwizy** istnieje metoda fabryki, która tworzy wystąpienie tego typu. Tworzysz drzewa składniowe, tworząc węzły hierarchicznie w sposób dolny. Następnie Przekształć istniejący program, zastępując istniejące węzły nowym drzewem utworzonym przez użytkownika.

Uruchom program Visual Studio i Utwórz nowy C# projekt narzędzia do **analizy kodu autonomicznego** . W programie Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt** , aby wyświetlić okno dialogowe Nowy projekt. W obszarze **rozszerzalność** **Visual C#**  > wybierz **Narzędzie do analizy kodu autonomicznego**. Ten przewodnik Szybki Start ma dwa przykładowe projekty, więc Nazwij rozwiązanie **SyntaxTransformationQuickStart**i Nadaj projektowi nazwę **ConstructionCS**. Kliknij przycisk **OK**.

Ten projekt używa metod klasy <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory?displayProperty=nameWithType> do konstruowania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType> reprezentujących `System.Collections.Generic` przestrzeni nazw.

Dodaj następującą dyrektywę using na początku pliku `Program.cs`, aby zaimportować metody fabryki klasy <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory> i metody <xref:System.Console>, aby można było ich używać później bez ich kwalifikowania:

[!code-csharp[import the SyntaxFactory class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#StaticUsings "import the Syntax Factory class and the System.Console class")]

Utworzysz **węzły składni nazw** w celu skompilowania drzewa, które reprezentuje instrukcję `using System.Collections.Generic;`. <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax> jest klasą bazową dla czterech typów nazw, które są C#wyświetlane w. Można napisać te cztery typy nazw razem, aby utworzyć dowolną nazwę, która może być wyświetlana w C# języku:

* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax?displayProperty=nameWithType>, która reprezentuje proste nazwy pojedynczego identyfikatora, takie jak `System` i `Microsoft`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.GenericNameSyntax?displayProperty=nameWithType>, która reprezentuje typ ogólny lub nazwę metody, np. `List<int>`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax?displayProperty=nameWithType>, która reprezentuje kwalifikowaną nazwę formularza `<left-name>.<right-identifier-or-generic-name>`, takich jak `System.IO`.
* <xref:Microsoft.CodeAnalysis.CSharp.Syntax.AliasQualifiedNameSyntax?displayProperty=nameWithType>, która reprezentuje nazwę przy użyciu aliasu zewnętrznego zestawu, takiego jak `LibraryV2::Foo`.

Użyj metody <xref:Microsoft.CodeAnalysis.CSharp.SyntaxFactory.IdentifierName(System.String)>, aby utworzyć węzeł <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>. Dodaj następujący kod w metodzie `Main` w `Program.cs`:

[!code-csharp[create the system identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateIdentifierName "Create and display the system name identifier")]

Poprzedni kod tworzy obiekt <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> i przypisuje go do zmiennej `name`. Wiele interfejsów API Roslyn zwraca klasy bazowe, aby ułatwić pracę z powiązanymi typami. Zmienna `name`, <xref:Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax>, może być ponownie użyta podczas tworzenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nie używaj wnioskowania o typie podczas tworzenia przykładu. Ten krok zostanie zautomatyzowany w tym projekcie.

Nazwa została utworzona. Teraz można utworzyć więcej węzłów w drzewie, tworząc <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Nowe drzewo używa `name` po lewej stronie nazwy i nowego <xref:Microsoft.CodeAnalysis.CSharp.Syntax.IdentifierNameSyntax> przestrzeni nazw `Collections` jako prawej strony <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax>. Dodaj następujący kod do pliku `program.cs`:

[!code-csharp[create the collections identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateQualifiedIdentifierName "Build the System.Collections identifier")]

Uruchom ponownie kod i Zobacz wyniki. Tworzysz drzewo węzłów, które reprezentują kod. Ten wzorzec będzie kontynuowany w celu skompilowania <xref:Microsoft.CodeAnalysis.CSharp.Syntax.QualifiedNameSyntax> `System.Collections.Generic`przestrzeni nazw. Dodaj następujący kod do pliku `Program.cs`:

[!code-csharp[create the full identifier](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateFullNamespace "Build the System.Collections.Generic identifier")]

Ponownie uruchom program, aby zobaczyć, że utworzono drzewo dla kodu, który ma zostać dodany.

### <a name="create-a-modified-tree"></a>Tworzenie zmodyfikowanego drzewa

Skompilowano małe drzewo składni zawierające jedną instrukcję. Interfejsy API do tworzenia nowych węzłów są właściwym wyborem do tworzenia pojedynczych instrukcji lub innych małych bloków kodu. Jednak aby utworzyć więcej bloków kodu, należy użyć metod, które zastępują węzły lub wstawiają węzły do istniejącego drzewa. Należy pamiętać, że drzewa składni są niezmienne. **Interfejs API składni** nie udostępnia żadnego mechanizmu modyfikacji istniejącego drzewa składni po konstrukcji. Zamiast tego dostarcza metody, które tworzą nowe drzewa na podstawie zmian istniejących. Metody `With*` są definiowane w konkretnych klasach, które pochodzą od <xref:Microsoft.CodeAnalysis.SyntaxNode> lub w metodach rozszerzających zadeklarowanych w klasie <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions>. Te metody tworzą nowy węzeł przez zastosowanie zmian do właściwości podrzędnych istniejącego węzła. Ponadto Metoda rozszerzenia <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> może służyć do zastępowania węzła podrzędnego w poddrzewie. Ta metoda aktualizuje także element nadrzędny tak, aby wskazywał nowo utworzony element podrzędny i powtarza ten proces w całym drzewie — proces znany jako _odwirowanie_ drzewa.

Następnym krokiem jest utworzenie drzewa, które reprezentuje cały (mały) program, a następnie zmodyfikuje go. Dodaj następujący kod na początku klasy `Program`:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#DeclareSampleCode "Create a tree that represents a small program")]

> [!NOTE]
> Przykładowy kod używa `System.Collections` przestrzeni nazw, a nie przestrzeni nazw `System.Collections.Generic`.

Następnie Dodaj następujący kod na dole metody `Main`, aby przeanalizować tekst i utworzyć drzewo:

[!code-csharp[create a parse tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#CreateParseTree "Create a tree that represents a small program")]

W tym przykładzie zastosowano metodę <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)?displayProperty=NameWithType>, aby zastąpić nazwę w węźle <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> z tą, która została skonstruowana w poprzednim kodzie.

Utwórz nowy węzeł <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax> przy użyciu metody <xref:Microsoft.CodeAnalysis.CSharp.Syntax.UsingDirectiveSyntax.WithName(Microsoft.CodeAnalysis.CSharp.Syntax.NameSyntax)>, aby zaktualizować nazwę `System.Collections` nazwą utworzoną w poprzednim kodzie. Dodaj następujący kod na końcu metody `Main`:

[!code-csharp[create a new subtree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#BuildNewUsing "Create the subtree with the replaced namespace")]

Uruchom program i uważnie Obejrzyj dane wyjściowe. `newusing` nie została umieszczona w drzewie głównym. Oryginalne drzewo nie zostało zmienione.

Dodaj następujący kod przy użyciu metody rozszerzenia <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A>, aby utworzyć nowe drzewo. Nowe drzewo jest wynikiem zamiany istniejącego importu z zaktualizowanym węzłem `newUsing`. To nowe drzewo jest przypisywane do istniejącej zmiennej `root`:

[!code-csharp[create a new root tree](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/ConstructionCS/Program.cs#TransformTree "Create the transformed root tree with the replaced namespace")]

Ponownie uruchom program. Tym razem drzewo już prawidłowo importuje `System.Collections.Generic` przestrzeni nazw.

### <a name="transform-trees-using-syntaxrewriters"></a>Przekształcanie drzew przy użyciu `SyntaxRewriters`

Metody `With*` i <xref:Microsoft.CodeAnalysis.SyntaxNodeExtensions.ReplaceNode%2A> zapewniają wygodną metodę przekształcenia poszczególnych gałęzi drzewa składni. Klasa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> wykonuje wiele transformacji w drzewie składni. Klasa <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter?displayProperty=nameWithType> jest podklasą <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxVisitor%601?displayProperty=nameWithType>. <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> stosuje transformację do określonego typu <xref:Microsoft.CodeAnalysis.SyntaxNode>. Przekształcenia można zastosować do wielu typów <xref:Microsoft.CodeAnalysis.SyntaxNode> obiektów, wszędzie tam, gdzie są wyświetlane w drzewie składni. Drugi projekt w tym przewodniku szybki start tworzy refaktoryzację wiersza polecenia, która usuwa jawne typy w deklaracjach zmiennych lokalnych w dowolnym miejscu, w którym można użyć wnioskowania o typie.

Utwórz nowy C# projekt **Narzędzia do analizy kodu autonomicznego** . W programie Visual Studio kliknij prawym przyciskiem myszy węzeł `SyntaxTransformationQuickStart` rozwiązanie. Wybierz pozycję **dodaj** > **Nowy projekt** , aby wyświetlić **okno dialogowe Nowy projekt**. W obszarze **rozszerzalność** **Visual C#**  > wybierz pozycję **Narzędzie do analizy kodu autonomicznego**. Nazwij projekt `TransformationCS` a następnie kliknij przycisk OK.

Pierwszym krokiem jest utworzenie klasy, która pochodzi od <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter> do wykonywania transformacji. Dodaj nowy plik klasy do projektu. W programie Visual Studio wybierz pozycję **projekt** > **Dodaj klasę..** .. W oknie dialogowym **Dodaj nowy element** wpisz `TypeInferenceRewriter.cs` jako nazwę pliku.

Dodaj następujące dyrektywy using do pliku `TypeInferenceRewriter.cs`:

[!code-csharp[add necessary usings](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#AddUsings "Add required usings")]

Następnie ustaw klasę `TypeInferenceRewriter` klasy <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter>:

[!code-csharp[add base class](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BaseClass "Add base class")]

Dodaj następujący kod, aby zadeklarować prywatne pole tylko do odczytu, aby pomieścić <xref:Microsoft.CodeAnalysis.SemanticModel> i zainicjować go w konstruktorze. To pole będzie potrzebne później, aby określić, gdzie można używać wnioskowania o typie:

[!code-csharp[initialize members](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Construction "Declare and initialize member variables")]

Zastąp metodę <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)>:

```csharp
public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)
{

}
```

> [!NOTE]
> Wiele interfejsów API Roslyn deklaruje typy zwracane, które są klasami bazowymi rzeczywistych zwracanych typów środowiska uruchomieniowego. W wielu scenariuszach jeden rodzaj węzła może być zastępowany przez inny rodzaj węzła całkowicie lub nawet usunięty. W tym przykładzie metoda <xref:Microsoft.CodeAnalysis.CSharp.CSharpSyntaxRewriter.VisitLocalDeclarationStatement(Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax)> zwraca <xref:Microsoft.CodeAnalysis.SyntaxNode>, a nie typ pochodny <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>. Ten przepisano nowy węzeł <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> w oparciu o istniejący.

Ten przewodnik Szybki Start obsługuje deklaracje zmiennych lokalnych. Można ją rozciągnąć do innych deklaracji, takich jak pętle `foreach`, pętle `for`, wyrażenia LINQ i wyrażenia lambda. Ponadto ten przekształcenie przekształci tylko deklaracje najprostszej formy:

```csharp
Type variable = expression;
```

Jeśli chcesz samodzielnie poznać swoją pracę, rozważ rozszerzenie gotowej próbki dla tych typów deklaracji zmiennych:

```csharp
// Multiple variables in a single declaration.
Type variable1 = expression1,
     variable2 = expression2;
// No initializer.
Type variable;
```

Dodaj następujący kod do treści metody `VisitLocalDeclarationStatement`, aby pominąć Zapisywanie tych form deklaracji:

[!code-csharp[exclude other declarations](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#Exclusions "Exclude variables declarations not processed by this sample")]

Metoda wskazuje, że nie następuje ponowne zapisywanie, zwracając niemodyfikowany parametr `node`. Jeśli żaden z tych wyrażeń `if` nie ma wartości true, węzeł reprezentuje możliwą deklarację z inicjalizacją. Dodaj te instrukcje, aby wyodrębnić nazwę typu określoną w deklaracji i powiązać ją przy użyciu pola <xref:Microsoft.CodeAnalysis.SemanticModel>, aby uzyskać symbol typu:

[!code-csharp[extract type name](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ExtractTypeSymbol "Extract the type name specified by the declaration")]

Teraz Dodaj tę instrukcję, aby powiązać wyrażenie inicjatora:

[!code-csharp[bind initializer](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#BindInitializer "Bind the initializer expressions")]

Na koniec Dodaj następującą instrukcję `if`, aby zastąpić istniejącą nazwę typu słowem kluczowym `var`, jeśli typ wyrażenia inicjatora pasuje do określonego typu:

[!code-csharp[ReplaceNode](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/TypeInferenceRewriter.cs#ReplaceNode "Replace the initializer node")]

Warunek jest wymagany, ponieważ deklaracja może rzutować wyrażenie inicjatora na klasę bazową lub interfejs. Jeśli jest to wymagane, typy po lewej stronie i prawo przypisania nie pasują do siebie. Usunięcie jawnego typu w takich przypadkach spowoduje zmianę semantyki programu. `var` jest określony jako identyfikator zamiast słowa kluczowego, ponieważ `var` jest kontekstowym słowem kluczowym. Kwizy wiodące i końcowe (biały znak) są transferowane ze starej nazwy typu do słowa kluczowego `var`, aby zachować biały odstęp i wcięcia. Nie można użyć `ReplaceNode`, a nie `With*` do przekształcenia <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax>, ponieważ nazwa typu jest rzeczywiście grandchild instrukcji deklaracji.

Zakończono `TypeInferenceRewriter`. Teraz wróć do pliku `Program.cs`, aby zakończyć przykład. Utwórz <xref:Microsoft.CodeAnalysis.Compilation> testowy i uzyskaj <xref:Microsoft.CodeAnalysis.SemanticModel> z niego. Użyj tej <xref:Microsoft.CodeAnalysis.SemanticModel>, aby wypróbować `TypeInferenceRewriter`. Ten krok należy wykonać jako ostatni. W międzyczasie Zadeklaruj zmienną zastępczą reprezentującą kompilację testu:

[!code-csharp[DeclareCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#DeclareTestCompilation "Declare the test compilation")]

Po przeprowadzeniu chwily powinien pojawić się komunikat o błędzie pojawia się, gdy nie istnieje metoda `CreateTestCompilation`. Naciśnij **klawisze CTRL + kropka** , aby otworzyć żarówkę, a następnie naciśnij klawisz ENTER, aby wywołać polecenie **Generuj metodę zastępczą** . To polecenie spowoduje wygenerowanie w klasie `Program` klasy zastępczej metody `CreateTestCompilation`. Wróć do tej metody, aby uzupełnić ją później:

![C#Generuj metodę na podstawie użycia](./media/syntax-transformation/generate-from-usage.png)

Napisz Poniższy kod, aby wykonać iterację poszczególnych <xref:Microsoft.CodeAnalysis.SyntaxTree> w <xref:Microsoft.CodeAnalysis.Compilation>testowych. Dla każdej z nich zainicjuj nowe `TypeInferenceRewriter` z <xref:Microsoft.CodeAnalysis.SemanticModel> dla tego drzewa:

[!code-csharp[IterateTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#IterateTrees "Iterate all the source trees in the test compilation")]

Wewnątrz utworzonej instrukcji `foreach` Dodaj następujący kod, aby przeprowadzić transformację w każdym drzewie źródłowym. Ten kod warunkowo zapisuje nowe przekształcone drzewo w przypadku dokonania edycji. Obiekt modyfikujący powinien modyfikować tylko drzewo, jeśli napotka co najmniej jedną deklarację zmiennej lokalnej, która mogłaby zostać uproszczona przy użyciu wnioskowania o typie:

[!code-csharp[TransformTrees](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#TransformTrees "Transform and save any trees that are modified by the rewriter")]

W kodzie `File.WriteAllText` powinny być widoczne zygzaks. Wybierz żarówkę i Dodaj niezbędną instrukcję `using System.IO;`.

Prawie gotowe! Po lewej stronie jest dostępny jeden krok: Tworzenie <xref:Microsoft.CodeAnalysis.Compilation>testowych. Ponieważ w tym przewodniku Szybki Start nie używasz wnioskowania o typie w ogóle, nastąpiło idealne przypadki testowe. Niestety, tworzenie kompilacji z pliku C# projektu wykracza poza zakres tego przewodnika. Jednak mamy nadzieję, że wcześniej zostały podane wskazówki. Zastąp zawartość metody `CreateTestCompilation` poniższym kodem. Tworzy kompilację testową, która w sposób niezgodny z projektem opisanym w tym przewodniku szybki start:

[!code-csharp[CreateTestCompilation](../../../../samples/snippets/csharp/roslyn-sdk/SyntaxTransformationQuickStart/TransformationCS/Program.cs#CreateTestCompilation "Create a test compilation using the code written for this quickstart.")]

Przetniej palce i Uruchom projekt. W programie Visual Studio wybierz kolejno opcje **debuguj** > **Rozpocznij debugowanie**. Powinien zostać wyświetlony monit przez program Visual Studio o zmianę plików w projekcie. Kliknij przycisk "**tak na wszystkie**", aby ponownie załadować zmodyfikowane pliki. Sprawdź je, aby obserwować ich wspaniałe. Zwróć uwagę na to, ile wyraźniejszy kod wygląda bez wszystkich jawnych i nadmiarowych specyfikatorów typów.

Gratulacje! **Interfejsy API kompilatora** są używane do tworzenia własnych refaktoryzacji, które przeszukują wszystkie pliki w C# projekcie dla określonych wzorców składni, analizuje semantykę kodu źródłowego, który jest zgodny z tymi wzorcami, i przekształca je. Jesteś teraz oficjalnie gotowym do refaktoryzacji autorem.
