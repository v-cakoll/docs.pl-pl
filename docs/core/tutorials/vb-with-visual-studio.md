---
title: Aplikacja .NET Core Hello world z Visual Basic w programie Visual Studio 2017
description: Dowiedz się, jak utworzyć prostą aplikację konsolową platformy .NET Core z Visual Basic przy użyciu programu Visual Studio 2017.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
dev_langs:
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b4f3cc055f73332db1348ef35174beab614df147
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039612"
---
# <a name="build-a-visual-basic-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a>Tworzenie aplikacji Hello world Visual Basic przy użyciu zestaw .NET Core SDK w programie Visual Studio 2017

W tym temacie przedstawiono krok po kroku wprowadzenie do kompilowania, debugowania i publikowania prostej aplikacji konsolowej platformy .NET Core przy użyciu Visual Basic w programie Visual Studio 2017. Program Visual Studio 2017 udostępnia w pełni funkcjonalne środowisko programistyczne do tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficznych dla platformy, aplikacja może działać na dowolnej platformie, która jest przeznaczona dla platformy .NET Core i w dowolnym systemie, w którym zainstalowano program .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Program Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z zainstalowanym obciążeniem "Programowanie dla wielu platform w środowisku .NET Core". Aplikację można opracowywać przy użyciu platformy .NET Core 2,1 lub nowszej.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące platformy .NET Core w systemie Windows](../windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Prosta aplikacja Hello world

Zacznij od utworzenia prostej aplikacji konsolowej "Hello world". Wykonaj następujące kroki:

1. Uruchom program Visual Studio 2017. Na pasku menu wybierz pozycję **plik** > **Nowy** > **projekt** . W oknie dialogowym *Nowy projekt** wybierz węzeł **Visual Basic** , po którym następuje węzeł **.NET Core** . Następnie wybierz szablon projektu **aplikacja konsoli (.NET Core)** . W polu tekstowym **Nazwa** wpisz "HelloWorld". Wybierz przycisk **OK**.

   ![Okno dialogowe nowego projektu z wybraną aplikacją konsolową](./media/vb-with-visual-studio/visual-studio-new-project.png)

1. Program Visual Studio używa szablonu do utworzenia projektu. Szablon aplikacji konsoli Visual Basic dla platformy .NET Core automatycznie definiuje klasę, `Program`przy użyciu pojedynczej `Main`metody, która przyjmuje <xref:System.String> tablicę jako argument. `Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

   ![Program Visual Studio i nowy projekt HelloWorld](./media/vb-with-visual-studio/visual-studio-main-window.png)

   Szablon tworzy prostą aplikację "Hello world". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia ciągu literału "Hello World!" w oknie konsoli. Wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, okno konsoli będzie widoczne tylko dla krótkiego interwału czasu przed jego zamknięciem. Dzieje się `Main` tak, ponieważ metoda kończy działanie, a aplikacja kończy się zaraz po wykonaniu pojedynczej `Main` instrukcji w metodzie.

1. Aby spowodować wstrzymanie aplikacji przed zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```

   Ten kod poprosi użytkownika o naciśnięcie dowolnego klawisza, a następnie wstrzymuje program do momentu naciśnięcia klawisza.

1. Na pasku menu wybierz pozycję **kompilacja** > Kompiluj**rozwiązanie**. Spowoduje to skompilowanie programu do języka pośredniego (IL), który jest konwertowany na kod binarny przez kompilator just-in-Time (JIT).

1. Uruchom program, wybierając przycisk **HelloWorld** z zieloną strzałką na pasku narzędzi.

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Ulepszanie aplikacji Hello world

Zwiększ swoją aplikację, aby monitować użytkownika o jego nazwę i wyświetlić ją wraz z datą i godziną. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź następujący kod Visual Basic w oknie kodu bezpośrednio po nawiasie otwierającym, który następuje `Sub Main(args As String())` po wierszu i przed pierwszym nawiasem zamykającym:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ten kod zastępuje zawartość `Main` metody.

   ![Plik programu Visual Studio ze zaktualizowaną metodą Main](./media/vb-with-visual-studio/visual-basic-code-window.png)

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name`. Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `currentDate`. Na koniec używa [ciągu interpolowanego](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) , aby wyświetlić te wartości w oknie konsoli.

1. Skompiluj program, **wybierając opcję** > Kompiluj**kompilację rozwiązania**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając > element menu**Rozpocznij debugowanie** debugowania. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz ENTER.

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Aplikacja została utworzona i uruchomiona. Aby opracować profesjonalną aplikację, wykonaj kilka dodatkowych czynności, aby przygotować aplikację do wydania:

- Aby debugować aplikację, zobacz [debugowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](debugging-with-visual-studio.md).

- Aby opublikować wersję dystrybucyjną aplikacji, zobacz temat [publikowanie aplikacji .NET Core Hello World przy użyciu programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

Zamiast aplikacji konsolowej, można również utworzyć bibliotekę klas .NET Standard z Visual Basic, .NET Core i Visual Studio 2017. Aby zapoznać się z krok po kroku, zobacz [Tworzenie biblioteki .NET Standard z Visual Basic i zestaw .NET Core SDK w programie Visual Studio 2017](vb-library-with-visual-studio.md).
