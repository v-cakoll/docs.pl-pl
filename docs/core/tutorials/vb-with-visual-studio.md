---
title: Tworzenie aplikacji Hello World z platformy .NET Core i Visual Basic w programie Visual Studio 2017 r.
description: "Sposób tworzenia prostej aplikacji konsoli .NET Core za pomocą Visual Basic przy użyciu programu Visual Studio 2017 r."
keywords: Oprogramowanie .NET core aplikacji konsoli .NET Core, programu Visual Studio 2017 r.
author: rpetrusha
ms.author: ronpet
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-vb
dev_langs:
- vb
ms.workload:
- dotnetcore
ms.openlocfilehash: 0e3dbdb5df72963980f459643fcb5f4588e0029f
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2018
---
# <a name="build-a-visual-basic-hello-world-application-with-net-core-in-visual-studio-2017"></a>Tworzenie aplikacji Visual Basic Hello World z platformą .NET Core w Visual Studio 2017 r.

Ten temat zawiera wprowadzenie krok po kroku do tworzenia, debugowania i publikowania prostej aplikacji konsoli .NET Core za pomocą języka Visual Basic w programie Visual Studio 2017 r. Visual Studio 2017 udostępnia środowisko deweloperskie oferujący wszystkie funkcje tworzenia aplikacji platformy .NET Core. Tak długo, jak aplikacja nie ma zależności specyficzne dla platformy, aplikację można uruchomić na dowolnej platformie, którego element docelowy .NET Core i w każdym systemie, który ma zainstalowane oprogramowanie .NET Core.

## <a name="prerequisites"></a>Wymagania wstępne

[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) z obciążeniem "Programowanie wieloplatformowych .NET Core" zainstalowany. Możesz utworzyć aplikację .NET Core 2.0.

Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące .NET Core w systemie Windows](../../core/windows-prerequisites.md).

## <a name="a-simple-hello-world-application"></a>Prostej aplikacji Hello World

Rozpocznij od utworzenia prostej aplikacji konsoli "Hello World". Wykonaj następujące kroki:

1. Launch Visual Studio 2017. Wybierz **pliku** > **nowy** > **projektu** na pasku menu. W *nowy projekt** okno dialogowe, wybierz opcję **Visual Basic** węzła następuje **.NET Core** węzła. Następnie wybierz **aplikacji konsoli (.NET Core)** szablonu projektu. W **nazwa** tekstu wpisz "HelloWorld". Wybierz **OK** przycisku.

   ![Okno dialogowe nowego projektu z aplikacji konsoli wybrane](./media/vb-with-visual-studio/new-project.png)
   
1. Visual Studio używa tego szablonu do tworzenia projektu. Szablon aplikacji konsoli języka Visual Basic .NET Core automatycznie definiuje klasę, `Program`, z jedną metodę `Main`, która pobiera <xref:System.String> tablic jako argumentu. `Main` jest punkt wejścia aplikacji, metody, która jest wywoływana automatycznie przez środowisko uruchomieniowe uruchamianiem aplikacji. Są dostępne w żadnych argumentów wiersza polecenia dostarczana, gdy aplikacja jest uruchamiana *argumentów* tablicy.

   ![Nowy projekt HelloWorld i Visual Studio](./media/vb-with-visual-studio/devenv.png)

   Szablon tworzy prostą aplikację "Hello World". Wywołuje <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metodę w celu wyświetlenia literału ciągu "Hello World!" w oknie konsoli. Wybierając **HelloWorld** przycisk z zieloną strzałką na pasku narzędzi, można uruchomić program w trybie debugowania. Jeśli to zrobisz, w oknie konsoli jest widoczna tylko interwał krótki czas przed jego zamknięciem. Dzieje się tak dlatego `Main` kończy — metoda i kończenia aplikacji tak szybko, jak jednej instrukcji w `Main` metoda jest wykonywana.

1. Aby spowodować, że aplikacja wstrzymać przed jego zamknięciem okna konsoli, Dodaj następujący kod bezpośrednio po wywołaniu <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> metody:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Ten kod monituje użytkownika o naciśnij dowolny klawisz, a następnie zatrzymuje program, dopóki nie zostanie naciśnięty klawisz.

1. Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**. Program to kompiluje się na język pośredni (IL), który jest konwertowany na kod binarny za pomocą kompilatora just-in-time (JIT).

1. Uruchom program wybierając **HelloWorld** przycisk z zieloną strzałkę na pasku narzędzi.

   ![Okno konsoli przedstawiający Hello World naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/helloworld1.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhancing-the-hello-world-application"></a>Rozszerzanie aplikacji Hello World

Ulepszanie aplikację do monitowania użytkownika o jej nazwę, aby go wyświetlić, oraz datę i godzinę. Aby zmodyfikować i przetestować program, wykonaj następujące czynności:

1. Wprowadź poniższy kod Visual Basic w oknie Kod bezpośrednio po otwierającym znajdujący się `Sub Main(args As String())` wierszu i przed pierwszym zamykający nawias kwadratowy:

   [!code-vb[GettingStarted#1](../../../samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   Ten kod zastępuje istniejące <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, <xref:System.Console.Write%2A?displayProperty=nameWithType>, i <xref:System.Console.ReadKey%2A?displayProperty=nameWithType> instrukcje.

   ![Visual Studio Program pliku z zaktualizowana metoda Main](./media/vb-with-visual-studio/codewindow.png)

   Ten kod wyświetla "Co to jest nazwa?" w oknie konsoli i czeka, dopóki użytkownik wprowadza ciąg, a następnie klawisz Enter. Ten ciąg jest przechowywana w zmiennej o nazwie `name`. Również pobiera wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwość, która zawiera bieżącym czasem lokalnym i przypisuje go do zmiennej o nazwie `currentDate`. Na koniec używa [interpolowane ciąg](../../csharp/language-reference/keywords/interpolated-strings.md) do wyświetlania tych wartości w oknie konsoli.

1. Kompiluj program, wybierając **kompilacji** > **Kompiluj rozwiązanie**.

1. Uruchom program w trybie debugowania w programie Visual Studio, wybierając zieloną strzałkę na pasku narzędzi, naciskając klawisz F5 lub wybierając pozycję **debugowania** > **Rozpocznij debugowanie** elementu menu. Odpowiadanie na ten monit wprowadzania nazwy i naciskając klawisz Enter.

   ![Okno konsoli z danych wyjściowych programu zmodyfikowane](./media/with-visual-studio/helloworld2.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

Utworzeniu i uruchom aplikację. Aby opracować professional aplikacji, należy wykonać dodatkowe kroki w celu przygotowania aplikacji do wersji:

- Informacje dotyczące debugowania aplikacji znajdują się w temacie [debugowania aplikacji C# Hello World z programu Visual Studio 2017](debugging-with-visual-studio.md).

- Informacje dotyczące tworzenia i publikowania dystrybucyjnego wersji aplikacji, zobacz [publikowania aplikacji C# Hello World z programu Visual Studio 2017](publishing-with-visual-studio.md).

<!--
## Related topics

Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017. For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).

You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor. For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md). -->
