---
title: Eksploruj kodu z wizualizatora składni Roslyn w programie Visual Studio
description: Wizualizator składni zawiera narzędzie visual do eksplorowania modele, które generuje zestawu SDK platformy kompilatora .NET dla kodu.
author: billwagner
ms.author: wiwagn
ms.date: 03/07/2018
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 04452159c759a0c7236c1b93dc966e5e9c54574a
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="explore-code-with-the-roslyn-syntax-visualizer-in-visual-studio"></a>Eksploruj kodu z wizualizatora składni Roslyn w programie Visual Studio

Ten artykuł zawiera omówienie narzędzia wizualizatora składnię, która jest dostarczana jako część kompilatora platformy .NET ("Roslyn") zestawu SDK. Wizualizator składni jest okna narzędzia, która pomaga sprawdzić i Eksploruj drzewa składni. Jest podstawowe narzędzie do zrozumienia modeli dla kodu, który chcesz przeanalizować. Istnieje również pomoc do debugowania podczas opracowywania własnych aplikacji przy użyciu kompilatora platformy .NET ("Roslyn") zestawu SDK. Otwórz narzędzie podczas tworzenia Twojej pierwszy analizatorów. Wizualizator pomaga w zrozumieniu modeli używanych przez interfejsy API. Można także użyć narzędzi, takich jak [SharpLab](https://sharplab.io) lub [LINQPad](https://www.linqpad.net/) Sprawdź kod i zrozumieć drzewa składni.

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

Zapoznanie pojęcia używane w zestawie SDK platformy kompilatora .NET, odczytując [omówienie](compiler-api-model.md) artykułu. Zawiera on wprowadzenie do drzewa składni, węzły tokeny i elementy towarzyszące składni.

## <a name="syntax-visualizer"></a>Składnia wizualizatora

**Wizualizatora składni** włącza kontrolę drzewo składni dla pliku kodu C# i VB w bieżącym oknie active editor w środowisku IDE programu Visual Studio. Wizualizator można uruchomić, klikając **widoku** > **inne okna** > **wizualizatora składni**.  Można również użyć **Szybkie uruchamianie** paska narzędzi w prawym górnym rogu. Typ "składni", a polecenie, aby otworzyć **wizualizatora składni** powinna zostać wyświetlona.

To polecenie powoduje otwarcie wizualizatora składni jako przestawne okna narzędzia. Jeśli nie masz otwarte okna edytora kodu, ekran jest pusty, jak pokazano na poniższej ilustracji. 

![Okno narzędzia wizualizatora składni](media/syntax-visualizer/syntax-visualizer.png)

Dokowanie tego okna narzędzia w dogodnym miejscu w programie Visual Studio, takich jak po lewej stronie. Wizualizator zawiera informacje dotyczące bieżącego pliku kodu.

Utwórz nowy projekt za pomocą **pliku** > **nowy projekt** polecenia. Można utworzyć projektu VB albo C#. Po otwarciu pliku głównego kodu dla tego projektu programu Visual Studio wizualizatora Wyświetla drzewa składni dla niego. Możesz otworzyć żadnych istniejących C# / VB pliku w tym wystąpieniu programu Visual Studio i wizualizatora wyświetla ten plik drzewa składni. Jeśli masz wiele plików kodu Otwórz w programie Visual Studio wizualizatora Wyświetla drzewo składni dla pliku kodu aktualnie aktywny, (kod plik, który ma fokus klawiatury.)

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
![Wizualizacja drzewa składni języka C#](media/syntax-visualizer/visualize-csharp.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)
![Wizualizacja drzewa składni języka VB](media/syntax-visualizer/visualize-visual-basic.png)

---

Jak pokazano w poprzednim obrazów, okna narzędzia wizualizatora Wyświetla drzewa składni u góry i u dołu siatki właściwości. Siatki właściwości są wyświetlane właściwości elementu aktualnie wybranego w drzewie, łącznie z .NET *typu* i *rodzaj* (SyntaxKind) elementu.

Drzewa składni obejmuje trzy typy elementów — *węzłów*, *tokenów*, i *elementy towarzyszące składni*. Możesz przeczytać więcej informacji na temat tych typów w [pracować ze składnią](work-with-syntax.md) artykułu. Elementy każdego typu są przedstawiane przy użyciu różnych kolorów. Kliknij przycisk "Legendy" Przegląd kolory używane.

Każdego elementu w drzewie wyświetla również własną **span**. **Span** jest wskaźników (pozycja początkowy i końcowy) dla tego węzła, w pliku tekstowym.  W poprzednim C# przykładzie wybranego "UsingKeyword [0..5)" token ma **zakres** szerokości, który jest pięć znaków [0..5). "[.)" Notation oznacza, że początkowy indeks jest częścią zakresu, ale nie jest końcową indeksu.

Istnieją dwa sposoby Przejdź drzewa:
* Rozwiń lub kliknięcie elementu w drzewie. Wizualizator automatycznie wybiera tekst odpowiadający zakres tego elementu w edytorze kodu.
* Kliknij, lub zaznacz tekst w edytorze kodu. W powyższym przykładzie VB Jeśli zaznacz wiersz zawierający "Modułu Module1" w edytorze kodu wizualizatora automatycznie przechodzi do odpowiedniego węzła ModuleStatement w drzewie. 

Wizualizator prezentuje elementu w drzewie, którego zakres najlepiej odpowiada zakres tekstu zaznaczonego w edytorze.

Wizualizator odświeża drzewa, aby dopasować zmiany w pliku active kodu. Dodaj wywołanie do `Console.WriteLine()` wewnątrz `Main()`. Podczas wpisywania wizualizatora odświeża drzewa.

Wpisana Wstrzymaj, wpisując raz można `Console.`. Drzewo zawiera niektóre elementy pokolorowane na różowo. W tym momencie występują błędy (nazywane również "Diagnostyki") w kodzie typu. Te błędy są dołączone do węzłów, tokeny i elementy towarzyszące składni w drzewie składni. Wizualizator pokazuje, którego elementy mają błędy dołączony do nich wyróżnianie tła na różowo. Aby sprawdzić błędy w dowolnym elemencie pokolorowane różowym, ustawiając kursor nad elementem. Wizualizator są wyświetlane tylko błędy składniowe (te błędy dotyczące składni kod maszynowy); go nie są wyświetlane wszystkie błędy semantyczne.
 
## <a name="syntax-graphs"></a>Wykresy składni

Kliknij prawym przyciskiem myszy dowolny element w drzewie, a następnie wybierz polecenie **Wyświetl wykres skierowane do składni**. 

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

Wizualizator Wyświetla graficzną reprezentację poddrzewo, począwszy od wybranego elementu. Spróbuj wykonać następujące czynności dla **MethodDeclaration** węzeł odpowiadający `Main()` metody w tym przykładzie C#. Wizualizator Wyświetla wykres składni, która wygląda w następujący sposób:

![Wyświetlanie wykresu składni języka C#](media/syntax-visualizer/csharp-syntax-graph.png)
# <a name="visual-basictabvisual-basic"></a>[Visual Basic](#tab/visual-basic)

Spróbuj również na **SubBlock** węzeł odpowiadający `Main()` metody w poprzednim przykładzie VB. Wizualizator Wyświetla wykres składni, która wygląda w następujący sposób:

![Wyświetlanie wykresu składni języka VB](media/syntax-visualizer/visual-basic-syntax-graph.png)

---

Podgląd wykresu składni ma opcji wyświetlania legendy jego schemat kolorowania. Można również ustawić kursor nad poszczególne elementy na wykresie składni za pomocą myszy, aby wyświetlić właściwości odpowiadającej tego elementu.

Wykresy składni dla różnych elementów można wyświetlić wielokrotnie w drzewie i wykresy zawsze jest wyświetlany w tym samym oknie w programie Visual Studio. Zadokuj z tego okna w dogodnym miejscu w programie Visual Studio, dzięki czemu nie trzeba Przełączanie kart, aby wyświetlić nowy wykres składni. Dolnej poniżej okna edytora kodu, często jest wygodne.

Oto dokowania układu do użycia z okna narzędzia wizualizatora i wykres składni:

![Jeden dokowania układu okna wykresu wizualizatora i składni](media/syntax-visualizer/docking-layout.png)

Innym rozwiązaniem jest umieszczenie okno wykresu składni na drugim monitorze w konfiguracji dwóch monitorów.

# <a name="inspecting-semantics"></a>Sprawdzanie semantyki

Wizualizator składni umożliwia proste kontroli symboli i informacje semantyczne. Typ `double x = 1 + 1;` wewnątrz Main() w przykładzie C#. Następnie wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wyróżnia wizualizatora **AddExpression** węzła w wizualizatora. Kliknij prawym przyciskiem myszy na tym **AddExpression** i wybierz polecenie **Symbol widoku (jeśli istnieją)**. Zwróć uwagę, że większość elementów menu ma kwalifikator "ewentualne". Wizualizator składni sprawdza właściwości węzła, w tym właściwości, które nie mogą znajdować się dla wszystkich węzłów. 

Siatki właściwości w wizualizatora aktualizacji, jak pokazano na poniższej ilustracji: symbol dla wyrażenia jest **SynthesizedIntrinsicOperatorSymbol** z **rodzaj = metody**.

![Właściwości symbolu](media/syntax-visualizer/symbol-properties.png)

Spróbuj **TypeSymbol widoku (jeśli istnieją)** dla tego samego **AddExpression** węzła. Siatki właściwości w wizualizatora aktualizacji, jak pokazano na poniższej ilustracji, co oznacza, że typ wybranego wyrażenia `Int32`.

![Właściwości TypeSymbol](media/syntax-visualizer/type-symbol-properties.png)

Spróbuj **TypeSymbol przekonwertować widoku (jeśli istnieją)** dla tego samego **AddExpression** węzła. Siatki właściwości aktualizacji, co oznacza, że chociaż jest typ wyrażenia `Int32`, przekonwertowanego typ wyrażenia jest `Double` jak pokazano na poniższej ilustracji. Ten węzeł zawiera informacji o symbolach przekonwertowanego typu, ponieważ `Int32` wyrażenie występuje w kontekście, w którym musi zostać przekonwertowany do `Double`. Ta konwersja spełnia `Double` typ określony dla zmiennej `x` po lewej stronie operatora przypisania.

![Przekonwertowana właściwości TypeSymbol](media/syntax-visualizer/converted-type-symbol-properties.png)

Na koniec, spróbuj **wartości stałej widoku (jeśli istnieją)** dla tego samego **AddExpression** węzła. Siatki właściwości pokazuje, że wartość wyrażenia jest stałą czasu kompilacji z wartością `2`.

![Stała wartość](media/syntax-visualizer/constant-value.png)

Powyższy przykład również mogą być replikowane w języku Visual Basic Typ `Dim x As Double = 1 + 1` w pliku VB. Wybierz wyrażenie `1 + 1` w oknie edytora kodu. Wizualizator wyróżnia odpowiadającego **AddExpression** węzła w wizualizatora. Powtórz te czynności dla tej **AddExpression** i powinna zostać wyświetlona identycznych wyników.

Badanie więcej kodu w języku Visual Basic Zaktualizuj główny plik VB następującym kodem:

```vb
Imports C = System.Console

Module Program
    Sub Main(args As String())
        C.WriteLine()
    End Sub
End Module
```

Ten kod wprowadza aliasu o nazwie `C` mapujący do typu `System.Console` w górnej części pliku i używa tego aliasu wewnątrz `Main()`. Wybrać ten alias `C` w `C.WriteLine()`w `Main()` metody. Wizualizator wybiera odpowiednie **IdentifierName** węzła w wizualizatora. Kliknij prawym przyciskiem myszy ten węzeł i kliknij przycisk **Symbol widoku (jeśli istnieją)**. Siatki właściwości wskazuje, że ten identyfikator jest powiązany z typem `System.Console` jak pokazano na poniższej ilustracji:

![Właściwości symbolu](media/syntax-visualizer/symbol-visual-basic.png)

Spróbuj **AliasSymbol widoku (jeśli istnieją)** dla tego samego **IdentifierName** węzła. Siatki właściwości oznacza identyfikator aliasu o nazwie `C` który jest powiązany `System.Console` docelowej. Innymi słowy, siatki właściwości zawiera informacje dotyczące **AliasSymbol** odpowiadający identyfikator `C`.

![Właściwości AliasSymbol](media/syntax-visualizer/alias-symbol.png)

Sprawdź, czy symbol odpowiadający żadnych deklarowany typ, metoda, właściwość. Wybierz odpowiedni węzeł wizualizatora i kliknij na **Symbol widoku (jeśli istnieją)**. Wybierz metodę `Sub Main()`, łącznie z treści metody. Polecenie **Symbol widoku (jeśli istnieją)** dla odpowiedniego **SubBlock** węzła w wizualizatora. Pokazuje siatki właściwości **MethodSymbol** tego **SubBlock** ma nazwę `Main` z zwracany typ `Void`.

![Wyświetlanie symboli dla deklaracji — metoda](media/syntax-visualizer/method-symbol.png)

W powyższych przykładach VB można łatwo replikowane w języku C#. Typ `using C = System.Console;` zamiast `Imports C = System.Console` aliasu. Powyższych kroków w języku C# yield identyczne wyniki w oknie wizualizatora.

Operacje kontroli semantycznego są dostępne tylko w węzłach. Nie są one dostępne na tokeny lub elementy towarzyszące składni. Nie wszystkie węzły mają interesujące informacje semantyczne do sprawdzenia. Jeśli węzeł nie ma interesujące informacje semantyczne, klikając **widoku * symboli (jeśli istnieją)** zawiera siatki właściwości puste.

Więcej o interfejsy API do wykonywania analizy semantyczne w [pracować z semantyki](work-with-semantics.md) przeglądu.

## <a name="closing-the-syntax-visualizer"></a>Zamykanie wizualizatora składni

Aby zamknąć okno wizualizatora, gdy nie jest ona używana do zbadanie kodu źródłowego. Wizualizator składni aktualizuje jego wyświetlana podczas przeglądania kodu, edytowanie i zmiana źródła. Można uzyskać rozpraszać gdy nie jest używana. 
