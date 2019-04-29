---
title: .NET core Witaj, świecie aplikacji za pomocą Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsoli .NET Core za pomocą Visual Basic w programie Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: faa801d8ded90b1a0f68eac1824e60ee6ba468a4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647130"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Tworzenie aplikacji Visual Basic Witaj, świecie przy użyciu zestawu .NET Core SDK w programie Visual Studio 2017

Ten temat zawiera instrukcje krok po kroku wprowadzenie do tworzenia, debugowania i publikowania prostego aplikacji konsolowej .NET Core w języku Visual Basic w programie Visual Studio 2017. Program Visual Studio 2017 zapewnia środowisko projektowe w pełni funkcjonalne służące do tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie przeznaczonego platformy .NET Core i w każdym systemie, który ma zainstalowany .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z zainstalowanym obciążeniem "Programowanie dla wielu platform .NET Core". Można opracować aplikację przy użyciu platformy .NET Core 2.0.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dla platformy .NET Core w Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Prostą aplikację typu Hello World

Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World". Wykonaj następujące kroki:

1. Launch Visual Studio 2017. Wybierz **pliku** > **New** > **projektu** z paska menu. W *nowy projekt** okno dialogowe, wybierz opcję **języka Visual Basic** węzła następuje **platformy .NET Core** węzła. Następnie wybierz pozycję **Aplikacja konsoli (.NET Core)** szablonu projektu. W **nazwa** tekstu wpisz "nazwę HelloWorld". Wybierz przycisk **OK**.

   ![Okno dialogowe nowego projektu za pomocą aplikacji Konsolowej wybrane](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Program Visual Studio używa tego szablonu do utworzenia projektu. Szablon aplikacji konsoli Visual Basic dla platformy .NET Core automatycznie definiuje klasę, `Program`, z jednej metody `Main`, która przyjmuje <xref:System.String> tablic jako argumentu. `Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie w czasie wykonywania po jej uruchomieniu aplikacji. Argumenty wiersza polecenia, dostarczana, gdy aplikacja zostanie uruchomiona, są dostępne w *args* tablicy.

   ![Program Visual Studio i nowego projektu HelloWorld](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Ten szablon tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli. Wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, okno konsoli jest widoczna na interwał krótki czas przed jej zamknięciem. Dzieje się tak dlatego `Main` metoda kończy działanie i aplikacja kończy się najszybciej, jak pojedynczą instrukcję w `Main` metoda jest wykonywana.

1. Aby spowodować, że aplikacja wstrzymać przed jej zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Program to kompilowany na język pośredni (IL), który jest konwertowany na kod binarny przez kompilator just-in-time (JIT).

1. Uruchom program, wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Udoskonalanie aplikacji Hello World

Rozszerz aplikację, aby monitować użytkownika o jej nazwę i wyświetlić go wraz z daty i godziny. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź następujący kod w języku Visual Basic w oknie kodu bezpośrednio po otwierającym, który następuje po `Sub Main(args As String())` wierszu i przed pierwszym nawiasem zamykającym:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcji.

   ![Plik Visual Studio Program przy użyciu zaktualizowanych metody Main](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Ten kod wyświetla "Jak ma nazwę"? w oknie konsoli i czeka, aż użytkownik wprowadza się ciąg, a następnie klawisz Enter. Ten ciąg jest przechowywana w zmiennej o nazwie `name`. Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżący czas lokalny, a następnie przypisuje go do zmiennej o nazwie `currentDate`. Na koniec używa [ciągiem interpolowanym](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) można wyświetlać te wartości w oknie konsoli.

1. Skompilować program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu. Odpowiedzieć na monit podawania nazwy i naciskając klawisz Enter.

   ![Okno konsoli z danych wyjściowych zmodyfikowane programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Został utworzony i uruchom aplikację. Tworzenie profesjonalnych aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:

- Aby debugować aplikację, zobacz [debugowania aplikacji .NET Core Witaj, świecie przy użyciu programu Visual Studio 2017](debugging-with-visual-studio.md).

- Aby opublikować dystrybucyjny wersji aplikacji, zobacz [publikowania aplikacji platformy .NET Core Witaj, świecie przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

Zamiast aplikacji konsoli możesz także tworzyć biblioteki .NET Standard klasy w języku Visual Basic, .NET Core i Visual Studio 2017. Wprowadzenie krok po kroku, zobacz [Tworzenie biblioteki .NET Standard, w języku Visual Basic i .NET Core SDK w programie Visual Studio 2017](vb-library-with-visual-studio.md).
