---
title: Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017
description: Tworzenie aplikacji .NET Core, która wywołuje elementy członkowskie innej biblioteki klas z programem Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ff60bb5de403970f432e938cba81ca4e99476e8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925986"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a>Korzystanie z biblioteki .NET Standard w programie Visual Studio 2017

Po utworzeniu biblioteki klas .NET Standard, wykonując kroki opisane w sekcji [Kompilowanie C# biblioteki klas przy użyciu platformy .NET Core w programie Visual Studio 2017](./library-with-visual-studio.md) lub [Kompilowanie biblioteki klas Visual Basic przy użyciu platformy .net core w programie Visual Studio 2017](vb-library-with-visual-studio.md), przetestowano ją w [ Testowanie biblioteki klas przy użyciu platformy .NET Core w programie Visual Studio 2017](testing-library-with-visual-studio.md)i skompilowanej wersji biblioteki, następnym krokiem jest udostępnienie jej dla obiektów wywołujących. Można to zrobić na dwa sposoby:

* Jeśli biblioteka będzie używana przez pojedyncze rozwiązanie (na przykład w przypadku składnika w pojedynczej dużej aplikacji), można dołączyć go jako projekt w rozwiązaniu.

* Jeśli biblioteka będzie ogólnie dostępna, możesz ją rozpowszechnić jako pakiet NuGet.

## <a name="including-a-library-as-a-project-in-a-solution"></a>Dołączanie biblioteki jako projektu w rozwiązaniu

Podobnie jak w przypadku testów jednostkowych w tym samym rozwiązaniu co Biblioteka klas, możesz dołączyć aplikację jako część tego rozwiązania. Można na przykład użyć biblioteki klas w aplikacji konsolowej, która wyświetla użytkownikowi komunikat, aby wprowadzić ciąg i określić, czy jego pierwszy znak jest pisany wielkimi literami:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Otwórz rozwiązanie utworzone w sekcji [Kompilowanie biblioteki C# klas przy użyciu programu .NET Core w programie Visual Studio 2017.](./library-with-visual-studio.md) `ClassLibraryProjects` W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt** z menu kontekstowego.

1. W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **wizualizacji C#**  i wybierz węzeł **.NET Core** , a następnie szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "pokaz" i wybierz przycisk **OK** .

   ![Okno dialogowe Dodawanie nowego projektu w programie Visual Studio —C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym.

   ![Menu kontekstowe projektu programu Visual Studio do ustawiania projektu startowego —C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projekt nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksplorator rozwiązań**kliknij prawym przyciskiem `ShowCase` myszy węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie**.

   ![Menu kontekstowe dodawania odwołania w projekcie programu Visual Studio —C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .

   ![Okno dialogowe zarządzania odwołaniami w programie Visual Studio —C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kod dla pliku *program.cs* Zastąp cały kod następującym kodem:

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz ENTER bez wpisywania ciągu, aplikacja zostanie przerwana, a okno konsoli zostanie zamknięte.

1. W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji `ShowCase` **debugowania** projektu. Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .

   ![Pasek narzędzi projektu programu Visual Studio z widocznym przyciskiem DebugujC#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Otwórz rozwiązanie utworzone w sekcji [Tworzenie biblioteki klas z Visual Basic i .NET Core w programie Visual Studio 2017.](vb-library-with-visual-studio.md) `ClassLibraryProjects` W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy rozwiązanie **ClassLibraryProjects** i wybierz polecenie **Dodaj** > **Nowy projekt** z menu kontekstowego.

1. W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **Visual Basic** i wybierz węzeł **.NET Core** , a następnie szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "pokaz" i wybierz przycisk **OK** .

   ![Okno dialogowe Dodawanie nowego projektu w programie Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **pokazu** i wybierz polecenie **Ustaw jako projekt startowy** w menu kontekstowym. 

   ![Menu kontekstowe projektu programu Visual Studio, aby ustawić projekt startowy — Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. Początkowo projekt nie ma dostępu do biblioteki klas. Aby zezwolić na wywoływanie metod w bibliotece klas, należy utworzyć odwołanie do biblioteki klas. W **Eksplorator rozwiązań**kliknij prawym przyciskiem `ShowCase` myszy węzeł **zależności** projektu i wybierz polecenie **Dodaj odwołanie**.

   ![Menu kontekstowe dodawania odwołania do projektu programu Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. W oknie dialogowym **Menedżer odwołań** wybierz pozycję **StringLibrary**, projekt biblioteki klas, a następnie wybierz przycisk **OK** .

   ![Okno dialogowe Zarządzanie odwołaniami w programie Visual Studio — Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. W oknie kod dla pliku *program. vb* Zastąp cały kod następującym kodem:

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   Kod używa `row` zmiennej do obsługi liczby wierszy danych zapisywana w oknie konsoli. Za każdym razem, gdy jest większy lub równy 25, kod czyści okno konsoli i wyświetla komunikat dla użytkownika.

   Program poprosi użytkownika o wprowadzenie ciągu. Wskazuje, czy ciąg rozpoczyna się od wielkiej litery. Jeśli użytkownik naciśnie klawisz ENTER bez wpisywania ciągu, aplikacja zostanie przerwana, a okno konsoli zostanie zamknięte.

1. W razie potrzeby zmień pasek narzędzi w celu skompilowania wersji `ShowCase` **debugowania** projektu. Skompiluj i uruchom program, wybierając zieloną strzałkę na przycisku **Pokaz** .

   ![Debuguj na pasku narzędzi-Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

Można debugować i publikować aplikację, która korzysta z tej biblioteki, wykonując czynności opisane w sekcji [debugowanie aplikacji Hello World za pomocą programu Visual studio 2017](debugging-with-visual-studio.md) i [publikowanie aplikacji Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="distributing-the-library-in-a-nuget-package"></a>Dystrybuowanie biblioteki w pakiecie NuGet

Bibliotekę klas można udostępnić publicznie, publikując ją jako pakiet NuGet. Program Visual Studio nie obsługuje tworzenia pakietów NuGet. Aby go utworzyć, użyj [ `dotnet` narzędzia wiersza polecenia](../tools/dotnet.md):

1. Otwórz okno konsoli. Na przykład w polu tekstowym **pytaj mnie coś** na pasku zadań systemu Windows wpisz `Command Prompt` (lub `cmd` for Short), a następnie otwórz okno konsoli, wybierając **polecenie Wiersz polecenia** aplikacji klasycznej lub naciskając klawisz ENTER, jeśli jest zaznaczone w polu wyszukiwania. uzyskane.

1. Przejdź do katalogu projektu biblioteki. O ile nie skonfigurowano ponownie typowej lokalizacji pliku, znajduje się ona w katalogu *Documents\Visual Studio 2017 \ Projects\ClassLibraryProjects\StringLibrary* . Katalog zawiera kod źródłowy i plik projektu, *StringLibrary. csproj*.

1. Wydaj polecenie `dotnet pack --no-build`. Narzędzie generuje pakiet z rozszerzeniem *. nupkg.* `dotnet`

   > [!TIP]
   > Jeśli katalog zawierający program *dotnet. exe* nie znajduje się w ścieżce, można znaleźć jego lokalizację, wprowadzając `where dotnet.exe` ją w oknie konsoli.

Aby uzyskać więcej informacji na temat tworzenia pakietów NuGet, zobacz [jak utworzyć pakiet NuGet za pomocą narzędzi międzyplatformowych](../deploying/creating-nuget-packages.md).
