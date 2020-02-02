---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio
description: Tworzenie aplikacji .NET Core, która wywołuje elementy członkowskie innej biblioteki klas z programem Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920454"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Korzystanie z biblioteki .NET Standard w programie Visual Studio

Po utworzeniu biblioteki klas .NET Standard, przetestowaniu i skompilowaniu wersji biblioteki, następnym krokiem jest udostępnienie jej obiektom wywołującym. Możesz to zrobić na dwa sposoby:

- Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład w przypadku składnika w pojedynczej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.
- Jeśli biblioteka będzie publicznie dostępna, możesz ją rozpowszechnić jako pakiet NuGet.

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
>
> - Dodaj do rozwiązania aplikację konsolową, która odwołuje się do projektu biblioteki .NET Standard.
> - Utwórz pakiet NuGet zawierający projekt biblioteki .NET Standard.

## <a name="add-a-console-app-to-your-solution"></a>Dodawanie aplikacji konsolowej do rozwiązania

Podobnie jak w przypadku testów jednostkowych w tym samym rozwiązaniu co Biblioteka klas w [testowaniu biblioteki .NET standard w programie Visual Studio](testing-library-with-visual-studio.md), możesz dołączyć aplikację jako część tego rozwiązania. Można na przykład użyć biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy jego pierwszy znak jest pisany wielkimi literami:

1. Otwórz rozwiązanie `ClassLibraryProjects` utworzone w [bibliotece kompilacja .NET standard w artykule Visual Studio](library-with-visual-studio.md) .

1. Dodaj nową aplikację konsolową .NET Core do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź w polu wyszukiwania **konsolę** . Wybierz **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź wartość **Prezentacja** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projekt nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **zależności** projektu `ShowCase`, a następnie wybierz polecenie **Dodaj odwołanie**.

   ![Dodaj menu kontekstowe odwołania w programie Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .

   ![Okno dialogowe programu Reference Manager z wybraną pozycją StringLibrary](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kodu dla pliku *program.cs* lub *program. vb* Zastąp cały kod następującym kodem:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod używa zmiennej `row`, aby zachować liczbę wierszy danych zapisaną w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz ENTER bez wprowadzania ciągu, aplikacja zostanie zakończona, a okno konsoli zostanie zamknięte.

1. W razie potrzeby zmień pasek narzędzi, aby skompilować wydanie **debugowania** projektu `ShowCase`. Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem Debuguj](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Można debugować i publikować aplikację, która korzysta z tej biblioteki, wykonując czynności opisane w sekcji [debugowanie C# aplikacji .NET Core Hello world lub jej Visual Basic przy użyciu programu Visual Studio](debugging-with-visual-studio.md) i [opublikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Tworzenie pakietu NuGet

Bibliotekę klas można udostępnić publicznie, publikując ją jako pakiet NuGet. Program Visual Studio nie obsługuje tworzenia pakietów NuGet. Aby go utworzyć, należy użyć poleceń interfejs wiersza polecenia platformy .NET Core:

1. Otwórz okno konsoli.

   Na przykład wpisz **wiersz polecenia** w polu wyszukiwania na pasku zadań systemu Windows. Wybierz pozycję **wiersz polecenia** aplikacja klasyczna lub naciśnij klawisz **Enter** , jeśli jest już zaznaczona w wynikach wyszukiwania.

1. Przejdź do katalogu projektu biblioteki. Katalog zawiera kod źródłowy i plik projektu, *StringLibrary. csproj* lub *StringLibrary. vbproj*.

1. Uruchom polecenie [dotnet Pack](../tools/dotnet-pack.md) , aby wygenerować pakiet z rozszerzeniem *. nupkg* :

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Jeśli katalog zawierający program *dotnet. exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` w oknie konsoli.

Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet przy użyciu interfejs wiersza polecenia platformy .NET Core](../deploying/creating-nuget-packages.md).
