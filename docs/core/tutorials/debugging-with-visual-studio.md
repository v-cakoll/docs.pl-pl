---
title: Debugowanie aplikacji Hello world .NET Core za pomocą programu Visual Studio 2017
description: Dowiedz się, jak debugować aplikację Hello world w C# programie lub Visual Basic za pomocą programu Visual Studio 2017.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: f318c163db6cfdd6de5aa99edebfeeb4bb470a02
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926166"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Debugowanie aplikacji Hello world w języku C# lub Visual Basic .NET Core przy użyciu programu Visual Studio 2017

Do tej pory zostały wykonane kroki z sekcji [kompilowanie C# Hello World aplikacji z platformą .NET Core w programie Visual Studio 2017](with-visual-studio.md) lub [Kompilowanie Visual Basic Hello World aplikacji z platformą .net core w programie Visual Studio 2017](vb-with-visual-studio.md) w celu utworzenia i uruchomienia prostej aplikacji konsolowej. Po napisaniu i skompilowaniu aplikacji możesz rozpocząć testowanie. Program Visual Studio zawiera kompleksowy zestaw narzędzi do debugowania, których można użyć podczas testowania i rozwiązywania problemów z aplikacją. 

## <a name="debugging-in-debug-mode"></a>Debugowanie w trybie debugowania

*Debugowanie* i *wydanie* są dwiema domyślnymi konfiguracjami kompilacji programu Visual Studio. Bieżąca konfiguracja kompilacji jest pokazywana na pasku narzędzi. Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania aplikacji w trybie **debugowania** .

   ![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Należy zawsze zacząć od testowania programu w trybie debugowania. Tryb debugowania wyłącza większość optymalizacji kompilatora i zapewnia bogatsze informacje podczas procesu kompilacji.

## <a name="setting-a-breakpoint"></a>Ustawienie punktu przerwania

Uruchom program w trybie debugowania i wypróbuj kilka funkcji debugowania:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. *Punkt przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania. 

   Ustaw punkt przerwania w wierszu, który `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` odczytuje, klikając na lewym marginesie okna kod w tym wierszu lub wybierając pozycję **Debuguj** > **Przełącz punkt przerwania** w wybranym wierszu. Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwony okrąg na lewym marginesie.

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając klawisz F5 lub wybierając **Debuguj** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę i naciśnij klawisz ENTER.

1. Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania `Console.WriteLine` i przed wykonaniem metody. W oknie **samochody** są wyświetlane wartości zmiennych, które są używane wokół bieżącego wiersza. Okno zmienne **lokalne** (które można wyświetlić, klikając kartę zmienne **lokalne** ) zawiera wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.

   ![Zrzut ekranu punktu przerwania w programie Visual Studio.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Można zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program. Jeśli **okno bezpośrednie** nie jest widoczne, Wyświetl je, wybierając element menu**bezpośrednie** **debugowania** > **systemu Windows** > . **Okno bezpośrednie** umożliwia korzystanie z debugowanej aplikacji.

1. Możesz interaktywnie zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **oknie bezpośrednim** i naciśnij klawisz ENTER.

1. Wprowadź `date = new DateTime(2016,11,01,11,59,00)` w **oknie bezpośrednim** i naciśnij klawisz ENTER.

   W **oknie bezpośrednim** zostanie wyświetlona wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartości. Ponadto wartość zmiennych jest aktualizowana w oknach **Autostart** i **lokalne** .

   ![Okno autouzupełniania i okno bezpośrednie](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając element menu **Debuguj** > **Kontynuuj** . Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w **oknie bezpośrednim**.

   ![Okno konsoli z gniazdem wartości, na którym znajduje się Twoja nazwa? Monituj po wykonaniu polecenia Hello gracie](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Naciśnij dowolny klawisz, aby wyjść z aplikacji i zakończyć tryb debugowania.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. *Punkt przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania. 

   Ustaw punkt przerwania w wierszu, który `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` odczytuje, klikając na lewym marginesie okna kod w tym wierszu lub wybierając pozycję **Debuguj** > **Przełącz punkt przerwania** w wybranym wierszu. Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwony okrąg na lewym marginesie.

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, naciskając klawisz F5 lub wybierając **Debuguj** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę i naciśnij klawisz ENTER.

1. Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania `Console.WriteLine` i przed wykonaniem metody. W oknie **samochody** są wyświetlane wartości zmiennych, które są używane wokół bieżącego wiersza. Okno zmienne **lokalne** (które można wyświetlić, klikając kartę zmienne **lokalne** ) zawiera wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.

   ![Okno aplikacji programu Visual Studio w punkcie przerwania](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Można zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program. Jeśli **okno bezpośrednie** nie jest widoczne, Wyświetl je, wybierając element menu**bezpośrednie** **debugowania** > **systemu Windows** > . **Okno bezpośrednie** umożliwia korzystanie z debugowanej aplikacji.

1. Możesz interaktywnie zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **oknie bezpośrednim** i naciśnij klawisz ENTER.

1. Wprowadź `currentDate = new DateTime(2016,11,01,11,59,00)` w **oknie bezpośrednim** i naciśnij klawisz ENTER.

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi lub wybierając element menu **Debuguj** > **Kontynuuj** . Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w **oknie bezpośrednim**.

   ![Okno konsoli pokazujące zmienione wartości wprowadzone w oknie bezpośrednim](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Naciśnij dowolny klawisz, aby wyjść z aplikacji i zakończyć tryb debugowania.

---

## <a name="setting-a-conditional-breakpoint"></a>Ustawianie warunkowego punktu przerwania

Program wyświetla ciąg wprowadzony przez użytkownika. Co się stanie, jeśli użytkownik nie wprowadzi niczego? Można to sprawdzić za pomocą przydatnej funkcji debugowania, *warunkowego punktu przerwania*, który przerywa wykonywanie programu po spełnieniu jednego lub kilku warunków.

Aby ustawić warunkowy punkt przerwania i sprawdzić, co się dzieje, gdy użytkownik nie może wprowadzić ciągu, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** . Zaznacz pole **warunki**.

   ![Edytor przedstawiający panel ustawień punktu przerwania —C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. W przypadku **wyrażenia warunkowego** Zastąp wartość "np. x = = 5" następującym:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że `String.IsNullOrEmpty(name)` wywołanie metody jest `true` , ponieważ *Nazwa* nie ma przypisanej wartości lub ponieważ jej wartość jest ciągiem pustym (""). Można również określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu na podstawie takich atrybutów jako identyfikatora wątku, procesu Nazwa lub nazwa wątku.

1. Wybierz przycisk **Zamknij** , aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu, aby wprowadzić swoją nazwę.

1. Ze względu na to, `name` że warunek `null` , <xref:System.String.Empty?displayProperty=nameWithType>który określono, jest albo, został spełniony, wykonanie programu zatrzyma się `Console.WriteLine` po osiągnięciu punktu przerwania i przed wykonaniem metody.

1. Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody, która jest `Main` metodą w programie. Zwróć uwagę, że wartość `name` zmiennej to `""`lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w **oknie bezpośrednim**. Wynik to `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji —C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć tryb debugowania.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod lub wybierając pozycję **debuguj > Przełącz element menu punkt przerwania** z wybranym wierszem.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** . Zaznacz pole **warunki**.

   ![Edytor przedstawiający panel ustawień punktu przerwania — Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. W przypadku **wyrażenia warunkowego** Zastąp wartość "np. x = 5" następującym:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testujesz warunek kodu, że `String.IsNullOrEmpty(name)` wywołanie metody jest `True` , ponieważ *Nazwa* nie ma przypisanej wartości lub ponieważ jej wartość jest ciągiem pustym (""). Można również określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu na podstawie takich atrybutów jako identyfikatora wątku, procesu Nazwa lub nazwa wątku.

1. Wybierz przycisk **Zamknij** , aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu, aby wprowadzić swoją nazwę.

1. Ze względu na to, `name` że warunek `null` , <xref:System.String.Empty?displayProperty=nameWithType>który określono, jest albo, został spełniony, wykonanie programu zatrzyma się `Console.WriteLine` po osiągnięciu punktu przerwania i przed wykonaniem metody.

1. Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody, która jest `Main` metodą w programie. Zwróć uwagę, że wartość `name` zmiennej to `""`lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w **oknie bezpośrednim**. Wynik to `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji — Visual Basic](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć tryb debugowania.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod lub wybierając pozycję **debuguj > Przełącz element menu punkt przerwania** z wybranym wierszem.

---
## <a name="stepping-through-a-program"></a>Krokowe przechodzenie przez program

Program Visual Studio umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania. Zwykle ustawiasz punkt przerwania i użyjesz tej funkcji do obserwowania przepływu programu za pomocą niewielkiej części kodu programu. Ponieważ program jest mały, możesz przejść przez cały program, wykonując następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Na pasku menu wybierz **debugowanie** > **krok po kroku** lub naciśnij klawisz F11. Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.

   ![Visual Studio — Wkrocz do metody —C#](./media/debugging-with-visual-studio/step-into-method.png)

   W tym momencie okno **automatycznie** pokazuje, że program ma zdefiniowaną tylko jedną zmienną `args`. Ponieważ nie przesłano żadnych argumentów wiersza polecenia do programu, jego wartość jest pustą tablicą ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio teraz podświetla następny wiersz wykonania. Jak widać na ilustracji, pobrano mniej niż jedną milisekundę do wykonania kodu między ostatnią instrukcją a tym. `args`pozostanie jedyną zadeklarowaną zmienną, a okno konsoli pozostanie puste.

   ![Krok programu Visual Studio w źródle metody —C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio podświetla instrukcję, która `name` zawiera przypisanie zmiennej. Wyświetlone`name` zostanie okno **autostarts** , `null`a w oknie konsoli jest wyświetlany ciąg "co to jest Twoja nazwa?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz ENTER. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio podświetla instrukcję, która `date` zawiera przypisanie C#zmiennej ( `currentDate` in) lub (w Visual Basic). Okno **samochody** pokazuje <xref:System.DateTime.Now?displayProperty=nameWithType> wartość właściwości i wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli jest również wyświetlany ciąg wprowadzony w momencie wyświetlenia monitu o wprowadzenie do konsoli.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Okno **samochody** pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. Okno konsoli nie jest zmieniane.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę. Wartości `date` (lub `currentDate`) i `name` zmienne pojawiają się w oknie **samochody** , a okno konsoli wyświetla sformatowany ciąg.

1. Wybierz pozycję **Debuguj** > **lub naciśnij** klawisz Shift i klawisz F11. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć tryb debugowania.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Na pasku menu wybierz **debugowanie** > **krok po kroku** lub naciśnij klawisz F11. Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.

   ![Visual Studio Wkrocz do metody-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   W tym momencie, ponieważ nie przeszedł żadnych argumentów wiersza polecenia do programu, okno **automatycznie** pokazuje, że wartość `args` zmiennej jest pustą tablicą ciągów. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio teraz podświetla następny wiersz wykonania. Jak widać na ilustracji, pobrano mniej niż jedną milisekundę do wykonania kodu między ostatnią instrukcją a tym. `args`pozostanie jedyną zadeklarowaną zmienną, a okno konsoli pozostanie puste.

   ![Visual Studio — przejdź do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio podświetla instrukcję, która `name` zawiera przypisanie zmiennej. Wyświetlone`name` zostanie okno **autostarts** , `Nothing`a w oknie konsoli jest wyświetlany ciąg "co to jest Twoja nazwa?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz ENTER. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio podświetla instrukcję, która `date` zawiera przypisanie C#zmiennej ( `currentDate` in) lub (w Visual Basic). Okno **samochody** pokazuje <xref:System.DateTime.Now?displayProperty=nameWithType> wartość właściwości i wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli jest również wyświetlany ciąg wprowadzony w momencie wyświetlenia monitu o wprowadzenie do konsoli.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Okno **samochody** pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. Okno konsoli nie jest zmieniane.

1. Wybierz pozycję **Debuguj** > **krok** lub naciśnij klawisz F11. Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę. Wartości `date` (lub `currentDate`) i `name` zmienne pojawiają się w oknie **samochody** , a okno konsoli wyświetla sformatowany ciąg.

1. Wybierz pozycję **Debuguj** > **lub naciśnij** klawisz Shift i klawisz F11. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć tryb debugowania.

---

## <a name="building-a-release-version"></a>Tworzenie wersji wydania

Po przetestowaniu kompilacji debugowania aplikacji należy również skompilować i przetestować wersję publikacji. Wersja wydania obejmuje optymalizacje kompilatora, które mogą czasami mieć negatywny wpływ na działanie aplikacji. Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach asynchronicznych lub wielowątkowych.

Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Zmień konfigurację kompilacji na pasku narzędzi z **Debuguj** do **Release**.

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Po naciśnięciu klawisza F5 lub wybraniu opcji **Kompiluj rozwiązanie** z menu **kompilacja** program Visual Studio kompiluje wersję publikacji aplikacji konsolowej. Można go przetestować, tak jak w przypadku debugowania wersji aplikacji.

Po zakończeniu debugowania aplikacji następnym krokiem jest opublikowanie wersji do wdrożenia aplikacji. Aby uzyskać informacje o tym, jak to zrobić, zobacz temat [publikowanie aplikacji Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).
