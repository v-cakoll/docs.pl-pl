---
title: Debugowanie aplikacji Hello World .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak debugować aplikację Hello World napisaną w języku C# lub Visual Basic za pomocą programu Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: b2ee1401fc89f990c5f930d80d1a510a117e63a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156676"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Debugowanie aplikacji C# lub Visual Basic .NET Core Hello World przy użyciu programu Visual Studio

Do tej pory postępowano zgodnie z instrukcjami w [tworzenie pierwszej aplikacji konsoli .NET Core w programie Visual Studio 2019,](with-visual-studio.md) aby utworzyć i uruchomić prostą aplikację konsoli. Po napisaniu i skompilowaniu aplikacji można rozpocząć testowanie go. Program Visual Studio zawiera kompleksowy zestaw narzędzi do debugowania, których można używać do rozwiązywania problemów z aplikacją.

## <a name="debug-build-configuration"></a>Konfiguracja kompilacji debugowania

*Debugowanie* i *wydanie* to dwie domyślne konfiguracje kompilacji programu Visual Studio. Bieżąca konfiguracja kompilacji jest wyświetlana na pasku narzędzi. Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania wersji debugowania aplikacji:

![Pasek narzędzi programu Visual Studio z wyróżnionym debugowaniem](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Rozpocznij od uruchomienia debugowania wersji aplikacji. Konfiguracja kompilacji debugowania wyłącza większość optymalizacji kompilatora i zapewnia bogatsze informacje podczas procesu kompilacji.

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

Uruchom program i spróbuj wykonać kilka funkcji debugowania:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Ustaw *punkt przerwania* w `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` wierszu, który odczytuje, klikając lewy margines okna kodu w tym wierszu. Punkt przerwania można również ustawić, umieszczając daszek w wierszu kodu, a następnie naciskając **klawisz F9** lub wybierając punkt przerwania **przełączania debugowania** > **Toggle Breakpoint** z paska menu.

   Punkt przerwania tymczasowo przerywa wykonanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.

   Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersz, na którym ustawiono punkt przerwania, wyróżniając go i wyświetlając czerwone kółko na lewym marginesie.

   ![Okno programu Visual Studio z zestawem punktów przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając **klawisz F5**lub wybierając **debugowanie** > **Debuguj rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program wyświetli monit o nazwę, a następnie naciśnij klawisz **Enter**.

1. Wykonywanie programu zatrzymuje się, gdy osiągnie `Console.WriteLine` punkt przerwania i przed wykonaniem metody. Okno **Locals** wyświetla wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metody.

   ![Zrzut ekranu przedstawiający punkt przerwania w programie Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. Okno **Natychmiastowe** umożliwia interakcję z debugowaniem aplikacji. Można interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak wpływa ona na program.

   1. Jeśli okno **Natychmiastowe** nie jest widoczne, wyświetl je, wybierając opcję **Debugowanie** > **systemu Windows** > **Natychmiastowe**.

   1. Wprowadź `name = "Gracie"` w oknie **Natychmiastowe** i naciśnij klawisz **Enter.**

   1. Wprowadź `date = DateTime.Parse("11/16/2019 5:25 PM")` w oknie **Natychmiastowe** i naciśnij klawisz **Enter.**

   Okno **Natychmiastowe** wyświetla wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartości. Ponadto wartości zmiennych są aktualizowane w oknie **Locals.**

   ![Miejscowi i bezpośredni system Windows w programie Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając **opcję DebugUj** > **kontynuuj**. Wartości wyświetlane w oknie konsoli odpowiadają zmianom dokonanym w oknie **Natychmiastowy.**

   ![Okno konsoli z wyświetlonymi wprowadzonymi wartościami](./media/debugging-with-visual-studio/console-window.png)

1. Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji i zatrzymać debugowanie.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Ustaw *punkt przerwania* w `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")` wierszu, który odczytuje, klikając lewy margines okna kodu w tym wierszu. Punkt przerwania można również ustawić, umieszczając daszek na żądanym wierszu, a następnie wybierając punkt przerwania **przełączania debugowania** > **Toggle Breakpoint** z paska menu.

   Punkt przerwania tymczasowo przerywa wykonanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.

   Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersz, na którym ustawiono punkt przerwania, wyróżniając go i wyświetlając czerwone kółko na lewym marginesie.

   ![Okno programu Visual Studio z zestawem punktów przerwania](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając **klawisz F5**lub wybierając **debugowanie** > **Debuguj rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program wyświetli **Enter**monit o nazwę, a naciśnieenter .

1. Wykonywanie programu zatrzymuje się, gdy osiągnie `Console.WriteLine` punkt przerwania i przed wykonaniem metody. Okno **Locals** wyświetla wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metody.

1. Okno **Natychmiastowe** umożliwia interakcję z debugowaniem aplikacji. Można interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak wpływa ona na program.

   1. Jeśli okno **Natychmiastowe** nie jest widoczne, wyświetl je, wybierając opcję **Debugowanie** > **systemu Windows** > **Natychmiastowe**.

   1. Wprowadź `name = "Gracie"` w oknie **Natychmiastowe** i naciśnij klawisz **Enter.**

   1. Wprowadź `date = DateTime.Parse("11/16/2019 5:25 PM")` w oknie **Natychmiastowe** i naciśnij klawisz **Enter.**

   Wartości zmiennych są aktualizowane w oknie **Locals.**

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając element menu **Debuguj** > **kontynuuj.** Wartości wyświetlane w oknie konsoli odpowiadają zmianom dokonanym w oknie **Natychmiastowy.**

   ![Okno konsoli z wyświetlonymi wprowadzonymi wartościami](./media/debugging-with-visual-studio/console-window.png)

1. Naciśnij dowolny klawisz, aby zakończyć działanie aplikacji i zatrzymać debugowanie.

---

## <a name="set-a-conditional-breakpoint"></a>Ustawianie warunkowego punktu przerwania

Program wyświetla ciąg, który wprowadza użytkownik. Co się stanie, jeśli użytkownik niczego nie wprowadzi? Można przetestować to za pomocą przydatnej funkcji debugowania o nazwie *warunkowego punktu przerwania,* która przerywa wykonywanie programu, gdy spełniony jest co najmniej jeden warunek.

Aby ustawić warunkowy punkt przerwania i sprawdzić, co się stanie, gdy użytkownik nie przejdzie ciągu, wykonaj następujące czynności:

# <a name="c"></a>[C #](#tab/csharp)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **Warunki,** aby otworzyć okno dialogowe **Ustawienia punktu przerwania.** Zaznacz pole **Warunki,** jeśli nie jest jeszcze zaznaczone.

   ![Edytor z panelem ustawień punktu przerwania - C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. W przypadku **wyrażenia warunkowego**zamień "np. x == 5" na następujące elementy:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że `String.IsNullOrEmpty(name)` wywołanie `true` metody `name` jest albo dlatego, że nie został przypisany wartość lub ponieważ jego wartość jest pusty ciąg (""). Zamiast wyrażenia warunkowego można również określić *liczbę trafień*, która przerywa wykonywanie programu przed wykonaniem instrukcji określoną liczbę razy, lub *warunek filtru*, który przerywa wykonywanie programu na podstawie takich atrybutów, jak identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz **pozycję Zamknij,** aby zamknąć okno dialogowe.

1. Uruchom program z debugowaniem, naciskając **klawisz F5**.

1. W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu o wprowadzenie nazwy.

1. Ponieważ warunek określony, `name` jest `null` <xref:System.String.Empty?displayProperty=nameWithType>albo lub , został spełniony, wykonanie programu zatrzymuje `Console.WriteLine` się, gdy osiągnie punkt przerwania i przed wykonaniem metody.

1. Wybierz okno **Locals,** które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody. W tym `Main` przypadku jest aktualnie wykonywaną metodą. Należy zauważyć, że `name` wartość `""`zmiennej jest , lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, że wartość jest pustym ciągiem, wprowadzając następującą instrukcję w oknie **Natychmiastowe** i naciskając klawisz **Enter**. Wynik jest `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Natychmiastowe okno zwracawartość true po wykonaniu instrukcji - C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kodu lub wybierając **debugowanie > Przełącz punkt przerwania,** gdy jest zaznaczony wiersz kodu.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **Warunki,** aby otworzyć okno dialogowe **Ustawienia punktu przerwania.** Zaznacz pole **wyboru Warunki**.

   ![Edytor z panelem ustawień punktu przerwania — Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Dla **wyrażenia warunkowego** zastąpić "np x = 5" z następującymi:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że `String.IsNullOrEmpty(name)` wywołanie `true` metody `name` jest albo dlatego, że nie został przypisany wartość lub ponieważ jego wartość jest pusty ciąg (""). Zamiast wyrażenia warunkowego można również określić *liczbę trafień*, która przerywa wykonywanie programu przed wykonaniem instrukcji określoną liczbę razy, lub *warunek filtru*, który przerywa wykonywanie programu na podstawie takich atrybutów, jak identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz **pozycję Zamknij,** aby zamknąć okno dialogowe.

1. Uruchom program z debugowaniem, naciskając **klawisz F5**.

1. W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu o wprowadzenie nazwy.

1. Ponieważ warunek określony, `name` jest `null` <xref:System.String.Empty?displayProperty=nameWithType>albo lub , został spełniony, wykonanie programu zatrzymuje `Console.WriteLine` się, gdy osiągnie punkt przerwania i przed wykonaniem metody.

1. Wybierz okno **Locals,** które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody. W tym `Main` przypadku jest aktualnie wykonywaną metodą. Należy zauważyć, że `name` wartość `""`zmiennej jest , lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, że wartość jest pustym ciągiem, wprowadzając następującą instrukcję w oknie **Natychmiastowe** i naciskając klawisz **Enter**. Wynik jest `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Natychmiastowe okno zwracawartość true po wykonaniu instrukcji - Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kodu lub wybierając element menu **Debuguj > Przełącz punkt przerwania** z zaznaczonym wierszem.

---
## <a name="step-through-a-program"></a>Krok po programie

Program Visual Studio umożliwia również przechodzenie liniowo przez program i monitorowanie jego realizacji. Zwykle można ustawić punkt przerwania i użyć tej funkcji, aby śledzić przepływ programu przez niewielką część kodu programu. Ponieważ program jest mały, można przejść przez cały program:

# <a name="c"></a>[C #](#tab/csharp)

1. Na pasku menu wybierz pozycję **Debuguj** > **krok do** lub naciśnij klawisz **F11**. Program Visual Studio wyróżnia i wyświetla strzałkę obok następnego wiersza wykonania.

   ![Visual Studio krok do metody - C #](./media/debugging-with-visual-studio/step-into-method.png)

   W tym momencie **locals** okno pokazuje, że program zdefiniował tylko jedną zmienną, `args`. Ponieważ nie przekazano programowi żadnych argumentów wiersza polecenia, jego wartość jest tablicą pustych ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio teraz wyróżnia następny wiersz wykonania. Jak pokazano na obrazie, zajęło mniej niż jedną milisekundę, aby wykonać kod między ostatnią instrukcją a tą. `args`pozostaje jedyną zadeklarowaną zmienną, a okno konsoli pozostaje puste.

   ![Krok programu Visual Studio w źródle metody — C #](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio wyróżnia instrukcję, która zawiera przypisanie zmiennej. `name` Okno **Locals** pokazuje, że `name` jest `null`, a okno konsoli wyświetla ciąg "Jak masz na imię?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> konsoli, ale mimo to metoda będzie przechwytywać dane wejściowe.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio wyróżnia instrukcję, która zawiera przypisanie zmiennej. `date` Locals **Locals** okno pokazuje wartość zwracaną przez <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> wywołanie metody. W oknie konsoli jest również wyświetlany ciąg wprowadzony w wierszu polecenia.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Locals **Locals** okno pokazuje wartość `date` zmiennej po przypisania z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. Okno konsoli pozostaje bez zmian.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> wywołuje metodę. W oknie konsoli jest wyświetlany sformatowany ciąg.

1. Wybierz **debugowanie** > **step out** lub naciśnij klawisz **Shift**+**F11**. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Na pasku menu wybierz pozycję **Debuguj** > **krok do** lub naciśnij klawisz **F11**. Program Visual Studio wyróżnia i wyświetla strzałkę obok następnego wiersza wykonania.

   ![Visual Studio krok do metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   W tym momencie **locals** okno pokazuje, że program zdefiniował tylko jedną zmienną, `args`. Ponieważ nie przekazano programowi żadnych argumentów wiersza polecenia, jego wartość jest tablicą pustych ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio teraz wyróżnia następny wiersz wykonania. Jak pokazano na rysunku, zajęło mniej niż jedną milisekundę, aby wykonać kod między ostatnią instrukcją a tą. `args`pozostaje jedyną zadeklarowaną zmienną, a okno konsoli pozostaje puste.

   ![Visual Studio krok do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio wyróżnia instrukcję, która zawiera przypisanie zmiennej. `name` Okno **Locals** pokazuje, że `name` jest `Nothing`, a okno konsoli wyświetla ciąg "Jak masz na imię?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> konsoli, ale mimo to metoda będzie przechwytywać dane wejściowe.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio wyróżnia instrukcję, która zawiera przypisanie zmiennej. `currentDate` Locals **Locals** okno pokazuje wartość zwracaną przez <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> wywołanie metody. W oknie konsoli jest również wyświetlany ciąg wprowadzony, gdy konsola zostanie poproszona o wprowadzenie danych.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Okno konsoli pozostaje bez zmian.

1. Wybierz **opcję Debug** > **Ujmij krok do** lub naciśnij klawisz **F11**. Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> wywołuje metodę. W oknie konsoli jest wyświetlany sformatowany ciąg.

1. Wybierz **debugowanie** > **step out** lub naciśnij klawisz **Shift**+**F11**. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

---

## <a name="build-a-release-version"></a>Tworzenie wersji

Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję. Wersja zawiera optymalizacje kompilatora, które czasami mogą negatywnie wpłynąć na zachowanie aplikacji. Na przykład optymalizacje kompilatora, które są przeznaczone do poprawy wydajności można utworzyć warunki wyścigu w aplikacjach wielowątkowych.

Aby utworzyć i przetestować wersję aplikacji konsoli, zmień konfigurację kompilacji na pasku narzędzi z **Debug** do **Release**.

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną debugowaniem](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Po naciśnięciu **klawisza F5** lub **wybraniu opcji Tworzenie rozwiązania** z menu **Kompilacja** program Visual Studio kompiluje wersję aplikacji. Można go przetestować, tak jak w wersji debugowania.

## <a name="next-steps"></a>Następne kroki

Po debugowania aplikacji następnym krokiem jest opublikowanie wdrożonej wersji aplikacji. Aby uzyskać informacje na temat sposobu wykonywania tej funkcji, zobacz [Publikowanie aplikacji .NET Core Hello World za pomocą programu Visual Studio](publishing-with-visual-studio.md).
