---
title: Debugowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio
description: Dowiedz się, jak debugować aplikację konsolową .NET Core za pomocą programu Visual Studio.
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4bd2a8a0e4b3cea55e209306dd3788552e4b61f3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005417"
---
# <a name="tutorial-debug-a-net-core-console-application-using-visual-studio"></a>Samouczek: debugowanie aplikacji konsolowej .NET Core przy użyciu programu Visual Studio

W tym samouczku przedstawiono narzędzia debugowania dostępne w programie Visual Studio.

## <a name="prerequisites"></a>Wymagania wstępne

- Ten samouczek współpracuje z aplikacją konsolową utworzoną w temacie [Tworzenie aplikacji konsolowej platformy .NET Core w programie Visual Studio 2019](with-visual-studio.md).

## <a name="debug-build-configuration"></a>Debuguj konfigurację kompilacji

*Debugowanie* i *wydanie* są dwiema domyślnymi konfiguracjami kompilacji programu Visual Studio. Bieżąca konfiguracja kompilacji jest pokazywana na pasku narzędzi. Poniższy obraz paska narzędzi pokazuje, że program Visual Studio jest skonfigurowany do kompilowania wersji do debugowania aplikacji:

![Pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-debug.png)

Zacznij od uruchomienia wersji debugowania aplikacji. Konfiguracja kompilacji debugowania powoduje wyłączenie większości optymalizacji kompilatora i zapewnia bogatsze informacje podczas procesu kompilacji.

## <a name="set-a-breakpoint"></a>Ustawianie punktu przerwania

<!-- markdownlint-disable MD025 -->

1. Ustaw *punkt przerwania* w wierszu, który wyświetla nazwę, datę i godzinę, klikając na lewym marginesie okna kod w tym wierszu. Innym sposobem ustawienia punktu przerwania jest umieszczenie kursora w wierszu kodu, a następnie naciśnięcie klawisza **F9** lub wybranie polecenia **Debuguj**  >  **Przełącz punkt przerwania** z paska menu.

   Punkt przerwania tymczasowo przerywa wykonywanie aplikacji *przed* wykonaniem wiersza z punktem przerwania.

   Jak widać na poniższej ilustracji, program Visual Studio wskazuje wiersz, w którym jest ustawiony punkt przerwania, zaznaczając go i wyświetlając czerwoną kropkę na lewym marginesie.

   ![Okno programu Visual Studio z ustawionym punktem przerwania](./media/debugging-with-visual-studio/set-breakpoint-in-editor.png)

1. Uruchom program w trybie debugowania, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi. Innymi sposobami rozpoczęcia debugowania są naciśnięcie klawisza **F5** lub wybranie polecenia **Debuguj**  >  **Rozpocznij debugowanie**.

1. Wprowadź ciąg w oknie konsoli, gdy program zapyta o nazwę, a następnie naciśnij klawisz **Enter**.

1. Wykonanie programu zostaje zatrzymane po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody. W oknie **Ustawienia lokalne** są wyświetlane wartości zmiennych, które są zdefiniowane w aktualnie wykonywanej metodzie.

   ![Zrzut ekranu punktu przerwania w programie Visual Studio](./media/debugging-with-visual-studio/breakpoint-hit.png)

1. Okno **bezpośrednie** umożliwia korzystanie z debugowanej aplikacji. Możesz interaktywnie zmienić wartość zmiennych, aby zobaczyć, jak ma to wpływ na program.

   1. Jeśli okno **bezpośrednie** nie jest widoczne, Wyświetl je, wybierając pozycję **Debuguj**  >  **Windows**  >  **natychmiast**Windows.

   1. Wprowadź `name = "Gracie"` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   1. Wprowadź `date = DateTime.Parse("2019-11-16T17:25:00Z").ToUniversalTime()` w oknie **bezpośrednim** i naciśnij klawisz **Enter** .

   W oknie **bezpośrednim** zostanie wyświetlona wartość zmiennej ciągu i właściwości <xref:System.DateTime> wartości. Ponadto wartości zmiennych są aktualizowane w oknie **zmiennych lokalnych** .

   ![Lokalne i natychmiastowe okna w programie Visual Studio 2019](./media/debugging-with-visual-studio/locals-immediate-window.png)

1. Kontynuuj wykonywanie programu, wybierając przycisk **Kontynuuj** na pasku narzędzi. Innym sposobem na kontynuowanie jest wybranie opcji **Debuguj**  >  **Kontynuuj**.

   Wartości wyświetlane w oknie konsoli odpowiadają zmianom wprowadzonym w oknie **bezpośrednim** .

   ![Okno konsoli pokazujące wprowadzone wartości](./media/debugging-with-visual-studio/console-window.png)

1. Naciśnij dowolny klawisz, aby zamknąć aplikację i zatrzymać debugowanie.

## <a name="set-a-conditional-breakpoint"></a>Ustaw punkt przerwania warunkowego

Program wyświetla ciąg wprowadzony przez użytkownika. Co się stanie, jeśli użytkownik nie wprowadzi niczego? Można to sprawdzić za pomocą przydatnej funkcji debugowania nazywanej *warunkowym punktem przerwania*, która przerywa wykonywanie programu po spełnieniu jednego lub kilku warunków.

Aby ustawić warunkowy punkt przerwania i sprawdzić, co się dzieje, gdy użytkownik nie może wprowadzić ciągu, wykonaj następujące czynności:

1. Kliknij prawym przyciskiem myszy czerwoną kropkę reprezentującą punkt przerwania. W menu kontekstowym wybierz pozycję **warunki** , aby otworzyć okno dialogowe **Ustawienia punktu przerwania** . Wybierz pole **warunki** , jeśli nie zostało jeszcze wybrane.

   ![Edytor przedstawiający panel ustawień punktu przerwania-C #](./media/debugging-with-visual-studio/breakpoint-settings.png)

1. Dla **wyrażenia warunkowego**wprowadź w polu poniższy kod, który pokazuje przykładowy kod, który sprawdza, czy `x` jest 5. Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.

   ```csharp
   String.IsNullOrEmpty(name)
   ```

   ```vb
   String.IsNullOrEmpty(name)
   ```

   Za każdym razem, gdy punkt przerwania został trafiony, debuger wywołuje `String.IsNullOrEmpty(name)` metodę i przerywa w tym wierszu tylko wtedy, gdy wywołanie metody zwróci wartość `true` .

   Zamiast wyrażenia warunkowego można określić *liczbę trafień*, która przerywa wykonywanie programu, zanim instrukcja zostanie wykonana określoną liczbę razy lub *warunek filtru*, który przerywa wykonywanie programu w oparciu o takie atrybuty jak identyfikator wątku, nazwa procesu lub nazwa wątku.

1. Wybierz pozycję **Zamknij** , aby zamknąć okno dialogowe.

1. Uruchom program z debugowaniem, naciskając klawisz **F5**.

1. W oknie konsoli naciśnij klawisz **Enter** po wyświetleniu monitu, aby wprowadzić swoją nazwę.

1. Ponieważ określony warunek ( `name` is `null` lub <xref:System.String.Empty?displayProperty=nameWithType> ) został spełniony, wykonanie programu zatrzyma się po osiągnięciu punktu przerwania i przed wykonaniem `Console.WriteLine` metody.

1. Wybierz okno zmienne **lokalne** , które pokazuje wartości zmiennych, które są lokalne dla aktualnie wykonywanej metody. W tym przypadku `Main` jest obecnie wykonywana metoda. Zwróć uwagę, że wartość `name` zmiennej to `""` lub <xref:System.String.Empty?displayProperty=nameWithType> .

1. Potwierdź, że wartość jest pustym ciągiem, wprowadzając poniższą instrukcję w oknie **bezpośrednim** i naciskając klawisz **Enter**. Wynik to `true` .

   ```csharp
   ? name == String.Empty
   ```

   ```vb
   ? String.IsNullOrEmpty(name)
   ```

   Znak zapytania kieruje okno bezpośrednie do [obliczenia wyrażenia](/visualstudio/ide/reference/immediate-window#enter-commands).

   ![Bezpośrednie okno zwracające wartość true po wykonaniu instrukcji-C #](./media/debugging-with-visual-studio/immediate-window-output.png)

1. Wybierz przycisk **Kontynuuj** na pasku narzędzi, aby kontynuować wykonywanie programu.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

1. Wyczyść punkt przerwania, klikając kropkę na lewym marginesie okna kod. Innym sposobem na wyczyszczenie punktu przerwania jest wybranie opcji **debuguj > przełączenia punktu przerwania** podczas wybierania wiersza kodu.

## <a name="step-through-a-program"></a>Przechodzenie przez program

Program Visual Studio umożliwia również krok po kroku w wierszu przez program i monitorowanie jego wykonania. Zwykle ustawiasz punkt przerwania i obserwuj przepływ programu za pomocą niewielkiej części kodu programu. Ponieważ program jest mały, możesz przejść przez cały program.

1. Wybierz pozycję **Debuguj**  >  **krok do**. Innym sposobem debugowania jednej instrukcji w danym momencie jest naciśnięcie klawisza **F11**.

   Program Visual Studio podświetla i wyświetli strzałkę obok następnego wiersza wykonania.

   C#

   ![Visual Studio Wkrocz do metody-C #](./media/debugging-with-visual-studio/step-into-method.png)

   Visual Basic

   ![Visual Studio Wkrocz do metody-Visual Basic](./media/debugging-with-visual-studio/vb-step-into-method.png)

   W tym momencie okno zmienne **lokalne** pokazuje, że `args` Tablica jest pusta i `name` i `date` ma wartości domyślne. Ponadto program Visual Studio otworzył puste okno konsoli.

1. Naciśnij klawisz **F11**. Program Visual Studio teraz podświetla następny wiersz wykonania. Okno **zmiennych lokalnych** jest niezmienione, a okno konsoli pozostanie puste.

   C#

   ![Visual Studio — krok w źródle metody — C #](./media/debugging-with-visual-studio/step-into-source-method.png)

   Visual Basic

   ![Visual Studio — przejdź do źródła metody — Visual Basic](./media/debugging-with-visual-studio/vb-step-into-source-method.png)

1. Naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `name` przypisanie zmiennej. Zostanie wyświetlone okno **Ustawienia lokalne** `name` , które ma wartość `null` , a w oknie konsoli jest wyświetlany ciąg "co to jest Twoja nazwa?".

1. Odpowiedz na monit, wprowadzając ciąg w oknie konsoli i naciskając klawisz **Enter**. Konsola nie odpowiada, a wprowadzony ciąg nie jest wyświetlany w oknie konsoli, ale <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> Metoda przechwytuje dane wejściowe.

1. Naciśnij klawisz **F11**. Program Visual Studio podświetla instrukcję, która zawiera `date` przypisanie zmiennej ( `currentDate` w Visual Basic). Okno zmienne **lokalne** pokazuje wartość zwracaną przez wywołanie <xref:System.Console.ReadLine%2A?displayProperty=nameWithType> metody. W oknie konsoli jest również wyświetlany ciąg wprowadzony w wierszu polecenia.

1. Naciśnij klawisz **F11**. Okno **lokalne** pokazuje wartość `date` zmiennej po przypisaniu z <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości. Okno konsoli nie jest zmieniane.

1. Naciśnij klawisz **F11**. Program Visual Studio wywołuje <xref:System.Console.WriteLine(System.String,System.Object,System.Object)?displayProperty=nameWithType> metodę. W oknie konsoli zostanie wyświetlony sformatowany ciąg.

1. Wybierz pozycję **Debuguj**  >  **Wyjdź**. Innym sposobem zatrzymania wykonywania krok po kroku jest naciśnięcie klawisza **SHIFT** + **F11**.

   W oknie konsoli zostanie wyświetlony komunikat i czeka na naciśnięcie klawisza.

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli i zatrzymać debugowanie.

## <a name="build-a-release-version"></a>Tworzenie wersji wydania

Po przetestowaniu wersji debugowania aplikacji należy również skompilować i przetestować wersję publikacji. Wersja wydania obejmuje optymalizacje kompilatora, które mogą czasami mieć negatywny wpływ na działanie aplikacji. Na przykład optymalizacje kompilatora, które mają na celu poprawę wydajności, mogą tworzyć sytuacje wyścigu w aplikacjach wielowątkowych.

Aby skompilować i przetestować wydaną wersję aplikacji konsolowej, Zmień konfigurację kompilacji na pasku narzędzi z **Debuguj** do **Release**.

![domyślny pasek narzędzi programu Visual Studio z wyróżnioną pozycją Debug](./media/debugging-with-visual-studio/visual-studio-toolbar-release.png)

Po naciśnięciu klawisza **F5** lub wybraniu opcji **Kompiluj rozwiązanie** z menu **kompilacja** program Visual Studio kompiluje wersję aplikacji. Można go przetestować, tak jak w przypadku wersji do debugowania.

## <a name="next-steps"></a>Następne kroki

W tym samouczku użyto narzędzi debugowania programu Visual Studio. W następnym samouczku zostanie opublikowana wersja aplikacji, którą można wdrożyć.

> [!div class="nextstepaction"]
> [Publikowanie aplikacji konsolowej .NET Core za pomocą programu Visual Studio](publishing-with-visual-studio.md)
