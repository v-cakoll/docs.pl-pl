---
title: Tworzenie aplikacji Hello world przy użyciu platformy .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć swoją pierwszą aplikację konsolową .NET Core za pomocą języka C# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 738fc49a820c3c5d94fb35c1bf7a8b718ed75cb3
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394823"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a>Samouczek: Tworzenie pierwszej aplikacji konsolowej .NET Core w programie Visual Studio 2019

Ten artykuł zawiera instrukcje krok po kroku dotyczące tworzenia i Hello world uruchamiania aplikacji konsolowej programu .NET Core w programie Visual Studio 2019. Aplikacja Hello world jest tradycyjnie używana do wprowadzenia początkujących do nowego języka programowania. Ten program po prostu wyświetla frazę "Hello world!" na ekranie.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019 w wersji 16,4 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** . Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.

Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Tworzymy aplikację.

Poniższe instrukcje tworzą prostą aplikację konsolową Hello world:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

1. Otwórz program Visual Studio 2019.

1. Utwórz nowy projekt aplikacji konsolowej C# .NET Core o nazwie "HelloWorld".

   1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** . Następnie wybierz pozycję **C#** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

      ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia. W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Zostanie otwarty Instalator programu Visual Studio. Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

      ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

   Szablon aplikacji konsolowej w języku C# dla platformy .NET Core automatycznie definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument. `Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Otwórz program Visual Studio 2019.

1. Utwórz Visual Basic nowy projekt aplikacji konsoli programu .NET Core o nazwie "HelloWorld".

   1. W oknie uruchamiania wybierz pozycję **Utwórz nowy projekt**.

      ![Przycisk Utwórz nowy projekt wybrany w oknie uruchamiania programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** . Następnie wybierz **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

      ![Wybierz szablon Visual Basic dla aplikacji konsolowej (.NET Framework)](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia. W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Zostanie otwarty Instalator programu Visual Studio. Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

   Szablon aplikacji konsoli dla platformy .NET Core automatycznie definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która przyjmuje <xref:System.String> tablicę jako argument. `Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w `args` parametrze.

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   Szablon tworzy prostą aplikację "Hello world". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie konsoli.

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.

   ![Pasek narzędzi programu Visual Studio z wybranym przyciskiem Uruchom jako HelloWorld](./media/with-visual-studio/run-program.png)

   Zostanie otwarte okno konsoli z tekstem "Hello world!" Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhance-the-app"></a>Ulepszanie aplikacji

Zwiększ swoją aplikację, aby monitować użytkownika o ich nazwę i wyświetlać ją wraz z datą i godziną. Poniższe instrukcje modyfikują i uruchamiają aplikację ponownie:

# <a name="c"></a>[C#](#tab/csharp)

1. Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/HelloWorld.cs#1)]

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name` . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` . Na koniec używa [ciągu interpolowanego](../../csharp/language-reference/tokens/interpolated.md) , aby wyświetlić te wartości w oknie konsoli.

1. Skompiluj program, **wybierając opcję Kompiluj**  >  **kompilację rozwiązania**.

1. Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

1. Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/Program.vb#1)]

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name` . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` . Na koniec używa [ciągu interpolowanego](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) , aby wyświetlić te wartości w oknie konsoli.

1. Skompiluj program, **wybierając opcję Kompiluj**  >  **kompilację rozwiązania**.

1. Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

---

## <a name="next-steps"></a>Następne kroki

W tym artykule opisano tworzenie i uruchamianie pierwszej aplikacji .NET Core. W następnym kroku debugujesz aplikację.

> [!div class="nextstepaction"]
> [Debugowanie aplikacji Hello world .NET Core w programie Visual Studio](debugging-with-visual-studio.md)
