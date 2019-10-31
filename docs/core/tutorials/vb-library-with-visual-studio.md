---
title: Tworzenie biblioteki klas .NET Standard Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć .NET Standard bibliotekę klas zapisaną w Visual Basic przy użyciu programu Visual Studio 2017
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1daab377abe3b6b89f73ed48eafadeae4d7eee77
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100867"
---
# <a name="build-a-net-standard-library-with-visual-basic-and-the-net-core-sdk-in-visual-studio-2017"></a>Tworzenie biblioteki .NET Standard z Visual Basic i zestaw .NET Core SDK w programie Visual Studio 2017

*Biblioteka klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, która jest przeznaczona dla .NET Standard 2,0 umożliwia wywoływanie biblioteki przez dowolną implementację platformy .NET, która obsługuje tę wersję .NET Standard. Po zakończeniu biblioteki klas możesz zdecydować, czy chcesz ją rozpowszechnić jako składnik innej firmy, czy chcesz ją dołączyć jako składnik pakietu z co najmniej jedną aplikacjami.

> [!NOTE]
> Listę wersji .NET Standard i obsługiwanych przez nich platform można znaleźć w temacie [.NET Standard](../../standard/net-standard.md).

W tym temacie utworzysz prostą bibliotekę narzędzi, która zawiera pojedynczą metodę obsługi ciągów. Należy zaimplementować ją jako [metodę rozszerzenia](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) , aby można było wywołać ją tak, jakby była elementem członkowskim klasy <xref:System.String>.

## <a name="creating-a-class-library-solution"></a>Tworzenie rozwiązania biblioteki klas

Zacznij od utworzenia rozwiązania dla projektu biblioteki klas i powiązanych z nim projektów. Rozwiązanie programu Visual Studio służy tylko jako kontener dla jednego lub wielu projektów. Aby utworzyć rozwiązanie:

1. Na pasku menu programu Visual Studio wybierz kolejno pozycje **plik** > **Nowy** > **projekt**.

1. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Inne typy projektów** , a następnie wybierz pozycję **rozwiązania programu Visual Studio**. Nazwij rozwiązanie "ClassLibraryProjects" i wybierz przycisk **OK** .

   ![Okno dialogowe tworzenia nowego projektu testowego programu Visual Studio](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Tworzenie projektu biblioteki klas

Utwórz projekt biblioteki klas:

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik rozwiązania **ClassLibraryProjects** i z menu kontekstowego wybierz pozycję **Dodaj** > **Nowy projekt**.

1. W oknie dialogowym **Dodaj nowy projekt** rozwiń węzeł **Visual Basic** , a następnie wybierz węzeł **.NET Standard** , po którym następuje szablon projektu **Biblioteka klas (.NET standard)** . W polu tekstowym **Nazwa** wprowadź wartość "StringLibrary" jako nazwę projektu. Wybierz **przycisk OK** , aby utworzyć projekt biblioteki klas.

   ![Okno dialogowe Dodaj nowy projekt biblioteki programu Visual Studio](./media/vb-library-with-visual-studio/create-new-library-project.png)

   Zostanie otwarte okno kod w środowisku deweloperskim programu Visual Studio. 
 
   ![Okno aplikacji programu Visual Studio pokazujące domyślny kod szablonu biblioteki klas](./media/vb-library-with-visual-studio/visual-studio-library.png)

1. Upewnij się, że biblioteka jest ukierunkowana na poprawną wersję .NET Standard. Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksplorator rozwiązań** Windows, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **Struktura docelowa** pokazuje, że są one ukierunkowane na .NET Standard 2,0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. W oknie dialogowym **Właściwości** Wyczyść tekst w polu tekstowym **główna przestrzeń nazw** . Dla każdego projektu Visual Basic automatycznie tworzy przestrzeń nazw, która odpowiada nazwie projektu, a wszystkie przestrzenie nazw zdefiniowane w plikach kodu źródłowego są nadrzędne tej przestrzeni nazw. Chcemy zdefiniować przestrzeń nazw najwyższego poziomu za pomocą słowa kluczowego [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) .
  
1. Zastąp kod w oknie kodu następującym kodem i Zapisz plik:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, która zwraca <xref:System.Boolean> wartość wskazującą, czy bieżące wystąpienie ciągu zaczyna się od wielkiej litery. Standard Unicode rozróżnia wielkie litery od małych liter. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca `true`, jeśli znak jest pisany wielką literą.

1. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**. Projekt powinien zostać skompilowany bez błędu.

   ![Okienko danych wyjściowych pokazujące, że kompilacja powiodła się](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Następny krok

Biblioteka została pomyślnie skompilowana. Ponieważ nie została wywołana żadna z jej metod, nie wiesz, czy działa ona zgodnie z oczekiwaniami. Następnym krokiem w opracowaniu biblioteki jest przetestowanie jej przy użyciu [projektu testów jednostkowych](testing-library-with-visual-studio.md).
