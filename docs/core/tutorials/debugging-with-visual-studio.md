---
title: Debugowanie aplikacji Hello world .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak debugować aplikację Hello world w C# programie lub Visual Basic za pomocą programu Visual Studio.
ms.date: 12/05/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bc2736165ec827c1f2670605f23f549ceed4e83a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714055"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio"></a>Debuguj aplikację C# Hello World .NET Core lub Visual Basic przy użyciu programu Visual Studio

Do tej pory wykonano kroki opisane w temacie [Tworzenie pierwszej aplikacji konsolowej .NET Core w programie Visual Studio 2019](with-visual-studio.md) w celu utworzenia i uruchomienia prostej aplikacji konsolowej. Po napisaniu i skompilowaniu aplikacji możesz rozpocząć testowanie. Program Visual Studio zawiera kompleksowy zestaw narzędzi do debugowania, których można użyć do rozwiązywania problemów z aplikacją.

## <a name="debug-build-configuration"></a>Debuguj konfigurację kompilacji

*Debugowanie* i *wydanie* są dwiema domyślnymi konfiguracjami kompilacji programu Visual Studio. Bieżąca konfiguracja kompilacji jest pokazywana na pasku narzędzi. Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania wersji do debugowania aplikacji:

![Pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Zacznij od uruchomienia wersji debugowania aplikacji. Konfiguracja kompilacji debugowania powoduje wyłączenie większości optymalizacji kompilatora i zapewnia bogatsze informacje podczas procesu kompilacji.

## <a name="set-a-breakpoint"></a>Ustaw punkt przerwania

Uruchom program i wypróbuj kilka funkcji debugowania:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Ustaw *punkt przerwania* w wierszu, który odczytuje `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");`, klikając na lewym marginesie okna kod w tym wierszu. Możesz również ustawić punkt przerwania, umieszczając karetkę w wierszu kodu, a następnie naciskając klawisz **F9** lub wybierając pozycję **Debuguj** > **Przełącz punkt przerwania** z paska menu.

   Punkt przerwania tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.

   Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwony okrąg na lewym marginesie.

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając klawisz **F5**lub wybierając pozycję **Debuguj** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę, a następnie naciśnij klawisz **Enter**.

1. Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem metody `Console.WriteLine`. W oknie **Ustawienia lokalne** są wyświetlane wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.

   ![Zrzut ekranu punktu przerwania w programie Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. Okno **bezpośrednie** umożliwia korzystanie z debugowanej aplikacji. Możesz interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.

   1. Jeśli okno **bezpośrednie** nie jest widoczne, Wyświetl je, wybierając pozycję **debuguj** > **Windows** > **natychmiastowe**.

   1. Wprowadź `name = "Gracie"` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   1. Wprowadź `date = DateTime.Parse("11/16/2019 5:25 PM")` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   W oknie **bezpośrednim** zostanie wyświetlona wartość zmiennej String i właściwości wartości <xref:System.DateTime>. Ponadto wartości zmiennych są aktualizowane w oknie **zmiennych lokalnych** .

   ![Lokalne i natychmiastowe okna w programie Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając pozycję **Debuguj** > **Kontynuuj**. Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w oknie **bezpośrednim** .

   ![Okno konsoli pokazujące wprowadzone wartości](./media/debugging-with-visual-studio/console-window.png)

1. Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Ustaw *punkt przerwania* w wierszu, który odczytuje `Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}!")`, klikając na lewym marginesie okna kod w tym wierszu. Możesz również ustawić punkt przerwania, umieszczając karetkę w żądanym wierszu, a następnie wybierając pozycję **debuguj** > **Przełącz punkt przerwania** z paska menu.

   Punkt przerwania tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.
   
   Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwony okrąg na lewym marginesie.

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/vb/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając klawisz **F5**lub wybierając pozycję **Debuguj** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę i naciśnij klawisz **Enter**.

1. Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem metody `Console.WriteLine`. W oknie **Ustawienia lokalne** są wyświetlane wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.

1. Okno **bezpośrednie** umożliwia korzystanie z debugowanej aplikacji. Możesz interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.

   1. Jeśli okno **bezpośrednie** nie jest widoczne, Wyświetl je, wybierając pozycję **debuguj** > **Windows** > **natychmiastowe**.

   1. Wprowadź `name = "Gracie"` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   1. Wprowadź `date = DateTime.Parse("11/16/2019 5:25 PM")` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   Wartości zmiennych są aktualizowane w oknie **zmiennych lokalnych** .

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając element menu **Debuguj** > **Kontynuuj** . Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w oknie **bezpośrednim** .

   ![Okno konsoli pokazujące wprowadzone wartości](./media/debugging-with-visual-studio/console-window.png)

1. Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.

---

## <a name="set-a-conditional-breakpoint"></a>Ustaw punkt przerwania warunkowego

Program wyświetla ciąg wprowadzony przez użytkownika. Co się stanie, jeśli użytkownik nie wprowadzi niczego? Można to sprawdzić za pomocą przydatnej funkcji debugowania nazywanej *warunkowym punktem przerwania*, która przerywa wykonywanie programu po spełnieniu jednego lub kilku warunków.

Aby ustawić warunkowy punkt przerwania i sprawdzić, co się dzieje, gdy użytkownik nie może wprowadzić ciągu, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** . Zaznacz pole wyboru **warunki** , jeśli nie zostało ono jeszcze wybrane.

   ![Edytor przedstawiający panel ustawień punktu przerwania —C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Dla **wyrażenia warunkowego**Zastąp wartość "np. x = = 5" następującym:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że wywołanie metody `String.IsNullOrEmpty(name)` jest `true`, ponieważ `name` nie ma przypisanej wartości lub ponieważ jej wartość jest ciągiem pustym (""). Zamiast wyrażenia warunkowego można także określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz pozycję **Zamknij** , aby zamknąć okno dialogowe.

1. Uruchom program z debugowaniem, naciskając klawisz **F5**.

1. W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu, aby wprowadzić swoją nazwę.

1. Ponieważ określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostało spełnione, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem metody `Console.WriteLine`.

1. Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody. W tym przypadku `Main` jest aktualnie wykonywanym metodami. Zwróć uwagę, że wartość zmiennej `name` jest `""`lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w oknie **bezpośrednim** i naciskając klawisz **Enter**. Wynik jest `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji —C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod lub wybierając polecenie **debuguj > Przełącz punkt przerwania** , gdy zostanie wybrany wiersz kodu.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** . Zaznacz pole **warunki**.

   ![Edytor przedstawiający panel ustawień punktu przerwania — Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. W przypadku **wyrażenia warunkowego** Zastąp wartość "np. x = 5" następującym:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że wywołanie metody `String.IsNullOrEmpty(name)` jest `true`, ponieważ `name` nie ma przypisanej wartości lub ponieważ jej wartość jest ciągiem pustym (""). Zamiast wyrażenia warunkowego można także określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz pozycję **Zamknij** , aby zamknąć okno dialogowe.

1. Uruchom program z debugowaniem, naciskając klawisz **F5**.

1. W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu, aby wprowadzić swoją nazwę.

1. Ponieważ określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostało spełnione, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem metody `Console.WriteLine`.

1. Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody. W tym przypadku `Main` jest aktualnie wykonywanym metodami. Zwróć uwagę, że wartość zmiennej `name` jest `""`lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w oknie **bezpośrednim** i naciskając klawisz **Enter**. Wynik jest `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji — Visual Basic](./media/debugging-with-visual-studio/vb/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod lub wybierając pozycję **debuguj > Przełącz element menu punkt przerwania** z wybranym wierszem.

---
## <a name="step-through-a-program"></a>Przechodzenie przez program

Program Visual Studio umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania. Zwykle ustawiasz punkt przerwania i użyjesz tej funkcji do obserwowania przepływu programu za pomocą niewielkiej części kodu programu. Ponieważ program jest mały, możesz przejść przez cały program:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Na pasku menu wybierz **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.

   ![Visual Studio — Wkrocz do metody —C#](./media/debugging-with-visual-studio/step-into-method.png)

   W tym momencie okno **lokalne** pokazuje, że program ma zdefiniowaną tylko jedną zmienną, `args`. Ponieważ nie przesłano żadnych argumentów wiersza polecenia do programu, jego wartość jest pustą tablicą ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio teraz podświetla następny wiersz wykonania. Jak widać w obrazie, wykonanie kodu między ostatnią instrukcją a tym. `args` pozostaje jedyną zadeklarowaną zmienną, a okno konsoli pozostanie puste.

   ![Krok programu Visual Studio w źródle metody —C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `name` przypisanie zmiennej. Okno **lokalne** pokazuje, że `name` jest `null`, a okno konsoli wyświetla ciąg "co to jest Twoja nazwa?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale metoda <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> przechwytuje dane wejściowe.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `date` przypisanie zmiennej. Okno zmienne **lokalne** pokazuje wartość zwracaną przez wywołanie metody <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. W oknie konsoli jest również wyświetlany ciąg wprowadzony w wierszu polecenia.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Okno zmienne **lokalne** pokazuje wartość zmiennej `date` po przypisaniu z właściwości <xref:System.DateTime.Now?displayProperty=nameWithType>. Okno konsoli nie jest zmieniane.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio wywołuje metodę <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. W oknie konsoli zostanie wyświetlony sformatowany ciąg.

1. Wybierz pozycję **debuguj** > **Wyjdź** lub naciśnij klawisz **SHIFT**+**F11**. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Na pasku menu wybierz **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.

   ![Visual Studio Wkrocz do metody-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   W tym momencie okno **lokalne** pokazuje, że program ma zdefiniowaną tylko jedną zmienną, `args`. Ponieważ nie przesłano żadnych argumentów wiersza polecenia do programu, jego wartość jest pustą tablicą ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio teraz podświetla następny wiersz wykonania. Jak widać na ilustracji, pobrano mniej niż jedną milisekundę do wykonania kodu między ostatnią instrukcją a tym. `args` pozostaje jedyną zadeklarowaną zmienną, a okno konsoli pozostanie puste.

   ![Visual Studio — przejdź do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `name` przypisanie zmiennej. Okno **lokalne** pokazuje, że `name` jest `Nothing`, a okno konsoli wyświetla ciąg "co to jest Twoja nazwa?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale metoda <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> przechwytuje dane wejściowe.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `currentDate` przypisanie zmiennej. Okno zmienne **lokalne** pokazuje wartość zwracaną przez wywołanie metody <xref:System.Console.ReadLine%2A?displayProperty=nameWithType>. W oknie konsoli jest również wyświetlany ciąg wprowadzony w momencie wyświetlenia monitu o wprowadzenie do konsoli.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Okno konsoli nie jest zmieniane.

1. Wybierz pozycję **debuguj** > **Wkrocz do** lub naciśnij klawisz **F11**. Program Visual Studio wywołuje metodę <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType>. W oknie konsoli zostanie wyświetlony sformatowany ciąg.

1. Wybierz pozycję **debuguj** > **Wyjdź** lub naciśnij klawisz **SHIFT**+**F11**. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

---

## <a name="build-a-release-version"></a>Tworzenie wersji wydania

Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję publikacji. Wersja wydania obejmuje optymalizacje kompilatora, które mogą czasami mieć negatywny wpływ na działanie aplikacji. Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach wielowątkowych.

Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Zmień konfigurację kompilacji na pasku narzędzi z **Debuguj** do **Release**.

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Po naciśnięciu klawisza **F5** lub wybraniu opcji **Kompiluj rozwiązanie** z menu **kompilacja** program Visual Studio kompiluje wersję aplikacji. Można go przetestować, tak jak w przypadku wersji do debugowania.

## <a name="next-steps"></a>Następne kroki

Po zakończeniu debugowania aplikacji następnym krokiem jest opublikowanie wersji do wdrożenia aplikacji. Aby uzyskać informacje o tym, jak to zrobić, zobacz temat [publikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio](publishing-with-visual-studio.md).
