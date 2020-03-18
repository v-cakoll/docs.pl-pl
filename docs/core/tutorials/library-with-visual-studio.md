---
title: Tworzenie biblioteki klas standardu .NET w programie Visual Studio
description: Dowiedz się, jak utworzyć bibliotekę klas .NET Standard napisaną w języku C# lub Visual Basic przy użyciu programu Visual Studio
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714020"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a>Tworzenie biblioteki standardu .NET w programie Visual Studio

*Biblioteka klas* definiuje typy i metody wywoływane przez aplikację. Biblioteka klas przeznaczona dla programu .NET Standard 2.0 umożliwia wywoływanie biblioteki przez dowolną implementację .NET obsługującej tę wersję standardu .NET. Po zakończeniu biblioteki klas, można zdecydować, czy chcesz rozpowszechniać go jako składnik innej firmy lub czy chcesz dołączyć go jako składnik w pakiecie z jedną lub więcej aplikacji.

> [!NOTE]
> Aby uzyskać listę wersji standardu .NET i obsługiwanych platform, zobacz [.NET Standard](../../standard/net-standard.md).

W tym temacie utworzysz prostą bibliotekę narzędziową zawierającą metodę obsługi pojedynczych ciągów. Zaimplementujesz go jako [metodę rozszerzenia,](../../csharp/programming-guide/classes-and-structs/extension-methods.md) dzięki czemu można wywołać go <xref:System.String> tak, jakby był członkiem klasy.

## <a name="create-a-visual-studio-solution"></a>Tworzenie rozwiązania programu Visual Studio

Rozpocznij od utworzenia pustego rozwiązania, aby umieścić projekt biblioteki klas. Rozwiązanie programu Visual Studio służy jako kontener dla jednego lub więcej projektów. Dodasz dodatkowe, powiązane projekty do tego samego rozwiązania, jeśli będziesz kontynuować serię samouczków.

Aby utworzyć puste rozwiązanie:

1. Otwórz program Visual Studio.

2. W oknie startowym wybierz pozycję **Utwórz nowy projekt**.

3. Na stronie **Tworzenie nowego projektu** wprowadź **rozwiązanie** w polu wyszukiwania. Wybierz szablon **Puste rozwiązanie,** a następnie wybierz pozycję **Dalej**.

   ![Pusty szablon rozwiązania w programie Visual Studio](media/library-with-visual-studio/blank-solution.png)

4. Na stronie **Konfigurowanie nowego projektu** wprowadź **pozycję ClassLibraryProjects** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

> [!TIP]
> Można również pominąć ten krok i pozwolić visual studio utworzyć rozwiązanie dla Ciebie podczas tworzenia projektu w następnym kroku. Poszukaj opcji rozwiązania na stronie **Konfigurowanie nowego projektu.**

## <a name="create-a-class-library-project"></a>Tworzenie projektu biblioteki klas

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Dodaj nowy projekt biblioteki klas Standard c# .NET o nazwie "StringLibrary" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania. Wybierz **c#** z listy Język, a następnie wybierz **wszystkie platformy** z listy Platforma. Wybierz szablon **Biblioteka klas (.NET Standard),** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **bibliotekę ciągów** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

1. Upewnij się, że biblioteka jest przeznaczona dla poprawnej wersji programu .NET Standard. Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksploratorze rozwiązań**, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **Platforma docelowa** pokazuje, że projekt jest przeznaczony dla programu .NET Standard 2.0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/library-project-properties.png)

1. Zastąp kod w oknie kodu następującym kodem i zapisz plik:

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę `StartsWithUpper`o nazwie . Ta metoda <xref:System.Boolean> zwraca wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielkimi literami. Standard Unicode odróżnia wielkie litery od małych liter. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca, `true` jeśli znak jest wielkimi literami.

1. Na pasku menu wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji**.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Dodaj nowy projekt biblioteki klas programu Visual Basic .NET Standard o nazwie "StringLibrary" do rozwiązania.

   1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksploratorze rozwiązań** i wybierz **polecenie Dodaj** > **nowy projekt**.

   1. Na stronie **Dodawanie nowego projektu** wprowadź **bibliotekę** w polu wyszukiwania. Wybierz **pozycję Visual Basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma. Wybierz szablon **Biblioteka klas (.NET Standard),** a następnie wybierz pozycję **Dalej**.

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **bibliotekę ciągów** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

1. Upewnij się, że biblioteka jest przeznaczona dla poprawnej wersji programu .NET Standard. Kliknij prawym przyciskiem myszy projekt biblioteki w **Eksploratorze rozwiązań**, a następnie wybierz polecenie **Właściwości**. Pole tekstowe **Platforma docelowa** pokazuje, że projekt jest przeznaczony dla programu .NET Standard 2.0.

   ![Właściwości projektu dla biblioteki klas](./media/library-with-visual-studio/vb/library-project-properties.png)

1. W oknie dialogowym **Właściwości** wyczyść tekst w polu tekstowym **Główny obszar nazw.** Dla każdego projektu program Visual Basic automatycznie tworzy obszar nazw odpowiadający nazwie projektu. W tym samouczku można zdefiniować obszar nazw [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) najwyższego poziomu przy użyciu słowa kluczowego w pliku kodu.

1. Zastąp kod w oknie kodu następującym kodem i zapisz plik:

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   Biblioteka klas `UtilityLibraries.StringLibrary`, zawiera metodę `StartsWithUpper`o nazwie . Ta metoda <xref:System.Boolean> zwraca wartość, która wskazuje, czy bieżące wystąpienie ciągu rozpoczyna się wielkimi literami. Standard Unicode odróżnia wielkie litery od małych liter. Metoda <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> zwraca, `true` jeśli znak jest wielkimi literami.

1. Na pasku menu wybierz pozycję **Zbuduj** > **rozwiązanie kompilacji**.

---

   Projekt należy skompilować bez błędów.

## <a name="next-steps"></a>Następne kroki

Biblioteka została pomyślnie utworzona. Ponieważ nie zostały wywołane żadnej z jego metod, nie wiesz, czy to działa zgodnie z oczekiwaniami. Następnym krokiem w tworzeniu biblioteki jest przetestowanie jej.

> [!div class="nextstepaction"]
> [Tworzenie projektu testu jednostkowego](testing-library-with-visual-studio.md)
