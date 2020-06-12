---
title: Tworzenie biblioteki klas .NET Standard przy użyciu Visual Studio dla komputerów Mac
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard przy użyciu Visual Studio dla komputerów Mac.
ms.date: 06/08/2020
ms.openlocfilehash: 3a107fff2fd6aef5e06d9af3eac334fbf5688fa5
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713743"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a>Samouczek: Tworzenie biblioteki .NET Standard przy użyciu Visual Studio dla komputerów Mac

W tym samouczku utworzysz prostą bibliotekę klas, która zawiera pojedynczą metodę obsługi ciągów. Implementuje ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim <xref:System.String> klasy.

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas przeznaczona dla .NET Standard 2,1 może być używana przez aplikację, która jest przeznaczona dla dowolnej implementacji platformy .NET, która obsługuje wersję 2,1 .NET Standard. Po zakończeniu biblioteki klas można ją rozpowszechnić jako składnik innej firmy lub jako składnik pakietu z jedną lub wieloma aplikacjami.

> [!NOTE]
> Opinie są wysoce wyceniane. Istnieją dwa sposoby przekazywania opinii zespołowi programistycznemu na Visual Studio dla komputerów Mac:
>
> - W Visual Studio dla komputerów Mac wybierz pozycję **Pomoc**  >  **Zgłoś problem** z menu lub **Zgłoś problem** na ekranie powitalnym, co spowoduje otwarcie okna umożliwiającego zgłoszenie usterki. Swoje opinie możesz śledzić w portalu [Społeczność deweloperów](https://developercommunity.visualstudio.com/spaces/41/index.html).
> - Aby dokonać sugestii, wybierz pozycję **Pomoc**  >  **Podaj sugestię** z menu lub **Podaj sugestię** z ekranu powitalnego, który przeprowadzi Cię do [witryny internetowej społeczność deweloperów Visual Studio dla komputerów Mac](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).

## <a name="prerequisites"></a>Wymagania wstępne

* [Zainstaluj program Visual Studio dla komputerów Mac w wersji 8,6 lub nowszej](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link). Wybierz opcję zainstalowania platformy .NET Core. Instalowanie platformy Xamarin jest opcjonalne w przypadku programowania .NET Core. Więcej informacji zawierają następujące zasoby:

  * [Samouczek: instalowanie Visual Studio dla komputerów Mac](/visualstudio/mac/installation).
  * [Obsługiwane wersje macOS](../install/dependencies.md?pivots=os-macos).
  * [Wersje programu .NET Core obsługiwane przez Visual Studio dla komputerów Mac](/visualstudio/mac/net-core-support).

## <a name="create-a-solution-with-a-class-library-project"></a>Utwórz rozwiązanie z projektem biblioteki klas

Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów. Utwórz rozwiązanie i projekt biblioteki klas w rozwiązaniu. Kolejne powiązane projekty zostaną dodane do tego samego rozwiązania później.

1. Rozpocznij Visual Studio dla komputerów Mac.

1. W oknie uruchamiania wybierz pozycję **Nowy projekt**.

1. W oknie dialogowym **Nowy projekt** w węźle **wiele platform** wybierz pozycję **Biblioteka**, a następnie wybierz szablon **Biblioteka .NET Standard** , a następnie wybierz przycisk **dalej**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Okno dialogowe Nowy projekt":::

1. W oknie dialogowym **Konfigurowanie nowej biblioteki .NET Standard** wybierz pozycję ".NET Standard 2,1", a następnie wybierz przycisk **dalej**.

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="Wybierz .NET Standard 2,1":::

1. Nadaj projektowi nazwę "StringLibrary" i rozwiązanie "ClassLibraryProjects". Pozostaw opcję **Utwórz katalog projektu w wybranym katalogu rozwiązania** . Wybierz przycisk **Utwórz**.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Opcje okna dialogowego Visual Studio dla komputerów Mac nowego projektu":::

1. Z menu głównego wybierz pozycję **Widok**  >  **okienka**  >  **Solution**, a następnie wybierz ikonę dokowania, aby zachować otwartą konsolę.

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Ikona dokowania dla konsoli rozwiązania":::

1. W konsoli **rozwiązania** rozwiń `StringLibrary` węzeł, aby odsłonić plik klasy dostarczony przez szablon, *Class1.cs*. <kbd>naciśnij klawisz Ctrl</kbd>i kliknij plik, wybierz polecenie **Zmień nazwę** z menu kontekstowego, a następnie zmień nazwę pliku na *StringLibrary.cs*. Otwórz plik i Zastąp jego zawartość następującym kodem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. Naciśnij pozycję <kbd>⌘</kbd><kbd>s</kbd> (<kbd>Command</kbd> + <kbd>s</kbd>), aby zapisać plik.

1. Wybierz pozycję **Błędy** na marginesie u dołu okna IDE, aby otworzyć panel **Błędy** . Wybierz przycisk **kompilacja danych wyjściowych** .

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Dolny margines środowiska IDE programu Visual Studio Mac przedstawiającego przycisk błędy":::

1. Z menu wybierz pozycję **kompilacja**  >  **Kompiluj wszystko** .

   Rozwiązanie kompiluje. Panel dane wyjściowe kompilacji pokazuje, że kompilacja zakończyła się pomyślnie.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="Okienko danych wyjściowych kompilacji programu Visual Studio dla komputerów Mac w panelu Błędy z komunikatem Kompilacja zakończona pomyślnie":::

## <a name="add-a-console-app-to-the-solution"></a>Dodawanie aplikacji konsolowej do rozwiązania

Dodaj aplikację konsolową, która używa biblioteki klas. Aplikacja wyświetli monit o wprowadzenie ciągu i zgłoszenie, czy ciąg rozpoczyna się od wielkiej litery.

1. W konsoli **rozwiązania** <kbd>naciśnij klawisz Ctrl</kbd>i kliknij `ClassLibraryProjects` rozwiązanie. Dodaj nowy projekt **aplikacji konsoli** , wybierając szablon z szablonów aplikacji **sieci Web i konsoli**  >  **App** , a następnie wybierz przycisk **dalej**.

1. Wybierz pozycję **.NET Core 3,1** jako **platformę docelową** i wybierz pozycję **dalej**.

1. Nadaj nazwę **pokazowi**projektu. Wybierz pozycję **Utwórz** , aby utworzyć projekt w rozwiązaniu.

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="Dodaj projekt pokazu":::

1. Otwórz plik *program.cs* . Zastąp kod następującym kodem:

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz <kbd>Enter</kbd> bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

## <a name="add-a-project-reference"></a>Dodaj odwołanie do projektu

Początkowo nowy projekt aplikacji konsolowej nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, Utwórz odwołanie do projektu do projektu biblioteki klas.

1. W konsoli **rozwiązania** <kbd>, kliknij</kbd>węzeł **zależności** w nowym projekcie **pokazu** . W menu kontekstowym wybierz polecenie **Dodaj odwołanie**.

1. W oknie dialogowym **odwołania** wybierz pozycję **StringLibrary** , a następnie wybierz pozycję **OK**.

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. <kbd>naciśnij klawisz Ctrl</kbd>i kliknij projekt pokazu i wybierz polecenie **Uruchom projekt** z menu kontekstowego.

1. Wypróbuj program, wprowadzając ciągi i naciskając klawisz <kbd>Enter</kbd>, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść.

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio dla komputerów Mac okno konsoli z uruchomioną aplikacją":::

## <a name="additional-resources"></a>Zasoby dodatkowe

* [Tworzenie bibliotek przy użyciu interfejs wiersza polecenia platformy .NET Core](libraries.md)
* [Wersje .NET Standard i obsługiwane przez nich platformy](../../standard/net-standard.md).
* [Visual Studio 2019 dla komputerów Mac — Informacje o wersji](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono rozwiązanie i projekt biblioteki oraz dodano projekt aplikacji konsoli, który używa biblioteki. W następnym samouczku dodasz projekt testu jednostkowego do rozwiązania.

> [!div class="nextstepaction"]
> [Testowanie biblioteki .NET Standard za pomocą platformy .NET Core przy użyciu Visual Studio dla komputerów Mac](testing-library-with-visual-studio-mac.md)
