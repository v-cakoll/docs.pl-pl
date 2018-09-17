---
title: Eksplorowanie kodu za pomocą wizualizatora składni Roslyn w programie Visual Studio
description: Wizualizatora składni obejmuje narzędzia wizualne Eksplorowanie modeli, które generuje kod w zestawie SDK platformy kompilatora .NET.
ms.date: 03/07/2018
ms.custom: mvc, vs-dotnet
ms.openlocfilehash: 97a058eed8c0babebd3a41ec91875bef83ac3527
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750209"
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Eksplorowanie kodu za pomocą wizualizatora składni Roslyn w programie Visual Studio

Ten artykuł zawiera omówienie narzędzia Syntax Visualizer, który jest dostarczany jako część platformy kompilatora .NET ("Roslyn") zestawu SDK. Wizualizatora składni jest oknem narzędzi, który ułatwia sprawdzanie i zapoznaj się z drzewa składni. Jest niezbędnego narzędzia, aby zrozumieć modeli dla kodu, który chcesz analizować. Jest również pomoc do debugowania podczas tworzenia własnych aplikacji przy użyciu platformy kompilatora .NET ("Roslyn") zestawu SDK. Otwórz to narzędzie, jak tworzenie swojej pierwszej analizatorów. Wizualizator pomaga zrozumieć te modele, które korzystają z interfejsów API. Można także użyć narzędzi, takich jak [SharpLab](https://sharplab.io) lub [LINQPad](https://www.linqpad.net/) inspekcji kodu i zrozumienie drzewa składni.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Zapoznaj się z pojęciami, używany w zestawie SDK platformy kompilatora .NET, zapoznając się [Przegląd](compiler-api-model.md) artykułu. Zawiera on wprowadzenie do drzewa składni, węzły, tokenów i elementy towarzyszące składni.

## <a name="syntax-visualizer"></a>Wizualizatora składni

**Syntax Visualizer** umożliwia inspekcję drzewa składni w pliku kodu C# lub VB w bieżącym oknie Edytor active w środowisku IDE programu Visual Studio. Wizualizator można uruchamiać przez kliknięcie **widoku** > **Windows inne** > **Syntax Visualizer**.  Można również użyć **Szybkie uruchamianie** narzędzi w prawym górnym rogu. Typ "składni", a polecenie, aby otworzyć **Syntax Visualizer** powinna zostać wyświetlona.

To polecenie otwiera Syntax Visualizer jako przestawne okna narzędzi. Jeśli nie masz z oknem edytora kodu, Otwórz ekran jest pusta, jak pokazano na poniższej ilustracji. 

![Okna narzędzi wizualizatora składni](media/syntax-visualizer/syntax-visualizer.png)

Dokowanie oknie tego narzędzia w dogodnym miejscu w programie Visual Studio, takie jak po lewej stronie. Wizualizator pokazuje informacje o bieżącym plikiem kodu.

Utwórz nowy projekt za pomocą **pliku** > **nowy projekt** polecenia. Można utworzyć projektu VB lub C#. Po otwarciu pliku głównego kodu dla tego projektu programu Visual Studio wizualizatora Wyświetla drzewo składni dla niego. Możesz otworzyć wszelkie istniejące języka C# / VB pliku w tym wystąpieniu programu Visual Studio i wizualizatora Wyświetla drzewo składni tego pliku. Jeśli masz wiele plików kodu, Otwórz w programie Visual Studio, wizualizatora Wyświetla drzewo składni dla pliku kodu aktualnie aktywny (kod plik, który ma fokus klawiatury.)

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Wizualizacja drzewo składni języka C#](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Wizualizacja drzewo składni języka VB](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak pokazano na poprzednim obrazów, okna narzędzi wizualizatora Wyświetla drzewo składni u góry i siatką właściwości na dole. Siatki właściwości są wyświetlane właściwości elementu, który jest aktualnie wybrany w drzewie, łącznie z platformą .NET *typu* i *rodzaj* (SyntaxKind) elementu.

Drzewa składni obejmuje trzy typy elementów — *węzłów*, *tokenów*, i *elementy towarzyszące składni*. Możesz przeczytać więcej na temat tych typów w [korzystanie ze składni](work-with-syntax.md) artykułu. Elementy każdego rodzaju są reprezentowane w innym kolorze. Kliknij przycisk "Legendy" Omówienie kolorów używanych.

Każdego elementu w drzewie wyświetla również swój własny **span**. **Span** jest indeksów (pozycja początkowy i końcowy) tego węzła w pliku tekstowym.  W tym C# przykładzie, wybrane "UsingKeyword [0..5)" token ma **zakres** szerokości, oznacza to pięć znaków [0..5). "[.)" Notation oznacza, że wartość początkowa indeksu jest częścią zakresu, ale indeks końcowy nie jest.

Istnieją dwa sposoby, aby przejść w drzewie:
* Rozwiń lub kliknąć elementy w drzewie. Wizualizator automatycznie wybiera tekst odpowiadający zakresu tego elementu w edytorze kodu.
* Kliknij lub wybierz tekst w edytorze kodu. W powyższym przykładzie VB Jeśli wybierzesz wiersz zawierający "Moduł Module1" w edytorze kodu wizualizatora automatycznie przechodzi do odpowiedniego węzła ModuleStatement w drzewie. 

Wizualizator wyróżnia elementu w drzewie, którego zakres najlepszych odpowiada zakres tekstu zaznaczonego w edytorze.

Wizualizator odświeża drzewa, aby dopasować zmiany w pliku aktywnego kodu. Dodaj wywołanie do `Console.WriteLine()` wewnątrz `Main()`. Podczas wpisywania wizualizatora odświeża drzewa.

Wstrzymaj, wpisując jeden raz, możesz wpisać `Console.`. Drzewo ma kilka elementów, kolorowanie ujęty w różową ramkę. W tym momencie występują błędy (nazywane również "Diagnostyka") w kodzie wpisane. Te błędy są dołączone do węzłów, tokenów i elementy towarzyszące składni w drzewie składni. Wizualizator dowiesz się, którego elementy mają błędy dołączonych do nich, wyróżnianie tła ujęty w różową ramkę. Można sprawdzić błędy w dowolnym elemencie pokolorowane różowy, umieszczając kursor myszy nad elementem. Wizualizator są wyświetlane tylko błędy składniowe (te błędy związane z składni kod maszynowy); go nie są wyświetlane błędy semantyczne.
 
## <a name="syntax-graphs"></a>Składnia wykresów

Kliknij prawym przyciskiem myszy dowolny element w drzewie, a następnie kliknij przycisk na **Wyświetl wykres kierowany składni**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Wizualizator Wyświetla graficzną reprezentację poddrzewo osadzone na wybrany element. Spróbuj wykonać następujące kroki, aby uzyskać **MethodDeclaration** węzeł odpowiadający `Main()` metody w przykładzie języka C#. Wizualizatora przedstawiony jest wykres składni, która wygląda w następujący sposób:

![Wyświetlanie grafu składni języka C#](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

Spróbuj wykonać takie same dla **SubBlock** węzeł odpowiadający `Main()` metody w poprzednim przykładzie VB. Wizualizatora przedstawiony jest wykres składni, która wygląda w następujący sposób:

![Wyświetlanie grafu składni języka VB](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Podgląd wykresu składni ma opcję, aby wyświetlić legendę jego schemat kolorowania. Możesz również umieścić wskaźnik nad poszczególne elementy na wykresie składni myszą, aby wyświetlić właściwości odpowiadający tego elementu.

Można wyświetlić składnię wykresów dla różne elementy w drzewie wielokrotnie i wykresy zawsze jest wyświetlany w tym samym oknie w programie Visual Studio. Można zadokować tego okna, w dogodnym miejscu w programie Visual Studio, dzięki czemu nie trzeba przełączać się między kart, aby wyświetlić nowy wykres składni. Dole poniżej okna edytora kodu, często jest wygodne.

Oto układ dokowania za pomocą okna narzędzi wizualizatora i okno wykresu składni:

![Jeden dokowania układu okna wykres Wizualizator i składnia](media/syntax-visualizer/docking-layout.png)

Innym rozwiązaniem jest umieszczenie okno wykresu składni na drugim monitorze w konfiguracji dwóch monitorów.

# <a name="inspecting-semantics"></a>Inspekcja semantyki

Syntax Visualizer włącza podstawowe kontrolę symboli i informacje semantyczne. Typ `double x = 1 + 1;` wewnątrz Main() w przykładzie języka C#. Następnie wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wyróżnia wizualizatora **AddExpression** węzła w wizualizatorze. Kliknij prawym przyciskiem myszy to **AddExpression** i kliknij pozycję **Symbol widoku (jeśli istnieje)**. Należy zauważyć, że większość elementów menu ma kwalifikator "ewentualne". Syntax Visualizer sprawdza właściwości węzła, w tym właściwości, które może nie być dostępne dla wszystkich węzłów. 

Siatki właściwości w wizualizatorze aktualizacji, jak pokazano na poniższym rysunku: symbol dla wyrażenia jest **SynthesizedIntrinsicOperatorSymbol** z **rodzaj = metoda**.

![Właściwości symbolu](media/syntax-visualizer/symbol-properties.png)

Spróbuj **TypeSymbol widoku (jeśli istnieje)** dla tego samego **AddExpression** węzła. Siatki właściwości w wizualizatorze aktualizacji, jak pokazano na poniższym rysunku, co oznacza, że typ wybranego wyrażenia `Int32`.

![Właściwości TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Spróbuj **TypeSymbol przekonwertować widoku (jeśli istnieje)** dla tego samego **AddExpression** węzła. Siatki właściwości aktualizacji, co oznacza, że mimo że typ wyrażenia `Int32`, jest typu konwertowanego wyrażenia `Double` jak pokazano na poniższej ilustracji. Ten węzeł zawiera informacje o symbolach przekonwertowanego typu, ponieważ `Int32` występuje wyrażenie w kontekście, w którym muszą zostać skonwertowane do `Double`. Ta konwersja spełnia `Double` typ określona dla zmiennej `x` po lewej stronie operatora przypisania.

![Przekonwertowana TypeSymbol właściwości](media/syntax-visualizer/converted-type-symbol-properties.png)

Ponadto spróbuj **wartości stałej widoku (jeśli istnieje)** dla tego samego **AddExpression** węzła. Siatki właściwości pokazuje, że wartości wyrażenia jest stałą czasu kompilacji z wartością `2`.

![Stała wartość](media/syntax-visualizer/constant-value.png)

Poprzedni przykład można również replikować w VB. Typ `Dim x As Double = 1 + 1` w pliku VB. Wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wizualizator wyróżnia odpowiednich **AddExpression** węzła w wizualizatorze. Powtórz te czynności dla tego **AddExpression** powinien zostać wyświetlony takie same wyniki.

Zbadanie kodu w VB. Zaktualizuj główne plik VB następującym kodem:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Ten kod wprowadza aliasu o nazwie `C` mapuje do typu `System.Console` w górnej części pliku i używa tego aliasu wewnątrz `Main()`. Wybierz użycie tego aliasu `C` w `C.WriteLine()`w programie `Main()` metody. Wizualizator wybiera odpowiedni **IdentifierName** węzła w wizualizatorze. Kliknij prawym przyciskiem myszy ten węzeł, a następnie kliknij przycisk na **Symbol widoku (jeśli istnieje)**. Siatki właściwości wskazuje na to, że ten identyfikator jest powiązana z typem `System.Console` jak pokazano na poniższej ilustracji:

![Właściwości symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Spróbuj **AliasSymbol widoku (jeśli istnieje)** dla tego samego **IdentifierName** węzła. Siatki właściwości wskazuje identyfikator aliasu o nazwie `C` , jest powiązany z `System.Console` docelowej. Innymi słowy, siatki właściwości zawiera informacje dotyczące **AliasSymbol** odpowiadającego identyfikatorowi `C`.

![Właściwości AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Sprawdź, czy symbol odpowiadający wszelkie deklarowany typ, metoda, właściwość. Wybierz odpowiedni węzeł w wizualizatorze i kliknąć **Symbol widoku (jeśli istnieje)**. Wybierz metodę `Sub Main()`, włączając w to treść metody. Kliknij pozycję **Symbol widoku (jeśli istnieje)** dla odpowiedniego **SubBlock** węzła w wizualizatorze. Pokazuje siatki właściwości **MethodSymbol** tego **SubBlock** ma nazwę `Main` z typem zwracanym `Void`.

![Wyświetlanie symboli dla deklaracji metody](media/syntax-visualizer/method-symbol.png)

Powyższe przykłady VB mogą łatwo zreplikowane w języku C#. Typ `using C = System.Console;` zamiast `Imports C = System.Console` aliasu. Powyższych kroków w języku C# przynieść takie same wyniki w oknie wizualizatora.

Operacje semantycznego inspekcji są dostępne tylko w węzłach. Nie są one dostępne na tokeny lub elementy towarzyszące składni. Nie wszystkie węzły mają interesujących informacji semantycznych do wglądu. Gdy węzeł nie interesujące informacje semantyczne, klikając **widoku * symboli (jeśli istnieje)** z siatką właściwości puste.

Możesz dowiedzieć się więcej o interfejsach API do wykonywania analizy semantycznej w [korzystanie z semantyki](work-with-semantics.md) przeglądu.

## <a name="closing-the-syntax-visualizer"></a>Zamykanie wizualizatora składni

Możesz zamknąć okno wizualizatora, gdy nie używasz go zbadanie kodu źródłowego. Wizualizatora składni aktualizuje jego wyświetlana podczas przeglądania kodu, edytowanie i zmiana źródła. Można uzyskać rozprasza uwagę, gdy nie jest używany. 
