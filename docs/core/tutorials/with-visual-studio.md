---
title: Tworzenie aplikacji Hello World z platformy .NET Core i C# w programie Visual Studio 2017 r.
description: Sposób tworzenia prostej aplikacji konsoli .NET Core za pomocą C# za pomocą programu Visual Studio 2017 r.
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.openlocfilehash: d68ae899e5dc7c37a9c92e79aeae452b000b0960
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218023"
---
# <a name="build-a-c-hello-world-application-with-net-core-in-visual-studio-2017"></a>Tworzenie aplikacji C# Hello World z platformą .NET Core w Visual Studio 2017 r.

Ten temat zawiera wprowadzenie krok po kroku do tworzenia, debugowania i użyciu języka C# w programie Visual Studio 2017 prostej aplikacji konsoli .NET Core publikacji. Visual Studio 2017 udostępnia środowisko deweloperskie oferujący wszystkie funkcje tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie, którego element docelowy .NET Core i w każdym systemie, który ma zainstalowane oprogramowanie .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany. Możesz utworzyć aplikację .NET Core 1.1 lub .NET Core 2.0.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](../../core/windows-prerequisites.md) tematu.

## <a name="a-simple-hello-world-application"></a>Prostej aplikacji Hello World

Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World". Wykonaj następujące kroki:

1. Uruchom program Visual Studio 2017 r. Wybierz **pliku** > **nowy** > **projektu** na pasku menu. W *nowy projekt** okno dialogowe, wybierz opcję **Visual C#** węzła następuje **.NET Core** węzła. Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** tekstu wpisz "HelloWorld". Wybierz **OK** przycisku.

   ![Okno dialogowe nowego projektu z aplikacji konsoli wybrane](./media/with-visual-studio/newproject.png)
   
1. Visual Studio używa tego szablonu do tworzenia projektu. Szablon aplikacji Konsolowej C# .NET Core automatycznie definiuje klasę, `Program`, z jedną metodę `Main`, która pobiera <xref:System.String> tablic jako argumentu. `Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie przez środowisko uruchomieniowe uruchamianiem aplikacji. Są dostępne w żadnych argumentów wiersza polecenia dostarczana, gdy aplikacja jest uruchamiana *argumentów* tablicy.

   ![Nowy projekt HelloWorld i Visual Studio](./media/with-visual-studio/devenv.png)

   Szablon tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli. Wybierając **HelloWorld** przycisk z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, w oknie konsoli jest widoczna tylko interwał krótki czas przed jego zamknięciem. Dzieje się tak dlatego `Main` kończy — metoda i kończenia aplikacji tak szybko, jak jednej instrukcji w `Main` metoda jest wykonywana.

1. Aby spowodować, że aplikacja wstrzymać przed jego zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```
   Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Program to kompiluje się na język pośredni (IL), który jest konwertowany na kod binarny za pomocą kompilatora just-in-time (JIT).

1. Uruchom program wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/helloworld1.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Rozszerzanie aplikacji Hello World

Ulepszanie aplikacji monit o podanie nazwy i wyświetlić je wraz z datą i godziną. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź poniższy kod C# w oknie Kod bezpośrednio po otwierającym znajdujący się `static void Main(string[] args)` wierszu i przed pierwszym zamykający nawias kwadratowy:

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcje.

   ![Visual Studio Program c sharp pliku z zaktualizowana metoda Main](./media/with-visual-studio/codewindow.png)

   Ten kod wyświetla "Co to jest nazwa?" w oknie konsoli i czeka, dopóki użytkownik wprowadza ciąg, a następnie klawisz Enter. Ten ciąg jest przechowywana w zmiennej o nazwie `name`. Również pobiera wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżącym czasem lokalnym i przypisuje go do zmiennej o nazwie `date`. Na koniec używa [interpolowane ciąg](../../csharp/language-reference/tokens/interpolated.md) do wyświetlania tych wartości w oknie konsoli.

1. Kompiluj program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu. Odpowiadanie na ten monit wprowadzania nazwy i naciskając klawisz Enter.

   ![Okno konsoli z danych wyjściowych programu zmodyfikowane](./media/with-visual-studio/helloworld2.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Utworzeniu i uruchom aplikację. Aby opracować professional aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:

- Informacje dotyczące debugowania aplikacji znajdują się w temacie [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md).

- Informacje dotyczące tworzenia i publikowania dystrybucyjnego wersji aplikacji, zobacz [publikowania aplikacji C# Hello World z programu Visual Studio 2017](publishing-with-visual-studio.md).

## <a name="related-topics"></a>Tematy pokrewne

Zamiast aplikacją konsoli, można także utworzyć biblioteki klas .NET Core i Visual Studio 2017 r. Wprowadzenie krok po kroku, zobacz [tworzenia biblioteki klas C# i .NET Core w Visual Studio 2017](library-with-visual-studio.md).

Można również tworzyć aplikacji konsoli .NET Core, Mac, Linux i Windows za pomocą [Visual Studio Code](https://code.visualstudio.com/), edytora kodu do pobrania. Samouczek krok po kroku, zobacz [wprowadzenie do korzystania z programu Visual Studio Code](with-visual-studio-code.md).
