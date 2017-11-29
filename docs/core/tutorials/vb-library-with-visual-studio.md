---
title: "Kompilowanie biblioteki klas z języka Visual Basic i .NET Core w Visual Studio 2017 r."
description: "Informacje o sposobie tworzenia biblioteki klas napisane w języku Visual Basic przy użyciu programu Visual Studio 2017 r."
keywords: Oprogramowanie .NET core, .NET Standard klasy biblioteki 2017 programu Visual Studio, Visual Basic
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs: vb
ms.openlocfilehash: 6572f35b1e2b652c9f2ff5448165ece104f0bdf6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-class-library-with-visual-basic-and-net-core-in-visual-studio-2017"></a>Kompilowanie biblioteki klas z języka Visual Basic i .NET Core w Visual Studio 2017 r.

A *biblioteki klas* definiuje typy i metody, które są wywoływane przez aplikację. Biblioteka klas, przeznaczonego dla programu .NET 2.0 standardowe umożliwia biblioteki ma być wywoływana przez wszystkie implementacja .NET obsługuje tej wersji programu .NET Standard. Po zakończeniu biblioteki klas, można wybrać ją rozpowszechnić jako części innych firm lub czy chcesz dołączyć go jako składnik powiązane z jedną lub więcej aplikacji.

> [!NOTE]
> Listę wersji platformy .NET Standard i platformy obsługują zawiera [.NET Standard](../../standard/net-standard.md).

W tym temacie utworzysz biblioteki prostego narzędzia, która zawiera jedną metodę obsługi ciągów. Będzie zaimplementowaniem go jako [— metoda rozszerzenia](../../visual-basic/programming-guide/language-features/procedures/extension-methods.md) tak, aby można go wywołać, tak jakby był on członkiem <xref:System.String> klasy.

## <a name="creating-a-class-library-solution"></a>Tworzenie rozwiązania biblioteki klas

Rozpocznij od utworzenia rozwiązania dla projektu biblioteki klas i jej powiązane projekty. Rozwiązanie Visual Studio po prostu służy jako kontener dla jednego lub więcej projektów. Aby utworzyć rozwiązania:

1. Na pasku menu programu Visual Studio wybierz **pliku** > **nowy** > **projektu**.

1. W **nowy projekt** okna dialogowego, rozwiń węzeł **inne typy projektów** , a następnie wybierz węzeł **rozwiązań programu Visual Studio**. Nazwa rozwiązania "ClassLibraryProjects" i wybierz **OK** przycisku.

   ![Okno dialogowe nowego projektu](./media/library-with-visual-studio/newproject.png)

## <a name="creating-the-class-library-project"></a>Tworzenie projektu biblioteki klas

Tworzenie projektu biblioteki klas:

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ClassLibraryProjects** rozwiązania plików i z menu kontekstowego wybierz **Dodaj** > **nowy Projekt**.

1. W **Dodawanie nowego projektu** okna dialogowego, rozwiń węzeł **Visual Basic** węzła, następnie wybierz **.NET Standard** węzła następuje **biblioteki klas (.NET Standard)**  szablonu projektu. W **nazwa** tekst Wprowadź "StringLibrary" jako nazwę projektu. Wybierz **OK** do tworzenia projektu biblioteki klas.

   ![Dodaj okno dialogowe Nowy projekt](./media/vb-library-with-visual-studio/libproject.png)

   W środowisku programowania Visual Studio następnie zostanie otwarte okno kodu. 
 
   ![Visual Studio aplikacji okno kod szablonu domyślnego klasy biblioteki](./media/vb-library-with-visual-studio/stringlibrary.png)

1. Sprawdź, czy biblioteka jest przeznaczony dla poprawna wersja programu .NET Standard. Kliknij prawym przyciskiem myszy na projekt biblioteki w **Eksploratora rozwiązań** systemu windows, następnie wybierz **właściwości**. **Platformy docelowej** pole tekstowe pokazuje, że firma Microsoft docelowych .NET 2.0 standardowa.

   ![Właściwości projektu biblioteki klas](./media/library-with-visual-studio/properties.png)

1. Również w **właściwości** okna dialogowego, wyczyść tekst w **głównej przestrzeni nazw** pola tekstowego. Dla każdego projektu Visual Basic automatycznie tworzy przestrzeni nazw, który odpowiada nazwie projektu, a wszystkie przestrzenie nazw zdefiniowane w plików kodu źródłowego są nadrzędne tego obszaru nazw. Chcemy zdefiniować przestrzeni nazw najwyższego poziomu za pomocą [ `namespace` ](../../visual-basic/language-reference/statements/namespace-statement.md) — słowo kluczowe.
  
1. Zastąp kod w oknie Kod następujący kod i Zapisz plik:

  [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę o nazwie `StartsWithUpper`, która zwraca <xref:System.Boolean> wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielką literę. Unicode standard rozróżnia wielkich liter z małych liter. <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> Metoda zwraca `true` Jeśli znak jest wielką.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Projekt powinien kompilacji bez błędów.

   ![W okienku z wyjściem pokazujący, że kompilacja zakończyła się pomyślnie](./media/library-with-visual-studio/buildsucceeds.png)



## <a name="next-step"></a>Następny krok

Został pomyślnie skompilowany biblioteki. Ponieważ nie zostało to jeszcze wywołana dowolnej metody, nie wiadomo, czy działa on zgodnie z oczekiwaniami. Następny krok w rozwoju biblioteki służy do testowania go przy użyciu [projektu testu jednostki](testing-library-with-visual-studio.md).
