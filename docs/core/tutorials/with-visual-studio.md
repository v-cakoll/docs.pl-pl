---
title: Tworzenie aplikacji Hello World platformy .NET Core w języku C# w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsoli .NET Core przy użyciu języka C# za pomocą programu Visual Studio 2017.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet
ms.openlocfilehash: 031c0a433391fbe4cdd40f6ce648f476787baf48
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594364"
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Tworzenie aplikacji C# Hello World z platformą .NET Core w programie Visual Studio 2017

Ten temat zawiera instrukcje krok po kroku wprowadzenie do tworzenia, debugowania i publikowania prostego aplikacji konsolowej .NET Core przy użyciu języka C# w programie Visual Studio 2017. Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie przeznaczonego platformy .NET Core i w każdym systemie, który ma zainstalowany .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core". Można opracować aplikację przy użyciu platformy .NET Core 1.1 lub .NET Core 2.0.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../../core/windows-prerequisites.md) tematu.

## <a name="a-simple-hello-world-application"></a>Prostą aplikację typu Hello World

Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World". Wykonaj następujące kroki:

1. Uruchom program Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W *nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** tekstu wpisz "nazwę HelloWorld". Wybierz **OK** przycisku.

   ![Okno dialogowe nowego projektu za pomocą aplikacji Konsolowej wybrane](./media/with-visual-studio/newproject.png)
   
1. Program Visual Studio używa tego szablonu do utworzenia projektu. Szablon aplikacji Konsolowej C# dla platformy .NET Core automatycznie definiuje klasę, `Program`, z jedną metodą `Main`, która przyjmuje <xref:System.String> tablic jako argumentu. `Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie w czasie wykonywania po jej uruchomieniu aplikacji. Argumenty wiersza polecenia, dostarczana, gdy aplikacja zostanie uruchomiona, są dostępne w *args* tablicy.

   ![Program Visual Studio i nowego projektu HelloWorld](./media/with-visual-studio/devenv.png)

   Ten szablon tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli. Wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, okno konsoli jest widoczna na interwał krótki czas przed jej zamknięciem. Dzieje się tak dlatego `Main` metoda kończy działanie i aplikacja kończy się najszybciej, jak pojedynczą instrukcję w `Main` metoda jest wykonywana.

1. Aby spowodować, że aplikacja wstrzymać przed jej zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Program to kompilowany na język pośredni (IL), który jest konwertowany na kod binarny przez kompilator just-in-time (JIT).

1. Uruchom program, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/helloworld1.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Udoskonalanie aplikacji Hello World

Rozszerz aplikację, aby monitować użytkownika o ich nazwy i wyświetl ją wraz z daty i godziny. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź następujący kod C# w oknie kodu bezpośrednio po otwierającym, który następuje po `static void Main(string[] args)` wierszu i przed pierwszym nawiasem zamykającym:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcji.

   ![Plik c sharp Visual Studio Program przy użyciu zaktualizowanych metody Main](./media/with-visual-studio/codewindow.png)

   Ten kod wyświetla "Jak ma nazwę"? w oknie konsoli i czeka, aż użytkownik wprowadza się ciąg, a następnie klawisz Enter. Ten ciąg jest przechowywana w zmiennej o nazwie `name`. Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżący czas lokalny, a następnie przypisuje go do zmiennej o nazwie `date`. Na koniec używa [ciągiem interpolowanym](../../csharp/language-reference/tokens/interpolated.md) można wyświetlać te wartości w oknie konsoli.

1. Skompilować program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu. Odpowiedzieć na monit podawania nazwy i naciskając klawisz Enter.

   ![Okno konsoli z danych wyjściowych zmodyfikowane programu](./media/with-visual-studio/helloworld2.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Został utworzony i uruchom aplikację. Tworzenie profesjonalnych aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:

- Aby uzyskać informacje na temat debugowania aplikacji, zobacz [debugowania języka C# aplikacji Hello World w programie Visual Studio 2017](debugging-with-visual-studio.md).

- Aby uzyskać informacje na temat tworzenia i publikowania dystrybucyjny wersji aplikacji, zobacz [publikowania C# aplikacji Hello World w programie Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

Zamiast aplikacji konsoli możesz także tworzyć biblioteki klas w języku .NET Core i Visual Studio 2017. Wprowadzenie krok po kroku, zobacz [tworzenia biblioteki klas w języku C# i .NET Core w programie Visual Studio 2017](library-with-visual-studio.md).

Możesz też opracować aplikację konsoli .NET Core na komputerach Mac, Linux i Windows przy użyciu [programu Visual Studio Code](https://code.visualstudio.com/), Edytor kodu do pobrania. Aby uzyskać samouczek krok po kroku, zobacz [rozpoczęcie korzystania z programu Visual Studio Code](with-visual-studio-code.md).
