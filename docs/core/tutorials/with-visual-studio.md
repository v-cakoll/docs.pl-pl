---
title: Tworzenie aplikacji C# Hello World przy użyciu platformy .NET Core w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsolową C# .NET Core przy użyciu programu Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: cc7d78006998b79fe9d522e71883ce1af817c051
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428563"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Kompilowanie C# aplikacji Hello World przy użyciu zestaw .NET Core SDK w programie Visual Studio 2017

W tym artykule przedstawiono krok po kroku wprowadzenie do kompilowania, debugowania i publikowania prostej aplikacji konsolowej platformy .NET Core przy C# użyciu programu w programie Visual Studio 2017. Program Visual Studio 2017 udostępnia w pełni funkcjonalne środowisko programistyczne do tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficznych dla platformy, aplikacja może działać na dowolnej platformie, która jest przeznaczona dla platformy .NET Core i w dowolnym systemie, w którym zainstalowano program .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Program Visual Studio 2017 lub nowszy](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym obciążeniem "Programowanie dla wielu platform" platformy .NET Core. Aplikację można opracowywać przy użyciu platformy .NET Core 2,1 lub nowszej.

Aby uzyskać więcej informacji, zobacz artykuł dotyczący [zależności i wymagań platformy .NET Core](../install/sdk.md?tabs=netcore30&pivots=os-windows#install-with-visual-studio).

## <a name="a-simple-hello-world-application"></a>Prosta aplikacja Hello world

Zacznij od utworzenia prostej aplikacji konsolowej "Hello world". Wykonaj następujące kroki:

1. Uruchom program Visual Studio. Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu. W oknie dialogowym **Nowy projekt** wybierz węzeł **wizualizacji C#**  , a następnie węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "HelloWorld". Wybierz przycisk **OK** .

   ![Okno dialogowe nowego projektu z wybraną aplikacją konsolową](./media/with-visual-studio/visual-studio-new-project.png)

1. Program Visual Studio używa szablonu do utworzenia projektu. Szablon C# aplikacji konsoli dla platformy .NET Core automatycznie definiuje klasę, `Program`przy użyciu pojedynczej metody `Main`, która przyjmuje tablicę <xref:System.String> jako argument. `Main` jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

   ![Program Visual Studio i nowy projekt HelloWorld](./media/with-visual-studio/visual-studio-main-window.png)

   Szablon tworzy prostą aplikację "Hello world". Wywołuje metodę <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>, aby wyświetlić ciąg literału "Hello world!" w oknie konsoli. Wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, okno konsoli będzie widoczne tylko dla krótkiego interwału czasu przed jego zamknięciem. Dzieje się tak, ponieważ metoda `Main` kończy działanie, a aplikacja kończy się zaraz po wykonaniu pojedynczej instrukcji w metodzie `Main`.

1. Aby spowodować wstrzymanie aplikacji przed zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu metody <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   Ten kod poprosi użytkownika o naciśnięcie dowolnego klawisza, a następnie wstrzymuje program do momentu naciśnięcia klawisza.

1. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**. Spowoduje to skompilowanie programu do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-Time (JIT).

1. Uruchom program, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi.

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Ulepszanie aplikacji Hello world

Zwiększ swoją aplikację, aby monitować użytkownika o ich nazwę i wyświetlać ją wraz z datą i godziną. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź następujący C# kod w oknie kodu bezpośrednio po nawiasie otwierającym, który następuje po wierszu `static void Main(string[] args)` i przed pierwszym zamykającym nawiasem klamrowym:

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ten kod zastępuje zawartość metody `Main`.

   ![Program Visual Studio c-Sharp plik ze zaktualizowaną metodą Main](./media/with-visual-studio/visual-csharp-code-window.png)

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name`. Pobiera również wartość właściwości <xref:System.DateTime.Now?displayProperty=nameWithType>, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date`. Na koniec używa [ciągu interpolowanego](../../csharp/language-reference/tokens/interpolated.md) , aby wyświetlić te wartości w oknie konsoli.

1. Skompiluj program, wybierając opcję **kompiluj** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając element menu **debuguj** > **Rozpocznij debugowanie** . Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz ENTER.

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Aplikacja została utworzona i uruchomiona. Aby opracować profesjonalną aplikację, wykonaj kilka dodatkowych czynności, aby przygotować aplikację do wydania:

- Aby uzyskać informacje na temat debugowania aplikacji, zobacz [debugowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](debugging-with-visual-studio.md).

- Aby uzyskać informacje na temat tworzenia i publikowania wersji aplikacji do dystrybucji, zobacz temat [publikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-articles"></a>Pokrewne artykuły:

Zamiast aplikacji konsolowej, można również utworzyć bibliotekę klas przy użyciu platformy .NET Core i programu Visual Studio 2017. Aby zapoznać się z krok po kroku, zobacz [Kompilowanie biblioteki klas C# z i .NET Core w programie Visual Studio 2017](library-with-visual-studio.md).

Możesz również opracować aplikację konsolową .NET Core na komputerach Mac, Linux i Windows za pomocą [Visual Studio Code](https://code.visualstudio.com/), do pobrania edytora kodu. Aby zapoznać się z samouczkiem krok po kroku, zobacz [wprowadzenie z Visual Studio Code](with-visual-studio-code.md).
