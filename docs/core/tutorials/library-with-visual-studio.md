---
title: Tworzenie C# biblioteki klas .NET Standard za pomocą programu Visual Studio 2017
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard, napisany w języku C# za pomocą programu Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0c98f8c8fc4847570964d8d4ea8deb221164441d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168939"
---
# <a name="build-a-net-standard-class-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a>Tworzenie biblioteki klas .NET Standard z C# i .NET Core SDK w programie Visual Studio 2017

A *biblioteki klas* Określa typy i metody, które są wywoływane przez aplikację. Biblioteka klas, który jest przeznaczony dla .NET Standard 2.0 umożliwia biblioteki można wywoływać za pomocą dowolnego implementacji .NET, która obsługuje daną wersję .NET Standard. Po zakończeniu biblioteki klas, można zdecydować, czy chcesz rozprowadzić go jako składników innych firm lub tego, czy chcesz dołączyć go jako składnik powiązane z jedną lub więcej aplikacji.

> [!NOTE]
> Aby uzyskać listę wersji programu .NET Standard i platform, które obsługują, zobacz [.NET Standard](../../standard/net-standard.md).

W tym temacie utworzysz bibliotekę prostego narzędzia, która zawiera jedną metodę obsługi ciągów. Będzie implementowana jako [— metoda rozszerzenia](../../csharp/programming-guide/classes-and-structs/extension-methods.md) tak, aby można go wywołać, tak jakby był on członkiem <xref:System.String> klasy.

## <a name="creating-a-class-library-solution"></a>Tworzenie rozwiązania biblioteki klas

Rozpocznij od utworzenia rozwiązania dla Twojego projektu biblioteki klas i jej powiązane projekty. Rozwiązania programu Visual Studio są po prostu służy jako kontener dla jednego lub więcej projektów. Aby utworzyć rozwiązanie:

1. Na pasku menu programu Visual Studio, wybierz **pliku** > **New** > **projektu**.

1. W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** , a następnie wybierz węzeł **Visual Studio Solutions**. Nazwij rozwiązanie "ClassLibraryProjects", a następnie wybierz pozycję **OK** przycisku.

   ![Okno dialogowe nowego projektu za pomocą nowe puste rozwiązanie wyróżniony](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a>Tworzenie projektu biblioteki klas

Utwórz projekt biblioteki klas:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania pliku, a następnie z menu kontekstowego wybierz pozycję **Dodaj** > **New Projekt**.

1. W **Dodaj nowy projekt** okna dialogowego, rozwiń węzeł **Visual C#** węzła, następnie wybierz pozycję **.NET Standard** węzła następuje **biblioteki klas (.NET Standard)** szablonu projektu. W **nazwa** tekstu wprowadź "StringLibrary" jako nazwę projektu. Wybierz **OK** Aby utworzyć projekt biblioteki klas.

   ![Dodawanie okna dialogowego Nowy projekt biblioteki](./media/library-with-visual-studio/add-new-library-project.png)

   W oknie kodu, a następnie zostanie otwarta w środowisku programowania Visual Studio.

   ![Visual Studio okna aplikacji, przedstawiający kod szablonu domyślnego klasy biblioteki](./media/library-with-visual-studio/string-library-project.png)

1. Sprawdź, czy nasza biblioteka jest przeznaczony dla prawidłowej wersji programu .NET Standard. Kliknij prawym przyciskiem myszy na projekt biblioteki w **Eksploratora rozwiązań** systemu windows, następnie wybierz pozycję **właściwości**. **Platformę docelową** pole tekstowe pokazuje, że firma Microsoft objęci .NET Standard 2.0.

   ![Właściwości projektu biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. Zastąp kod w oknie Kod następującym kodem, a następnie zapisz plik:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, co powoduje zwrócenie <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się od wielkiej litery. Unicode standard rozróżnia wielkie litery z małych liter. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda zwraca `true` Jeśli znak jest wielką literą.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Projekt powinien być skompilowana bez błędów.

   ![Okienko danych wyjściowych, pokazujący, że kompilacja zakończyła się pomyślnie](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a>Następny krok

Został pomyślnie skompilowany biblioteki. Ponieważ jeszcze nie wywołać dowolną z jego metod, nie wiadomo, czy działa zgodnie z oczekiwaniami. Następnym krokiem w tworzeniu biblioteki jest przetestowanie go za pomocą [projektu testu jednostkowego](testing-library-with-visual-studio.md).