---
title: Debugowanie aplikacji Hello World platformy .NET Core za pomocą programu Visual Studio 2017
description: Dowiedz się, jak debugować aplikację Hello World w języku C# lub Visual Basic w programie Visual Studio 2017.
ms.date: 12/15/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 9b2375443c9947a32fcccea062642103601d5010
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610720"
---
# <a name="debug-your-c-or-visual-basic-net-core-hello-world-application-using-visual-studio-2017"></a>Debugowanie usługi C# lub Visual Basic .NET Core aplikacji Hello World przy użyciu programu Visual Studio 2017

Jak dotąd wykonano kroki opisane w [kompilacji aplikacji C# Hello World z platformą .NET Core w programie Visual Studio 2017](with-visual-studio.md) lub [tworzenie aplikacji Hello World języka Visual Basic z platformą .NET Core w programie Visual Studio 2017](vb-with-visual-studio.md) do utworzenia i uruchomienia prostej aplikacji konsolowej. Po napisane i skompilowanych aplikacji, możesz rozpocząć testowanie go. Visual Studio zawiera rozbudowany zestaw narzędzi używanych podczas testowania i rozwiązywanie problemów z aplikacją do debugowania.

## <a name="debugging-in-debug-mode"></a>Debugowanie w trybie debugowania

*Debugowanie* i *wersji* są dwa domyślne programu Visual Studio konfiguracji kompilacji. Bieżącą konfigurację kompilacji jest wyświetlany na pasku narzędzi. Na poniższej ilustracji narzędzi przedstawiono, że program Visual Studio jest skonfigurowany do kompilowania aplikacji w **debugowania** trybu.

   ![domyślne narzędzi programu Visual Studio z wyróżnioną pozycją debugowania](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Należy zawsze zacząć, testując program w trybie debugowania. Debugowanie trybu wyłącza większość optymalizacji kompilatora i bogatsze informacje podczas procesu kompilacji.

## <a name="setting-a-breakpoint"></a>Ustawienie punktu przerwania

Uruchom program w trybie debugowania, a następnie spróbuj kilka funkcji debugowania:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *punktu przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wiersz zawierający punkt przerwania jest wykonywany. 

   Ustaw punkt przerwania w wierszu, który odczytuje `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` , klikając na lewym marginesie w oknie Kod w danym wierszu lub wybierając **debugowania** > **Przełącz punkt przerwania** element menu przy użyciu wiersza wybrany. Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersza, w którym ustawiono punkt przerwania, zaznaczając ją i wyświetlając czerwone kółko w jego lewym marginesie.

   ![Wizualne okno programu Studio zestaw punktu przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy użytkownik jest monitowany o podanie nazwy, a następnie naciśnij klawisz Enter.

1. Zatrzymuje wykonywanie programów, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana. **Autos** okno wyświetla wartości zmiennych, które są używane w całym bieżącego wiersza. **Lokalne** okna (który można wyświetlić, klikając **lokalne** kartę) wyświetla wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metody.

   ![Zrzut ekranu przedstawiający punkt przerwania w programie Visual Studio.](./media/debugging-with-visual-studio/breakpoint-console-window.png)

1. Można zmienić wartości zmiennych, aby zobaczyć, jak wpływa na program. Jeśli **bezpośrednim** nie jest widoczny, go wyświetlić, wybierając **debugowania** > **Windows** > **bezpośrednie**elementu menu. **Bezpośrednim** umożliwia interakcję z aplikacją debugowania.

1. Interaktywnie można zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **bezpośrednim** i naciśnij klawisz Enter.

1. Wprowadź `date = new DateTime(2016,11,01,11,59,00)` w **bezpośrednim** i naciśnij klawisz Enter.

   **Bezpośrednim** Wyświetla właściwości i wartość zmiennej ciągu <xref:System.DateTime> wartość. Ponadto wartości zmiennych jest aktualizowana w **Autos** i **lokalne** systemu windows.

   ![Okno zmiennych automatycznych i okno bezpośrednie](./media/debugging-with-visual-studio/autos-immediate-window.png)

1. Kontynuowania wykonywania programu, wybierając **Kontynuuj** przycisk na pasku narzędzi lub wybierając **debugowania** > **Kontynuuj** elementu menu. Wartości wyświetlane w oknie konsoli odnoszą się do zmian w **bezpośrednim**.

   ![Okno konsoli Wyświetla wartość gniazda w jak się Nazywasz? wiersz, a następnie Hello Gracie](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Naciśnij dowolny klawisz, aby wyjść z trybu debugowania aplikacji i na końcu.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *punktu przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wiersz zawierający punkt przerwania jest wykonywany. 

   Ustaw punkt przerwania w wierszu, który odczytuje `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` , klikając na lewym marginesie w oknie Kod w danym wierszu lub wybierając **debugowania** > **Przełącz punkt przerwania** element menu przy użyciu wiersza wybrany. Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersza, w którym ustawiono punkt przerwania, zaznaczając ją i wyświetlając czerwone kółko w jego lewym marginesie.

   ![Wizualne okno programu Studio zestaw punktu przerwania](./media/debugging-with-visual-studio/vb-set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając **debugowania** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy użytkownik jest monitowany o podanie nazwy, a następnie naciśnij klawisz Enter.

1. Zatrzymuje wykonywanie programów, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana. **Autos** okno wyświetla wartości zmiennych, które są używane w całym bieżącego wiersza. **Lokalne** okna (który można wyświetlić, klikając **lokalne** kartę) wyświetla wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metody.

   ![Visual Studio okna aplikacji w punkcie przerwania](./media/debugging-with-visual-studio/vb-stop-at-breakpoint.png)

1. Można zmienić wartości zmiennych, aby zobaczyć, jak wpływa na program. Jeśli **bezpośrednim** nie jest widoczny, go wyświetlić, wybierając **debugowania** > **Windows** > **bezpośrednie**elementu menu. **Bezpośrednim** umożliwia interakcję z aplikacją debugowania.

1. Interaktywnie można zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **bezpośrednim** i naciśnij klawisz Enter.

1. Wprowadź `currentDate = new DateTime(2016,11,01,11,59,00)` w **bezpośrednim** i naciśnij klawisz Enter.

1. Kontynuowania wykonywania programu, wybierając **Kontynuuj** przycisk na pasku narzędzi lub wybierając **debugowania** > **Kontynuuj** elementu menu. Wartości wyświetlane w oknie konsoli odnoszą się do zmian w **bezpośrednim**.

   ![Okno konsoli zmienione wartości wprowadzone w oknie bezpośrednim](./media/debugging-with-visual-studio/debug-changed-value.png)

1. Naciśnij dowolny klawisz, aby wyjść z trybu debugowania aplikacji i na końcu.
---

## <a name="setting-a-conditional-breakpoint"></a>Ustawienie warunkowego punktu przerwania

Program wyświetla ciąg, który użytkownik wprowadza. Co się stanie, jeśli użytkownik nie poda wszystko? Można to sprawdzić za pomocą przydatna funkcja debugowania *warunkowego punktu przerwania*, które podziały program wykonania, gdy dla jednego lub więcej warunki są spełnione.

Aby ustawić warunkowego punktu przerwania i testowania, co się stanie po użytkownik nie wprowadza się ciąg, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Kliknij prawym przyciskiem myszy na czerwoną kropkę, która reprezentuje punkt przerwania. W menu kontekstowym wybierz **warunki** otworzyć **ustawienia punktu przerwania** okna dialogowego. Pole wyboru dla **warunki**.

   ![Panel ustawień edytora przedstawiający punkt przerwania —C#](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Aby uzyskać **wyrażenia warunkowego** Zastąp "np. x == 5" następującym kodem:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   Testowany warunek kodu, który `String.IsNullOrEmpty(name)` jest wywołanie metody `true` albo ponieważ *nazwa* nie zostanie przypisana wartość lub jego wartość jest ciągiem pustym (""). Można również określić *liczba trafień*, które przerwania wykonywania programu, zanim instrukcja jest wykonane określoną liczbę razy, lub *warunek filtru*, który przerwań program wykonywania na podstawie na przykład atrybuty jako identyfikator wątku, nazwa procesu lub nazwę wątku.

1. Wybierz **Zamknij** przycisk, aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu wprowadź nazwę.

1. Ponieważ firma Microsoft określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostały spełnione, zatrzymuje wykonywanie programów, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana.

1. Wybierz **lokalne** okno, które znajdują się wartości zmiennych lokalnych do aktualnie wykonywanej metody, która jest `Main` metody w programach. Zauważ, że wartość `name` zmienna jest `""`, lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, wartość jest ciągiem pustym, wprowadzając następującą instrukcję w **bezpośrednim**. Wynik jest `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Okno bezpośrednie zwraca wartość true po wykonaniu instrukcji -C#](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Wybierz **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie programów.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zamknąć tryb debugowania.

1. Wyczyść punkt przerwania, klikając na kropki (.) na lewym marginesie w oknie kodu lub wybierając **Debuguj > Przełącz punkt przerwania** element menu o wybrany wiersz.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Kliknij prawym przyciskiem myszy na czerwoną kropkę, która reprezentuje punkt przerwania. W menu kontekstowym wybierz **warunki** otworzyć **ustawienia punktu przerwania** okna dialogowego. Pole wyboru dla **warunki**.

   ![Panel ustawień edytora przedstawiający punkt przerwania — języka Visual Basic](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Aby uzyskać **wyrażenia warunkowego** Zastąp "np. x = 5" następującym kodem:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Testowany warunek kodu, który `String.IsNullOrEmpty(name)` jest wywołanie metody `True` albo ponieważ *nazwa* nie zostanie przypisana wartość lub jego wartość jest ciągiem pustym (""). Można również określić *liczba trafień*, które przerwania wykonywania programu, zanim instrukcja jest wykonane określoną liczbę razy, lub *warunek filtru*, który przerwań program wykonywania na podstawie na przykład atrybuty jako identyfikator wątku, nazwa procesu lub nazwę wątku.

1. Wybierz **Zamknij** przycisk, aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu wprowadź nazwę.

1. Ponieważ firma Microsoft określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostały spełnione, zatrzymuje wykonywanie programów, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana.

1. Wybierz **lokalne** okno, które znajdują się wartości zmiennych lokalnych do aktualnie wykonywanej metody, która jest `Main` metody w programach. Zauważ, że wartość `name` zmienna jest `""`, lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, wartość jest ciągiem pustym, wprowadzając następującą instrukcję w **bezpośrednim**. Wynik jest `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

  ![Zwraca wartość true po instrukcji jest wykonywany — Visual Basic okno bezpośrednie](./media/debugging-with-visual-studio/vb-immediate-window-output.png)

1. Wybierz **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie programów.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zamknąć tryb debugowania.

1. Wyczyść punkt przerwania, klikając na kropki (.) na lewym marginesie w oknie kodu lub wybierając **Debuguj > Przełącz punkt przerwania** element menu o wybrany wiersz.
---
## <a name="stepping-through-a-program"></a>Krokowe wykonywanie programu

Program Visual Studio umożliwia również przejrzeć wiersz po wierszu programu i monitorować jej wykonanie. Zwykle będzie Ustaw punkt przerwania i postępuj zgodnie z przepływem programu za pomocą niewielką część kodu źródłowego za pomocą tej funkcji. Ponieważ program jest mała, możesz przejrzeć całego programu, wykonując następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Na pasku menu wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Visual Studio wyróżnia i wyświetla strzałkę obok pozycji następnego wiersza wykonywania.

   ![Visual Studio krok po kroku — — metodaC#](./media/debugging-with-visual-studio/step-into-method.png)

   W tym momencie **Autos** okno pokazuje, czy program został zdefiniowany tylko jednej zmiennej `args`. Ponieważ żadnych argumentów wiersza polecenia nie zostały przekazane do programu, jego wartość jest pustą tablicę ciągów. Ponadto program Visual Studio zostało otwarte okno konsoli pusty.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio są teraz wyróżniane wykonanie następnego wiersza. Jak pokazano na rysunku, trzeba było poświęcić mniejszym niż jedna milisekunda na wykonanie kodu między ostatnią instrukcję, a ten drugi. `args` pozostaje tylko zadeklarowana zmienna, a następnie w oknie konsoli pozostanie puste.

   ![Program Visual Studio kroku w źródle metoda-C#](./media/debugging-with-visual-studio/step-into-source-method.png)

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wyróżnia instrukcji, która obejmuje `name` przypisanie zmiennej. **Autos** okno pokazuje, że `name` jest `null`, i w oknie konsoli zostaną wyświetlone ciąg "Co to jest Twoja nazwa?".

1. Odpowiadanie do wiersza polecenia, wprowadzając ciąg w oknie konsoli, a następnie naciskając klawisz Enter. Konsola nie odpowiada, a ciąg, możesz wprowadzić nie są wyświetlane w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda jednak będzie przechwytywać dane wejściowe.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wyróżnia instrukcji, która obejmuje `date` (w języku C#) lub `currentDate` (w języku Visual Basic) przypisanie zmiennej. **Autos** Pokazuje okno <xref:System.DateTime.Now?displayProperty=nameWithType> wartości właściwości i wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli wyświetlane są również ciąg wprowadzona podczas konsoli zostanie wyświetlony monit o wprowadzenie danych.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. **Autos** okno pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. W oknie konsoli ulega zmianie.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Wartości `date` (lub `currentDate`) i `name` zmienne są wyświetlane w **Autos** okna i okna konsoli Wyświetla sformatowany ciąg.

1. Wybierz **debugowania** > **Step Out** lub naciśnij klawisz Shift i klawisz F11. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zamknąć tryb debugowania.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Na pasku menu wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Visual Studio wyróżnia i wyświetla strzałkę obok pozycji następnego wiersza wykonywania.

   ![Visual Studio krok po kroku metody - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   W tym momencie ponieważ żadnych argumentów wiersza polecenia nie zostały przekazane do programu, **Autos** okno pokazuje, że wartość `args` zmienna jest tablicą pusty ciąg. Ponadto program Visual Studio zostało otwarte okno konsoli pusty.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio są teraz wyróżniane wykonanie następnego wiersza. Jak pokazano na rysunku, trzeba było poświęcić mniejszym niż jedna milisekunda na wykonanie kodu między ostatnią instrukcję, a ten drugi. `args` pozostaje tylko zadeklarowana zmienna, a następnie w oknie konsoli pozostanie puste.

   ![Visual Studio krok po kroku metoda źródła - Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wyróżnia instrukcji, która obejmuje `name` przypisanie zmiennej. **Autos** okno pokazuje, że `name` jest `Nothing`, i w oknie konsoli zostaną wyświetlone ciąg "Co to jest Twoja nazwa?".

1. Odpowiadanie do wiersza polecenia, wprowadzając ciąg w oknie konsoli, a następnie naciskając klawisz Enter. Konsola nie odpowiada, a ciąg, możesz wprowadzić nie są wyświetlane w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metoda jednak będzie przechwytywać dane wejściowe.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wyróżnia instrukcji, która obejmuje `date` (w języku C#) lub `currentDate` (w języku Visual Basic) przypisanie zmiennej. **Autos** Pokazuje okno <xref:System.DateTime.Now?displayProperty=nameWithType> wartości właściwości i wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli wyświetlane są również ciąg wprowadzona podczas konsoli zostanie wyświetlony monit o wprowadzenie danych.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. **Autos** okno pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. W oknie konsoli ulega zmianie.

1. Wybierz **debugowania** > **Step Into** lub nacisnąć klawisz F11. Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Wartości `date` (lub `currentDate`) i `name` zmienne są wyświetlane w **Autos** okna i okna konsoli Wyświetla sformatowany ciąg.

1. Wybierz **debugowania** > **Step Out** lub naciśnij klawisz Shift i klawisz F11. Spowoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zamknąć tryb debugowania.
---

## <a name="building-a-release-version"></a>Tworzenie wersji wydania

Po przetestowaniu kompilacji debugowania aplikacji, należy również skompilować i przetestować wersję wydania. Wersja zawiera optymalizacje kompilatora, które może czasami negatywnie wpłynąć na zachowanie aplikacji. Na przykład optymalizacje kompilatora, które są przeznaczone do zwiększenia wydajności, można utworzyć wyścigu w aplikacjach asynchronicznych lub wielowątkowych.

Aby skompilować i przetestować wersji aplikacji konsolowej, zmień konfigurację kompilacji na pasku narzędzi z **debugowania** do **wersji**.

![domyślne narzędzi programu Visual Studio z wyróżnioną pozycją debugowania](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Po naciśnięciu klawisza F5 lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu programu Visual Studio kompiluje wersji aplikacji konsoli. Można go przetestować, tak jak wersji debugowania aplikacji.

Po zakończeniu debugowania aplikacji, następnym krokiem jest opublikowanie wdrażanym wersji aplikacji. Aby uzyskać informacje, jak to zrobić, zobacz [publikowanie aplikacji Hello World w programie Visual Studio 2017](publishing-with-visual-studio.md).
