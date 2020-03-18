---
title: Tworzenie aplikacji Hello World z usługą .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć pierwszą aplikację konsoli .NET Core z c# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713996"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Samouczek: Tworzenie pierwszej aplikacji konsoli .NET Core w programie Visual Studio 2019

Ten artykuł zawiera wprowadzenie krok po kroku do tworzenia i uruchamiania aplikacji konsoli Hello World .NET Core w programie Visual Studio 2019. Aplikacja Hello World jest tradycyjnie używana do wprowadzania początkujących do nowego języka programowania. Ten program po prostu wyświetla wyrażenie "Hello World!" na ekranie.

## <a name="prerequisites"></a>Wymagania wstępne

- [Visual Studio 2019 w wersji 16.4 lub nowszej wersji](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem **programistycznym .NET Core.** Zestaw SDK .NET Core 3.1 jest instalowany automatycznie po wybraniu tego obciążenia.

Aby uzyskać więcej informacji, zobacz [sekcję Instalowanie w programie Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie sdk .NET Core SDK.](../install/sdk.md?pivots=os-windows)

## <a name="create-the-app"></a>Tworzymy aplikację.

Poniższe instrukcje tworzą prostą aplikację konsoli Hello World:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C #](#tab/csharp)

1. Otwórz Visual Studio 2019.

1. Utwórz nowy projekt aplikacji konsoli C# .NET Core o nazwie "HelloWorld".

   1. W oknie startowym wybierz pozycję **Utwórz nowy projekt**.

      ![Tworzenie nowego przycisku projektu wybranego w oknie startowym programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stronie **Tworzenie nowego projektu** wprowadź **konsolę** w polu wyszukiwania. Następnie wybierz **c#** z listy Język, a następnie wybierz **pozycję Wszystkie platformy** z listy Platforma. Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.

      ![Tworzenie nowego okna projektu z zaznaczonymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia zainstalowanego. W **Install more tools and features** **obszarze Nie znajdując tego, czego szukasz?** Zostanie otwarty Instalator programu Visual Studio. Upewnij się, że masz zainstalowane obciążenie **programistyczne dla wielu platform .NET Core.**

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **helloworld** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

      ![Konfigurowanie nowego okna projektu za pomocą pól nazwa projektu, lokalizacja i nazwa rozwiązania](./media/with-visual-studio/configure-new-project.png)

   Szablon aplikacji konsoli C# dla .NET Core automatycznie `Program`definiuje klasę, `Main`z jedną <xref:System.String> metodą, przyjmuje tablicę jako argument. `Main`jest punktem wejścia aplikacji, metodą, która jest wywoływana automatycznie przez czas wykonywania po uruchomieniu aplikacji. Wszystkie argumenty wiersza polecenia podane po uruchomieniu aplikacji są dostępne w *tablicy args.*

   ![Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Otwórz Visual Studio 2019.

1. Utwórz nowy projekt aplikacji konsoli programu Visual Basic .NET Core o nazwie "HelloWorld".

   1. W oknie startowym wybierz pozycję **Utwórz nowy projekt**.

      ![Tworzenie nowego przycisku projektu wybranego w oknie startowym programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stronie **Tworzenie nowego projektu** wprowadź **konsolę** w polu wyszukiwania. Następnie wybierz **visual basic** z listy Język, a następnie wybierz pozycję Wszystkie **platformy** z listy Platforma. Wybierz szablon **aplikacji konsoli (.NET Core),** a następnie wybierz pozycję **Dalej**.

      ![Wybierz szablon języka Visual Basic dla aplikacji konsoli (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia zainstalowanego. W **Install more tools and features** **obszarze Nie znajdując tego, czego szukasz?** Zostanie otwarty Instalator programu Visual Studio. Upewnij się, że masz zainstalowane obciążenie **programistyczne dla wielu platform .NET Core.**

   1. Na stronie **Konfigurowanie nowego projektu** wprowadź **helloworld** w polu **Nazwa projektu.** Następnie wybierz pozycję **Utwórz**.

   Szablon aplikacji konsoli dla programu .NET Core `Program`automatycznie definiuje klasę `Main`, z <xref:System.String> jedną metodą, która przyjmuje tablicę jako argument. `Main`jest punktem wejścia aplikacji, metodą, która jest wywoływana automatycznie przez czas wykonywania po uruchomieniu aplikacji. Wszystkie argumenty wiersza polecenia podane po uruchomieniu `args` aplikacji są dostępne w parametrze.

   ![Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Szablon tworzy prostą aplikację "Hello World". Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> aby wyświetlić ciąg literału "Hello World!" w oknie konsoli.

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.

   ![Pasek narzędzi programu Visual Studio z zaznaczonym przyciskiem uruchamiania HelloWorld](./media/with-visual-studio/run-program.png)

   Zostanie otwarte okno konsoli z tekstem "Hello World!" wydrukowane na ekranie i niektóre informacje debugowania programu Visual Studio.

   ![Okno konsoli z wyświetlonym klawiszem Hello World Naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhance-the-app"></a>Ulepszanie aplikacji

Popraw aplikację, aby monitować użytkownika o jego nazwę i wyświetlić ją wraz z datą i godziną. Poniższe instrukcje modyfikują i ponownie uruchamiają aplikację:

# <a name="c"></a>[C #](#tab/csharp)

1. Zamień zawartość `Main` metody, która jest obecnie tylko `Console.WriteLine`wiersz, który wywołuje , z następującym kodem:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ten kod wyświetla "Jak się nazywasz?" w oknie konsoli i czeka, aż użytkownik wejdzie ciąg, a następnie klawisz Enter. Przechowuje ten ciąg w `name`zmiennej o nazwie . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje ją `date`do zmiennej o nazwie . Na koniec używa [interpolowany ciąg](../../csharp/language-reference/tokens/interpolated.md) do wyświetlania tych wartości w oknie konsoli.

1. Skompiluj program, wybierając **rozwiązanie kompilacji .** > **Build Solution**

1. Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter.**

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Zamień zawartość `Main` metody, która jest obecnie tylko `Console.WriteLine`wiersz, który wywołuje , z następującym kodem:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ten kod wyświetla "Jak się nazywasz?" w oknie konsoli i czeka, aż użytkownik wejdzie ciąg, a następnie klawisz Enter. Przechowuje ten ciąg w `name`zmiennej o nazwie . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje ją `date`do zmiennej o nazwie . Na koniec używa [interpolowany ciąg](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) do wyświetlania tych wartości w oknie konsoli.

1. Skompiluj program, wybierając **rozwiązanie kompilacji .** > **Build Solution**

1. Aby uruchomić program, wybierz **helloworld** na pasku narzędzi lub naciśnij **klawisz F5**.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter.**

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

---

## <a name="next-steps"></a>Następne kroki

W tym artykule utworzono i uruchom i uruchom pierwszą aplikację .NET Core. W następnym kroku debugujesz aplikację.

> [!div class="nextstepaction"]
> [Debugowanie aplikacji .NET Core Hello World w programie Visual Studio](debugging-with-visual-studio.md)
