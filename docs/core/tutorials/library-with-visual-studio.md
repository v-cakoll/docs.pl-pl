---
title: Tworzenie biblioteki klas .NET Standard w programie Visual Studio
description: Dowiedz się, jak utworzyć .NET Standardą bibliotekę klas C# zapisaną w programie lub Visual Basic przy użyciu programu Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343107"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Tworzenie biblioteki .NET Standard w programie Visual Studio

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard. Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.

> [!NOTE]
> Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).

W tym temacie utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów. Należy zaimplementować ją jako [metodę rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim klasy <xref:System.String>.

## <a name="create-a-visual-studio-solution"></a>Tworzenie rozwiązania programu Visual Studio

Zacznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas w. Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub wielu projektów. Jeśli będziesz kontynuować pracę z serią samouczków, dodasz kolejne powiązane projekty do tego samego rozwiązania.

Aby utworzyć puste rozwiązanie:

1. Otwórz program Visual Studio.

2. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania. Wybierz szablon **pustego rozwiązania** , a następnie wybierz przycisk **dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na stronie **Konfiguruj nowy projekt** wprowadź **ClassLibraryProjects** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Możesz również pominąć ten krok i pozwolić programowi Visual Studio utworzyć rozwiązanie dla Ciebie podczas tworzenia projektu w następnym kroku. Zapoznaj się z opcjami rozwiązania na stronie **Konfiguruj nowy projekt** .

## <a name="create-a-class-library-project"></a>Tworzenie projektu biblioteki klas

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. Dodaj nowy C# projekt biblioteki klas .NET Standard o nazwie "StringLibrary" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania. Wybierz **C#** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

1. Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard. Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. Zastąp kod w oknie kodu następującym kodem i Zapisz plik:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`. Ta metoda zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery. Standard Unicode rozróżnia wielkie litery od małych liter. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.

1. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. Dodaj nowy projekt biblioteki klas Visual Basic .NET Standard o nazwie "StringLibrary" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **Nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania. Wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Biblioteka klas (.NET standard)** , a następnie wybierz przycisk **dalej**.

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **StringLibrary** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

1. Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard. Kliknij prawym przyciskiem myszy projekt Biblioteka w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **platformy docelowej** pokazuje, że projekt jest docelowy .NET Standard 2,0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

1. W oknie dialogowym **Właściwości** Wyczyść tekst w polu tekstowym **główna przestrzeń nazw** . Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odnosi się do nazwy projektu. W tym samouczku zdefiniujesz przestrzeń nazw najwyższego poziomu za pomocą słowa kluczowego [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) w pliku kodu.

1. Zastąp kod w oknie kodu następującym kodem i Zapisz plik:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`. Ta metoda zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery. Standard Unicode rozróżnia wielkie litery od małych liter. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.

1. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**.

---

   Projekt powinien zostać skompilowany bez błędu.

## <a name="next-steps"></a>Następne kroki

Biblioteka została pomyślnie skompilowana. Ponieważ nie została wywołana żadna z jej metod, nie wiesz, czy działa ona zgodnie z oczekiwaniami. Następnym krokiem w opracowaniu biblioteki jest przetestowanie go.

> [!div class="nextstepaction"]
> [Tworzenie projektu testu jednostkowego](testing-library-with-visual-studio.md)
