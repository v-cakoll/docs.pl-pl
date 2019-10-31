---
title: Aplikacja .NET Core Hello world z Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsolową platformy .NET Core z Visual Basic przy użyciu programu Visual Studio 2017.
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 1200afb30c6bdebf66b2a1e080c62a776a7e9826
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100875"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Tworzenie aplikacji Hello world Visual Basic przy użyciu zestaw .NET Core SDK w programie Visual Studio 2017

W tym temacie przedstawiono krok po kroku wprowadzenie do kompilowania, debugowania i publikowania prostej aplikacji konsolowej platformy .NET Core przy użyciu Visual Basic w programie Visual Studio 2017. Program Visual Studio 2017 udostępnia w pełni funkcjonalne środowisko programistyczne do tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficznych dla platformy, aplikacja może działać na dowolnej platformie, która jest przeznaczona dla platformy .NET Core i w dowolnym systemie, w którym zainstalowano program .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core". Aplikację można opracowywać przy użyciu platformy .NET Core 2,1 lub nowszej.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące platformy .NET Core w systemie Windows](../windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Prosta aplikacja Hello world

Zacznij od utworzenia prostej aplikacji konsolowej "Hello world". Wykonaj następujące kroki:

1. Uruchom program Visual Studio 2017. Wybierz pozycję **plik** > **Nowy** > **projekt** na pasku menu. W oknie dialogowym *Nowy projekt** wybierz węzeł **Visual Basic** , po którym następuje węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "HelloWorld". Wybierz przycisk **OK** .

   ![Okno dialogowe nowego projektu z wybraną aplikacją konsolową](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Program Visual Studio używa szablonu do utworzenia projektu. Szablon aplikacji konsoli Visual Basic dla platformy .NET Core automatycznie definiuje klasę, `Program`, przy użyciu pojedynczej metody, `Main`, która przyjmuje tablicę <xref:System.String> jako argument. `Main` jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

   ![Program Visual Studio i nowy projekt HelloWorld](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Szablon tworzy prostą aplikację "Hello world". Wywołuje metodę <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>, aby wyświetlić ciąg literału "Hello world!" w oknie konsoli. Wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, okno konsoli będzie widoczne tylko dla krótkiego interwału czasu przed jego zamknięciem. Dzieje się tak, ponieważ metoda `Main` kończy działanie, a aplikacja kończy się zaraz po wykonaniu pojedynczej instrukcji w metodzie `Main`.

1. Aby spowodować wstrzymanie aplikacji przed zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu metody <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Ten kod poprosi użytkownika o naciśnięcie dowolnego klawisza, a następnie wstrzymuje program do momentu naciśnięcia klawisza.

1. Na pasku menu wybierz kolejno opcje **kompiluj** > **Kompiluj rozwiązanie**. Spowoduje to skompilowanie programu do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-Time (JIT).

1. Uruchom program, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi.

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Ulepszanie aplikacji Hello world

Zwiększ swoją aplikację, aby monitować użytkownika o jego nazwę i wyświetlić ją wraz z datą i godziną. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź następujący kod Visual Basic w oknie kodu bezpośrednio po nawiasie otwierającym, który następuje po wierszu `Sub Main(args As String())` i przed pierwszym nawiasem zamykającym:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ten kod zastępuje zawartość metody `Main`.

   ![Plik programu Visual Studio ze zaktualizowaną metodą Main](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name`. Pobiera również wartość właściwości <xref:System.DateTime.Now?displayProperty=nameWithType>, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `currentDate`. Na koniec używa [ciągu interpolowanego](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) , aby wyświetlić te wartości w oknie konsoli.

1. Skompiluj program, wybierając opcję **kompiluj** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając element menu **debuguj** > **Rozpocznij debugowanie** . Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz ENTER.

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Aplikacja została utworzona i uruchomiona. Aby opracować profesjonalną aplikację, wykonaj kilka dodatkowych czynności, aby przygotować aplikację do wydania:

- Aby debugować aplikację, zobacz [debugowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](debugging-with-visual-studio.md).

- Aby opublikować wersję dystrybucyjną aplikacji, zobacz temat [publikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

Zamiast aplikacji konsolowej, można również utworzyć bibliotekę klas .NET Standard z Visual Basic, .NET Core i Visual Studio 2017. Aby zapoznać się z krok po kroku, zobacz [Tworzenie biblioteki .NET Standard z Visual Basic i zestaw .NET Core SDK w programie Visual Studio 2017](vb-library-with-visual-studio.md).
