---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio
description: Skompiluj aplikację .NET Core, która wywołuje członków innej biblioteki klas za pomocą programu Visual Studio 2019.
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920454"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a>Korzystanie z biblioteki .NET Standard w programie Visual Studio

Po utworzeniu biblioteki klas .NET Standard przetestowano ją i skonstruowano wersję biblioteki, następnym krokiem jest udostępnienie jej obiektom wywołującym. Możesz to zrobić na dwa sposoby:

- Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład, jeśli jest składnikiem w jednej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.
- Jeśli biblioteka będzie publicznie dostępna, można rozpowszechniać go jako pakiet NuGet.

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
>
> - Dodaj aplikację konsoli do rozwiązania, które odwołuje się do projektu biblioteki standardu .NET.
> - Utwórz pakiet NuGet zawierający projekt biblioteki standardów .NET.

## <a name="add-a-console-app-to-your-solution"></a>Dodawanie aplikacji konsoli do rozwiązania

Podobnie jak w tym samym rozwiązaniu, co biblioteka klas, w [testowej bibliotece standardu .NET w programie Visual Studio,](testing-library-with-visual-studio.md)aplikacja może być dołączona jako część tego rozwiązania. Na przykład można użyć biblioteki klas w aplikacji konsoli, która monituje użytkownika, aby wprowadzić ciąg i raporty, czy jego pierwszy znak jest wielkimi literami:

1. Otwórz `ClassLibraryProjects` rozwiązanie utworzone w artykule [Tworzenie biblioteki standardu .NET w](library-with-visual-studio.md) programie Visual Studio.

1. Dodaj do rozwiązania nową aplikację konsoli .NET Core o nazwie "ShowCase".

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **konsolę** w polu wyszukiwania. Wybierz **c#** lub **Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma. Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **pokaż sprawę** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy projekt **ShowCase** i w menu kontekstowym wybierz polecenie **Ustaw jako projekt startup.**

   ![Menu kontekstowe projektu programu Visual Studio do ustawiania projektu startowego](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projekt nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł `ShowCase` **Zależności** projektu i wybierz polecenie **Dodaj odwołanie**.

   ![Dodawanie menu kontekstowego odwołania w programie Visual Studio](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas i wybierz przycisk **OK.**

   ![Okno dialogowe Menedżera odwołań z zaznaczoną biblioteką ciągów](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kodu pliku *Program.cs* lub *Program.vb* zastąp cały kod następującym kodem:

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisanych w oknie konsoli. Zawsze, gdy jest większa lub równa 25, kod czyści okno konsoli i wyświetla komunikat do użytkownika.

   Program monituje użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg zaczyna się od znaku wielkich liter. Jeśli użytkownik naciśnie klawisz Enter bez wprowadzania ciągu, aplikacja się kończy, a okno konsoli zostanie zamknięte.

1. W razie potrzeby zmień pasek narzędzi, aby skompilować wersję **debugowania** `ShowCase` projektu. Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **ShowCase.**

   ![Pasek narzędzi projektu programu Visual Studio z przyciskiem Debugowania](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

Można debugować i publikować aplikację korzystającą z tej biblioteki, wykonując kroki opisane w [debugowania aplikacji C# lub Visual Basic .NET Core Hello World przy użyciu programu Visual Studio](debugging-with-visual-studio.md) i [publikowania aplikacji .NET Core Hello World za pomocą programu Visual Studio](publishing-with-visual-studio.md).

## <a name="create-a-nuget-package"></a>Tworzenie pakietu NuGet

Można udostępnić biblioteki klas powszechnie dostępne przez opublikowanie go jako pakiet NuGet. Program Visual Studio nie obsługuje tworzenia pakietów NuGet. Aby go utworzyć, należy użyć poleceń cli .NET Core:

1. Otwórz okno konsoli.

   Na przykład wprowadź **wiersz polecenia** w polu wyszukiwania na pasku zadań systemu Windows. Wybierz aplikację **klasyczną Wiersz polecenia** lub naciśnij klawisz **Enter,** jeśli jest już zaznaczona w wynikach wyszukiwania.

1. Przejdź do katalogu projektu biblioteki. Katalog zawiera kod źródłowy i plik projektu, *StringLibrary.csproj* lub *StringLibrary.vbproj*.

1. Uruchom polecenie [dotnet pack,](../tools/dotnet-pack.md) aby wygenerować pakiet z rozszerzeniem *.nupkg:*

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > Jeśli katalog zawierający *program dotnet.exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` ją w oknie konsoli.

Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [Jak utworzyć pakiet NuGet za pomocą .NET Core CLI](../deploying/creating-nuget-packages.md).
