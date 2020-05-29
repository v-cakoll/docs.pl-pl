---
title: Tworzenie aplikacji konsolowej przy użyciu platformy .NET Core w programie Visual Studio
description: Dowiedz się, jak utworzyć aplikację konsolową .NET Core w języku C# lub Visual Basic przy użyciu programu Visual Studio.
author: BillWagner
ms.author: wiwagn
ms.date: 05/20/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 9c3456cd8c940e53e8a70c1d3a7c3b09de77c21d
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201586"
---
# <a name="tutorial-create-a-net-core-console-application-in-visual-studio-2019"></a>Samouczek: Tworzenie aplikacji konsolowej .NET Core w programie Visual Studio 2019

W tym samouczku przedstawiono sposób tworzenia i uruchamiania aplikacji konsolowej .NET Core w programie Visual Studio 2019.

## <a name="prerequisites"></a>Wymagania wstępne

- [Program Visual Studio 2019 w wersji 16,6 lub nowszej](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) z zainstalowanym **wieloplatformowym obciążeniem programistycznym dla platformy .NET Core** . Zestaw .NET Core 3,1 SDK jest instalowany automatycznie po wybraniu tego obciążenia.

  Aby uzyskać więcej informacji, zobacz sekcję [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) w artykule [Instalowanie zestaw .NET Core SDK](../install/sdk.md?pivots=os-windows) .

## <a name="create-the-app"></a>Tworzymy aplikację.

<!-- markdownlint-disable MD025 -->

1. Otwórz program Visual Studio 2019.

1. Utwórz nowy projekt aplikacji konsoli .NET Core o nazwie "HelloWorld".

   1. Na stronie startowej wybierz pozycję **Utwórz nowy projekt**.

      ![Przycisk Utwórz nowy projekt wybrany na stronie startowej programu Visual Studio](./media/with-visual-studio/start-window.png)

   1. Na stronie **Tworzenie nowego projektu** wprowadź w polu wyszukiwania **konsolę** . Następnie wybierz pozycję **C#** lub **Visual Basic** z listy język, a następnie wybierz pozycję **wszystkie platformy** z listy platform. Wybierz szablon **Aplikacja konsolowa (.NET Core)** , a następnie wybierz przycisk **dalej**.

      ![Utwórz nowe okno projektu z wybranymi filtrami](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > Jeśli nie widzisz szablonów .NET Core, prawdopodobnie brakuje wymaganego obciążenia. W obszarze **nie można znaleźć tego, czego szukasz?** komunikat wybierz łącze **Zainstaluj więcej narzędzi i funkcji** . Zostanie otwarty Instalator programu Visual Studio. Upewnij się, że masz zainstalowaną **Międzyplatformowe obciążenie programistyczne dla platformy .NET Core** .

   1. Na stronie **Konfiguruj nowy projekt** wprowadź **HelloWorld** w polu **Nazwa projektu** . Następnie wybierz pozycję **Utwórz**.

      ![Skonfiguruj okno nowego projektu z nazwą projektu, lokalizacją i polami nazw rozwiązań](./media/with-visual-studio/configure-new-project.png)

   Szablon aplikacji konsoli dla platformy .NET Core definiuje klasę, `Program` przy użyciu pojedynczej metody, `Main` która pobiera <xref:System.String> tablicę jako argument. `Main`jest punktem wejścia aplikacji, metoda, która jest wywoływana automatycznie przez środowisko uruchomieniowe podczas uruchamiania aplikacji. Wszystkie argumenty wiersza polecenia dostarczone podczas uruchamiania aplikacji są dostępne w tablicy *args* .

   Jeśli język, którego chcesz użyć, nie jest wyświetlany, Zmień selektor języka w górnej części strony.

   ```csharp
   using System;

   namespace HelloWorld
   {
       class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello World!");
           }
       }
   }
   ```

   ```vb
   Imports System

   Module Program
       Sub Main(args As String())
           Console.WriteLine("Hello World!")
       End Sub
   End Module
   ```

   Szablon tworzy prostą aplikację "Hello world". Wywołuje metodę, <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> Aby wyświetlić "Hello World!" w oknie konsoli.

## <a name="run-the-app"></a>Uruchomienie aplikacji

1. Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.

   ![Pasek narzędzi programu Visual Studio z wybranym przyciskiem Uruchom jako HelloWorld](./media/with-visual-studio/run-program.png)

   Zostanie otwarte okno konsoli z tekstem "Hello world!" Wydrukowano na ekranie i niektóre informacje debugowania programu Visual Studio.

   ![Okno konsoli z pokazanymi Hello world naciśnij dowolny klawisz, aby kontynuować](./media/with-visual-studio/hello-world-console.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="enhance-the-app"></a>Ulepszanie aplikacji

Podnieś poziom aplikacji, aby monitować użytkownika o jego nazwę i wyświetlić go wraz z datą i godziną. Poniższe instrukcje modyfikują aplikację i uruchamiają ją ponownie:

1. Zastąp zawartość `Main` metody, która jest aktualnie tylko wierszem, który wywołuje `Console.WriteLine` , przy użyciu następującego kodu:

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="Snippet1":::

   Ten kod wyświetla "co to jest Twoja nazwa?" w oknie konsoli i czeka, aż użytkownik wprowadzi ciąg, a następnie klawisz ENTER. Ten ciąg jest przechowywany w zmiennej o nazwie `name` . Pobiera również wartość <xref:System.DateTime.Now?displayProperty=nameWithType> właściwości, która zawiera bieżący czas lokalny i przypisuje go do zmiennej o nazwie `date` ( `currentDate` w Visual Basic). Na koniec wyświetla te wartości w oknie konsoli.

   `\n`( `vbCrLf` W Visual Basic) reprezentuje znak nowego wiersza.

   Znak dolara ( `$` ) przed ciągiem umożliwia umieszczenie wyrażeń takich jak nazwy zmiennych w nawiasach klamrowych w ciągu. Wartość wyrażenia jest wstawiana do ciągu zamiast wyrażenia. Ta składnia jest określana mianem [ciągów interpolowanych](../../csharp/language-reference/tokens/interpolated.md).

1. Aby uruchomić program, wybierz opcję **HelloWorld** na pasku narzędzi lub naciśnij klawisz **F5**.

1. Odpowiedz na monit, wprowadzając nazwę i naciskając klawisz **Enter** .

   ![Okno konsoli ze zmodyfikowanym wyjściem programu](./media/with-visual-studio/hello-world-update.png)

1. Naciśnij dowolny klawisz, aby zamknąć okno konsoli.

## <a name="next-steps"></a>Następne kroki

W tym samouczku utworzono aplikację .NET Core. W następnym samouczku debugujesz aplikację.

> [!div class="nextstepaction"]
> [Debugowanie aplikacji konsolowej .NET Core w programie Visual Studio](debugging-with-visual-studio.md)
