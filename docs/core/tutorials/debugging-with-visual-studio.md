---
title: Debugowanie aplikacji C# lub Visual Basic Hello World .NET Core z programu Visual Studio 2017 r.
description: Dowiedz się, jak można debugować aplikacji Hello World, napisany w języku C# lub Visual Basic z programu Visual Studio 2017 r.
author: BillWagner
ms.author: wiwagn
ms.date: 12/15/2017
ms.openlocfilehash: 3c130c2eebdf79c1db171cb2171aa68dfff728a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218433"
---
# <a name="debug-your-hello-world-application-with-visual-studio-2017"></a>Debugowanie aplikacji Hello World z programu Visual Studio 2017 r.

Do tej pory zostały wykonane kroki w [kompilacji aplikacji C# Hello World z platformą .NET Core w Visual Studio 2017](.\with-visual-studio.md) lub [kompilacji aplikacji Hello World Visual Basic z platformą .NET Core w Visual Studio 2017](vb-with-visual-studio.md) do utworzenia i uruchom prostej aplikacji konsolowej. Po zapisane i skompilować aplikację, możesz rozpocząć testowanie go. Visual Studio zawiera rozbudowany zestaw narzędzia debugowania, które można używać podczas testowania i rozwiązywania problemów aplikacji.

## <a name="debugging-in-debug-mode"></a>Debugowanie w trybie debugowania

*Debugowanie* i *wersji* są dwa domyślne Visual Studio konfiguracje kompilacji. Bieżąca konfiguracja kompilacji jest wyświetlana na pasku narzędzi. Na poniższej ilustracji narzędzi pokazuje, że Visual Studio jest skonfigurowany do skompilowania aplikacji w **debugowania** tryb.

   ![Visual Studio paska narzędzi](./media/debugging-with-visual-studio/toolbar1.png)

Zawsze należy rozpocząć testując program w trybie debugowania. Debugowanie trybu wyłącza optymalizacje kompilatora większości i bardziej rozbudowane informacje podczas procesu kompilacji.

## <a name="setting-a-breakpoint"></a>Ustawienia punktu przerwania

Uruchom program w trybie debugowania, a następnie spróbuj kilka funkcji do debugowania:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. A *punktu przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wiersz zawierający punkt przerwania jest wykonywana. 

   Ustaw punkt przerwania w wierszu `Console.WriteLine($"\nHello, {name}, on {date:d} at {date:t}!");` , klikając na lewym marginesie okna kodu, w tym wierszu lub wybierając **debugowania** > **Przełącz punkt przerwania** element menu z wiersza wybrany. Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersz, w którym punkt przerwania jest ustawiony przez podświetlenie i wyświetlanie czerwone koło jego lewym marginesie.

   ![Visual Studio Program okna z zestawem punktu przerwania](./media/debugging-with-visual-studio/setbreakpoint.png)

1. Uruchom program w trybie debugowania, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybranie **debugowania** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy użytkownik jest monitowany o nazwę, a następnie naciśnij klawisz Enter.

1. Zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana. **Automatycznych** wyświetlane wartości zmiennych, które są używane wokół bieżącego wiersza. **Zmiennych lokalnych** okna (które można wyświetlić, klikając **zmiennych lokalnych** kartę) wyświetla wartości zmiennych, które są zdefiniowane w metodzie aktualnie wykonywane.

   ![Okno aplikacji w usłudze Visual Studio](./media/debugging-with-visual-studio/break.png)

1. Można zmienić wartości zmiennych, aby zobaczyć, jak wpływa na program. Jeśli **oknie bezpośrednim** nie jest widoczny, wyświetl ją, wybierając **debugowania** > **Windows** > **Immediate**elementu menu. **Oknie bezpośrednim** umożliwia interakcję z aplikacją debugowanie.

1. Interaktywnie można zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **oknie bezpośrednim** i naciśnij klawisz Enter.

1. Wprowadź `date = new DateTime(2016,11,01,11,59,00)` w **oknie bezpośrednim** i naciśnij klawisz Enter.

   **Oknie bezpośrednim** Wyświetla wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartość. Ponadto zaktualizowane wartości zmiennych w **automatycznych** i **zmiennych lokalnych** systemu windows.

   ![Okno zmiennych automatycznych oraz w oknie bezpośrednim](./media/debugging-with-visual-studio/autosimmediate.png)

1. Kontynuować działanie programu, wybierając **Kontynuuj** przycisku w pasku narzędzi lub wybierając **debugowania** > **Kontynuuj** elementu menu. Wartości wyświetlane w oknie konsoli odpowiadają zmiany wprowadzone w **oknie bezpośrednim**.

   ![Wartość typu gniazda co to jest nazwa wyświetlana w oknie konsoli? wiersz następuje Hello Gracie na 2016-11-1 11:59:00](./media/debugging-with-visual-studio/changed.png)

1. Naciśnij dowolny klawisz, aby wyjść z trybu debugowania aplikacji i na końcu.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. A *punktu przerwania* tymczasowo przerywa wykonywanie aplikacji *przed* wiersz zawierający punkt przerwania jest wykonywana. 

   Ustaw punkt przerwania w wierszu `Console.WriteLine(vbCrLf + $"Hello, {name}, on {currentDate:d} at {currentDate:t}!")` , klikając na lewym marginesie okna kodu, w tym wierszu lub wybierając **debugowania** > **Przełącz punkt przerwania** element menu z wiersza wybrany. Jak pokazano na poniższej ilustracji, Visual Studio wskazuje wiersz, w którym punkt przerwania jest ustawiony przez podświetlenie i wyświetlanie czerwone koło jego lewym marginesie.

   ![Visual Studio Program okna z zestawem punktu przerwania](./media/debugging-with-visual-studio/vb-setbreakpoint.png)

1. Uruchom program w trybie debugowania, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybranie **debugowania** > **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy użytkownik jest monitowany o nazwę, a następnie naciśnij klawisz Enter.

1. Zatrzymuje wykonanie programu, po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana. **Automatycznych** wyświetlane wartości zmiennych, które są używane wokół bieżącego wiersza. **Zmiennych lokalnych** okna (które można wyświetlić, klikając **zmiennych lokalnych** kartę) wyświetla wartości zmiennych, które są zdefiniowane w metodzie aktualnie wykonywane.

   ![Okno aplikacji w usłudze Visual Studio](./media/debugging-with-visual-studio/vb-break.png)

1. Można zmienić wartości zmiennych, aby zobaczyć, jak wpływa na program. Jeśli **oknie bezpośrednim** nie jest widoczny, wyświetl ją, wybierając **debugowania** > **Windows** > **Immediate**elementu menu. **Oknie bezpośrednim** umożliwia interakcję z aplikacją debugowanie.

1. Interaktywnie można zmienić wartości zmiennych. Wprowadź `name = "Gracie"` w **oknie bezpośrednim** i naciśnij klawisz Enter.

1. Wprowadź `currentDate = new DateTime(2016,11,01,11,59,00)` w **oknie bezpośrednim** i naciśnij klawisz Enter.

1. Kontynuować działanie programu, wybierając **Kontynuuj** przycisku w pasku narzędzi lub wybierając **debugowania** > **Kontynuuj** elementu menu. Wartości wyświetlane w oknie konsoli odpowiadają zmiany wprowadzone w **oknie bezpośrednim**.

   ![Okno konsoli wartości zmiany wprowadzone w oknie bezpośrednim](./media/debugging-with-visual-studio/changed.png)

1. Naciśnij dowolny klawisz, aby wyjść z trybu debugowania aplikacji i na końcu.
---

## <a name="setting-a-conditional-breakpoint"></a>Ustawienie warunkowych punktów przerwania

Program wyświetla ciąg wprowadzonych przez użytkownika. Co się stanie, jeśli użytkownik nie wypełniać? Można to sprawdzić za pomocą przydatne funkcji debugowania *warunkowych punktów przerwania*, które podziały program wykonywania, gdy dla jednego lub więcej warunki są spełnione.

Aby ustawić warunkowe punktu przerwania i przetestować, co się dzieje, gdy użytkownik nie wprowadź ciąg, wykonaj następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Kliknij prawym przyciskiem myszy na czerwonej kropki, który reprezentuje punkt przerwania. W menu kontekstowym wybierz **warunki** otworzyć **ustawienia punktów przerwania** okna dialogowego. Pole wyboru dla **warunki**.

   ![Panel ustawień punktu przerwania](./media/debugging-with-visual-studio/breakpointsettings.png)

1. Dla **wyrażenia warunkowego** Zastąp "np. x == 5" następującym kodem:

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   W przypadku testowania dla warunku kodu, który `String.IsNullOrEmpty(name)` jest wywołanie metody `true` albo ponieważ *nazwa* nie zostanie przypisana wartość lub jego wartość jest pustym ciągiem (""). Można również określić *liczba trafień*, które przerwań program wykonywania przed instrukcja jest wykonywane przez określoną liczbę razy, lub *warunek filtru*, który wykonanie oparte na przykład program przerwań atrybuty jako identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz **zamknąć** przycisk, aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu o wprowadzenie nazwy.

1. Ponieważ firma Microsoft określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostały spełnione, zatrzymuje wykonywanie programu po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana.

1. Wybierz **zmiennych lokalnych** okna, które zawiera wartości zmiennych, które znajdują się lokalnie do aktualnie realizowanej metodę, która jest `Main` metody w programie. Sprawdź, że wartość `name` zmienna jest `""`, lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, wartość jest pustym ciągiem, wprowadzając następującą instrukcję w **oknie bezpośrednim**. Wynik jest `true`.

   ```csharp
   ? name == String.Empty
   ```

   ![Zwraca wartość true, po wykonaniu instrukcji okno bezpośrednie](./media/debugging-with-visual-studio/emptystring.png)

1. Wybierz **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć działanie w trybie debugowania.

1. Usuń punkt przerwania, klikając kropki (.) na lewym marginesie okna kodu lub wybierając **debugowania > Przełącz punkt przerwania** element menu o wybrany wiersz.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Kliknij prawym przyciskiem myszy na czerwonej kropki, który reprezentuje punkt przerwania. W menu kontekstowym wybierz **warunki** otworzyć **ustawienia punktów przerwania** okna dialogowego. Pole wyboru dla **warunki**.

   ![Panel ustawień punktu przerwania](./media/debugging-with-visual-studio/vb-breakpointsettings.png)

1. Dla **wyrażenia warunkowego** Zastąp "np. x = 5" następującym kodem:

   ```vb
   String.IsNullOrEmpty(name)
   ```

   W przypadku testowania dla warunku kodu, który `String.IsNullOrEmpty(name)` jest wywołanie metody `True` albo ponieważ *nazwa* nie zostanie przypisana wartość lub jego wartość jest pustym ciągiem (""). Można również określić *liczba trafień*, które przerwań program wykonywania przed instrukcja jest wykonywane przez określoną liczbę razy, lub *warunek filtru*, który wykonanie oparte na przykład program przerwań atrybuty jako identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz **zamknąć** przycisk, aby zamknąć okno dialogowe.

1. Uruchom program w trybie debugowania.

1. W oknie konsoli naciśnij klawisz Enter po wyświetleniu monitu o wprowadzenie nazwy.

1. Ponieważ firma Microsoft określony warunek, `name` jest `null` lub <xref:System.String.Empty?displayProperty=nameWithType>, zostały spełnione, zatrzymuje wykonywanie programu po osiągnięciu punktu przerwania i przed `Console.WriteLine` metoda jest wykonywana.

1. Wybierz **zmiennych lokalnych** okna, które zawiera wartości zmiennych, które znajdują się lokalnie do aktualnie realizowanej metodę, która jest `Main` metody w programie. Sprawdź, że wartość `name` zmienna jest `""`, lub <xref:System.String.Empty?displayProperty=nameWithType>.

1. Upewnij się, wartość jest pustym ciągiem, wprowadzając następującą instrukcję w **oknie bezpośrednim**. Wynik jest `true`.

   ```vb
   ? String.IsNullOrEmpty(name)
   ```
  ![Zwraca wartość true, po wykonaniu instrukcji okno bezpośrednie](./media/debugging-with-visual-studio/vb-emptystring.png)

1. Wybierz **Kontynuuj** przycisk na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć działanie w trybie debugowania.

1. Usuń punkt przerwania, klikając kropki (.) na lewym marginesie okna kodu lub wybierając **debugowania > Przełącz punkt przerwania** element menu o wybrany wiersz.
---
## <a name="stepping-through-a-program"></a>Krokowe wykonywanie programu

Program Visual Studio umożliwia również kroku wiersz po wierszu za pośrednictwem programu i monitorować jego wykonywania. Zwykle będzie Ustaw punkt przerwania i wykonaj przepływem programu, chociaż niewielką częścią kodu źródłowego za pomocą tej funkcji. Ponieważ program jest mały, można przejrzeć całego programu, wykonując następujące czynności:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)
1. Na pasku menu wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia i wyświetla strzałkę obok następnego wiersza wykonywania.

   ![Visual Studio okna](./media/debugging-with-visual-studio/stepinto1.png)

   W tym momencie **automatycznych** okna pokazuje, że program został zdefiniowany tylko jedną zmienną `args`. Ponieważ żadnych argumentów wiersza polecenia nie zostały przekazane do programu, jego wartość wynosi tablicy pusty ciąg. Ponadto Visual Studio zostało otwarte okno konsoli puste.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio teraz prezentuje wykonanie następnego wiersza. Jak pokazano na rysunku, trwało mniej niż jednej milisekundy na wykonanie kodu od ostatniej instrukcji i to jeden. `args` pozostaje tylko zadeklarowana zmienna, a w oknie konsoli pozostanie puste.

   ![Visual Studio okna](./media/debugging-with-visual-studio/stepinto2.png)

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia instrukcji, która obejmuje `name` przypisanie zmiennej. **Automatycznych** okna wskazuje, że `name` jest `null`, i w oknie konsoli wyświetla ciąg "Co to jest nazwa?".

1. Odpowiadanie na ten monit wpisując ciąg w oknie konsoli i naciskając klawisz Enter. Konsola nie odpowiada, a ciąg, możesz wprowadzić nie są wyświetlane w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody niemniej przechwytywania dane wejściowe.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia instrukcji, która obejmuje `date` (w języku C#) lub `currentDate` (w języku Visual Basic) przypisanie zmiennej. **Automatycznych** Pokazuje okno <xref:System.DateTime.Now?displayProperty=nameWithType> wartość właściwości i wartość zwrócona przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli wyświetla również ciąg wprowadzana w trakcie konsoli zostanie wyświetlony monit o wprowadzenie danych.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. **Automatycznych** okno zawiera wartość `date` zmiennej po przypisanie z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. W oknie konsoli jest bez zmian.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Wywołuje program Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Wartości `date` (lub `currentDate`) i `name` zmienne są wyświetlane w **automatycznych** okna, a następnie w oknie konsoli jest wyświetlany ciąg sformatowany.

1. Wybierz **debugowania** > **Wyjdź** lub naciśnij klawisz Shift i klawisz F11. Powoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć działanie w trybie debugowania.
# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)
1. Na pasku menu wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia i wyświetla strzałkę obok następnego wiersza wykonywania.

   ![Visual Studio okna](./media/debugging-with-visual-studio/vb-stepinto1.png)

   W tym momencie ponieważ żadnych argumentów wiersza polecenia nie zostały przekazane do programu, **automatycznych** okna wskazuje, że wartość `args` zmienna jest tablicą pusty ciąg. Ponadto Visual Studio zostało otwarte okno konsoli puste.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio teraz prezentuje wykonanie następnego wiersza. Jak pokazano na rysunku, trwało mniej niż jednej milisekundy na wykonanie kodu od ostatniej instrukcji i to jeden. `args` pozostaje tylko zadeklarowana zmienna, a w oknie konsoli pozostanie puste.

   ![Visual Studio okna](./media/debugging-with-visual-studio/vb-stepinto2.png)

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia instrukcji, która obejmuje `name` przypisanie zmiennej. **Automatycznych** okna wskazuje, że `name` jest `Nothing`, i w oknie konsoli wyświetla ciąg "Co to jest nazwa?".

1. Odpowiadanie na ten monit wpisując ciąg w oknie konsoli i naciskając klawisz Enter. Konsola nie odpowiada, a ciąg, możesz wprowadzić nie są wyświetlane w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody niemniej przechwytywania dane wejściowe.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Visual Studio wyróżnia instrukcji, która obejmuje `date` (w języku C#) lub `currentDate` (w języku Visual Basic) przypisanie zmiennej. **Automatycznych** Pokazuje okno <xref:System.DateTime.Now?displayProperty=nameWithType> wartość właściwości i wartość zwrócona przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli wyświetla również ciąg wprowadzana w trakcie konsoli zostanie wyświetlony monit o wprowadzenie danych.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. **Automatycznych** okno zawiera wartość `date` zmiennej po przypisanie z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. W oknie konsoli jest bez zmian.

1. Wybierz **debugowania** > **Step Into** lub naciśnij klawisz F11. Wywołuje program Visual Studio <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metody. Wartości `date` (lub `currentDate`) i `name` zmienne są wyświetlane w **automatycznych** okna, a następnie w oknie konsoli jest wyświetlany ciąg sformatowany.

1. Wybierz **debugowania** > **Wyjdź** lub naciśnij klawisz Shift i klawisz F11. Powoduje to zatrzymanie wykonywania krok po kroku. W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zakończyć działanie w trybie debugowania.
---

## <a name="building-a-release-version"></a>Tworzenie wersji

Po przeprowadzeniu testów z kompilacji debugowania aplikacji, należy również skompilować i przetestować wersji. Wersja zawiera optymalizacje kompilatora, które może czasami negatywnie wpłynąć na zachowanie aplikacji. Na przykład w aplikacjach asynchronicznych lub wielowątkowe warunki wyścigu można tworzyć optymalizacje kompilatora, które są zaprojektowane do zwiększenia wydajności.

Tworzenie i testowanie wersji aplikacji konsoli, zmień konfigurację kompilacji, na pasku narzędzi z **debugowania** do **wersji**.

![Obraz](./media/debugging-with-visual-studio/toolbar2.png)

Gdy naciśnij klawisz F5 lub wybierz **Kompiluj rozwiązanie** z **kompilacji** menu programu Visual Studio kompiluje wersji aplikacji konsoli. Można przetestować go tak samo jak wersja do debugowania aplikacji.

Po zakończeniu debugowania aplikacji, następnym krokiem jest opublikować wersję można wdrożyć aplikacji. Aby uzyskać informacje, jak to zrobić, zobacz [publikowanie aplikacji Hello World z programu Visual Studio 2017](./publishing-with-visual-studio.md).
