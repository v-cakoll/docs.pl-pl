---
title: "Podręcznik języka F#"
description: "Ten przewodnik zawiera przegląd różnych materiałów szkoleniowych w F #, funkcjonalny język programowania, który działa na platformie .NET."
author: jackfoxy
ms.author: phcart
ms.date: 03/19/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 8be5ac5090e10ae9270e7eec529bd9b7c3c663fb
ms.sourcegitcommit: 32172ca05d5dcce7ef3d327b9c8639c736e0fe2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2018
---
# <a name="f-guide"></a>Podręcznik języka F#

F # jest funkcjonalny język programowania, który działa na platformie .NET. Ponadto wprowadzono pełną obsługę dla obiektów, umożliwiając mieszanego funkcjonalności i programowania obiektu pragmatyczne rozwiązania wszelkich problemów.

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

F # jest o wydajność Centrum. Powszechna i pełne zaawansowanych funkcji jest obsługa narzędzi F #.

## <a name="learning-f"></a>Learning F # #

[Samouczek języka F #](tour.md) zawiera omówienie funkcji języka główne z dużą ilością przykładów kodu. Jest to zalecane, jeśli dopiero zaczynasz korzystać z języka F # i chcesz uzyskać pewne pojęcie zasady działania języka.

[Rozpoczynanie pracy z F # w programie Visual Studio](get-started/get-started-visual-studio.md) Jeśli komputer znajduje się w systemie Windows i chcesz pełne środowisko programu Visual Studio IDE (Integraded Development Environment).

[Rozpoczynanie pracy z F # w programie Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) Jeśli teraz macOS i chcesz użyć programu Visual Studio IDE.

[Rozpoczynanie pracy z F # w programie Visual Studio Code](get-started/get-started-vscode.md) Jeśli chcesz lekkie, obsługujący wiele platform i środowisko IDE z zaawansowanymi funkcjami.

[Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core](get-started/get-started-command-line.md) Jeśli chcesz użyć narzędzia wiersza polecenia.

## <a name="references"></a>Odwołania

[Dokumentacja języka F #](language-reference/index.md) jest odwołaniem urzędnika, kompleksowe dla wszystkich funkcji języka F #. Każdego artykułu opisano składnię i zawiera przykłady kodu. Pasek filtru w spisie treści umożliwia powinny być określone.

[Dokumentacja biblioteki podstawowej F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) jest odwołanie do interfejsu API biblioteki podstawowej F #.

## <a name="additional-guides"></a>Dodatkowe przewodniki

[F # dla zabawy i zysku](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) kompleksowe i bardzo szczegółowe książki na uczenia F #. Jego zawartość i autora są ukochanego przez społeczność F #. Odbiorcy docelowi jest głównie deweloperom obiektowej tła programowania.

[F # programowania Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) jest wikibook o uczenia F #. Istnieje również produktu społeczności F #. Odbiorcy docelowi jest osoby, które są nowe w F #, z niewielki obiektowej programowania tła.

## <a name="learn-f-through-videos"></a>Informacje F # za pomocą wideo

[Samouczek języka F # na działanie serwisu YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) jest doskonałym wprowadzenie do F # za pomocą programu Visual Studio, przedstawiający partii dużą przykłady w trakcie 1,5 godziny. Odbiorcy docelowi jest deweloperów programu Visual Studio, nowi F #.

[Wprowadzenie do programowania w języku F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) jest doskonałym wideo serii, która korzysta z programu Visual Studio Code edytorem głównego. Seria filmów zaczyna się od nothing i kończy się tworzenie gry wideo RPG tekstowy. Odbiorcy docelowi jest deweloperów, którzy preferowane Visual Studio Code (lub lekkie IDE) i dopiero zaczynasz korzystać z języka F #.

[What's New in Visual Studio 2017 dla F # dla programistów](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) jest kursu wideo, który zawiera niektóre nowsze funkcje w F # w programie Visual Studio 2017 r. Odbiorcy docelowi jest deweloperów programu Visual Studio, nowi F #.

## <a name="other-useful-resources"></a>Inne przydatne zasoby

[Witryny sieci Web wstawki kodu programu F #](http://www.fssnip.net) zawiera zestaw ogromną przedstawiający sposób wykonywania wszystko, co w języku F #, od bezwzględny dla początkujących użytkowników do bardzo zaawansowane wstawki fragmentów kodu.

[Slack Foundation oprogramowania F #](http://fsharp.org/guides/slack/) jest doskonałym miejscem dla początkujących i ekspertów podobne, jest bardzo aktywny, a niektóre na świecie najlepsze F # programistów dla Czat. Zdecydowanie zaleca się dołączenie.

## <a name="the-f-software-foundation"></a>Foundation oprogramowania F #

Mimo że Microsoft głównej deweloperów języka F # i jej narzędzi w programie Visual Studio, F # nie jest również obsługiwana przez niezależnych foundation, F # oprogramowania Foundation (FSSF).

Misji Foundation oprogramowania F # jest podwyższyć poziom, ochronę i poprawić język programowania, F # i obsługuje i ułatwić rozwój różnych i międzynarodową społeczność programistów F #.

Aby dowiedzieć się więcej i angażowanie, zapoznaj się [fsharp.org](http://fsharp.org). Bezpłatnie do przyłączenia i deweloperów F # w podstawę sieci jest coś, których nie chcesz, aby pominąć w serwisie!
