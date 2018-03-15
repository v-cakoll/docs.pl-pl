---
title: "Podręcznik języka F#"
description: "Ten przewodnik zawiera przegląd różnych materiałów szkoleniowych w F #, funkcjonalny język programowania, który działa na platformie .NET."
author: jackfoxy
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: b7cf3feb5699f85bf09a47f008fdaf70ac7c8d77
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2018
---
# <a name="f-guide"></a><span data-ttu-id="cf09a-103">Podręcznik języka F#</span><span class="sxs-lookup"><span data-stu-id="cf09a-103">F# Guide</span></span>

<span data-ttu-id="cf09a-104">F # jest funkcjonalny język programowania, który działa na platformie .NET.</span><span class="sxs-lookup"><span data-stu-id="cf09a-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="cf09a-105">Ponadto wprowadzono pełną obsługę dla obiektów, umożliwiając mieszanego funkcjonalności i programowania obiektu pragmatyczne rozwiązania wszelkich problemów.</span><span class="sxs-lookup"><span data-stu-id="cf09a-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    args                     // Use F# pipe operators to send the args into some functions.
    |> Array.map getGreeting // Turn each name into a friendly greeting.
    |> Array.iter printfn    // Print them!

    0
```

<span data-ttu-id="cf09a-106">F # jest o wydajność Centrum.</span><span class="sxs-lookup"><span data-stu-id="cf09a-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="cf09a-107">Powszechna i pełne zaawansowanych funkcji jest obsługa narzędzi F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="cf09a-108">Learning F #</span><span class="sxs-lookup"><span data-stu-id="cf09a-108">Learning F#</span></span> #

<span data-ttu-id="cf09a-109">[Samouczek języka F #](tour.md) zawiera omówienie funkcji języka główne z dużą ilością przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="cf09a-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="cf09a-110">Jest to zalecane, jeśli dopiero zaczynasz korzystać z języka F # i chcesz uzyskać pewne pojęcie zasady działania języka.</span><span class="sxs-lookup"><span data-stu-id="cf09a-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="cf09a-111">[Rozpoczynanie pracy z F # w programie Visual Studio](get-started/get-started-visual-studio.md) Jeśli komputer znajduje się w systemie Windows i chcesz pełne środowisko programu Visual Studio IDE (Integraded Development Environment).</span><span class="sxs-lookup"><span data-stu-id="cf09a-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="cf09a-112">[Rozpoczynanie pracy z F # w programie Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) Jeśli teraz macOS i chcesz użyć programu Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="cf09a-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="cf09a-113">[Rozpoczynanie pracy z F # w programie Visual Studio Code](get-started/get-started-vscode.md) Jeśli chcesz lekkie, obsługujący wiele platform i środowisko IDE z zaawansowanymi funkcjami.</span><span class="sxs-lookup"><span data-stu-id="cf09a-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="cf09a-114">[Rozpoczynanie pracy z F # z poziomu interfejsu wiersza polecenia platformy .NET Core](get-started/get-started-command-line.md) Jeśli chcesz użyć narzędzia wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf09a-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

## <a name="references"></a><span data-ttu-id="cf09a-115">Odwołania</span><span class="sxs-lookup"><span data-stu-id="cf09a-115">References</span></span>

<span data-ttu-id="cf09a-116">[Dokumentacja języka F #](language-reference/index.md) jest odwołaniem urzędnika, kompleksowe dla wszystkich funkcji języka F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-116">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="cf09a-117">Każdego artykułu opisano składnię i zawiera przykłady kodu.</span><span class="sxs-lookup"><span data-stu-id="cf09a-117">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="cf09a-118">Pasek filtru w spisie treści umożliwia powinny być określone.</span><span class="sxs-lookup"><span data-stu-id="cf09a-118">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="cf09a-119">[Dokumentacja biblioteki podstawowej F #](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) jest odwołanie do interfejsu API biblioteki podstawowej F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-119">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>

## <a name="additional-guides"></a><span data-ttu-id="cf09a-120">Dodatkowe przewodniki</span><span class="sxs-lookup"><span data-stu-id="cf09a-120">Additional guides</span></span>

<span data-ttu-id="cf09a-121">[F # dla zabawy i zysku](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) kompleksowe i bardzo szczegółowe książki na uczenia F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-121">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="cf09a-122">Jego zawartość i autora są ukochanego przez społeczność F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-122">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="cf09a-123">Odbiorcy docelowi jest głównie deweloperom obiektowej tła programowania.</span><span class="sxs-lookup"><span data-stu-id="cf09a-123">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="cf09a-124">[F # programowania Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) jest wikibook o uczenia F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-124">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="cf09a-125">Istnieje również produktu społeczności F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-125">It is also a product of the F# community.</span></span> <span data-ttu-id="cf09a-126">Odbiorcy docelowi jest osoby, które są nowe w F #, z niewielki obiektowej programowania tła.</span><span class="sxs-lookup"><span data-stu-id="cf09a-126">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="cf09a-127">Informacje F # za pomocą wideo</span><span class="sxs-lookup"><span data-stu-id="cf09a-127">Learn F# through videos</span></span>

<span data-ttu-id="cf09a-128">[Samouczek języka F # na działanie serwisu YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) jest doskonałym wprowadzenie do F # za pomocą programu Visual Studio, przedstawiający partii dużą przykłady w trakcie 1,5 godziny.</span><span class="sxs-lookup"><span data-stu-id="cf09a-128">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="cf09a-129">Odbiorcy docelowi jest deweloperów programu Visual Studio, nowi F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-129">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="cf09a-130">[Wprowadzenie do programowania w języku F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) jest doskonałym wideo serii, która korzysta z programu Visual Studio Code edytorem głównego.</span><span class="sxs-lookup"><span data-stu-id="cf09a-130">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="cf09a-131">Seria filmów zaczyna się od nothing i kończy się tworzenie gry wideo RPG tekstowy.</span><span class="sxs-lookup"><span data-stu-id="cf09a-131">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="cf09a-132">Odbiorcy docelowi jest deweloperów, którzy preferowane Visual Studio Code (lub lekkie IDE) i dopiero zaczynasz korzystać z języka F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-132">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="cf09a-133">[What's New in Visual Studio 2017 dla F # dla programistów](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) jest kursu wideo, który zawiera niektóre nowsze funkcje w F # w programie Visual Studio 2017 r.</span><span class="sxs-lookup"><span data-stu-id="cf09a-133">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="cf09a-134">Odbiorcy docelowi jest deweloperów programu Visual Studio, nowi F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-134">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="cf09a-135">Inne przydatne zasoby</span><span class="sxs-lookup"><span data-stu-id="cf09a-135">Other useful resources</span></span>

<span data-ttu-id="cf09a-136">[Witryny sieci Web wstawki kodu programu F #](http://www.fssnip.net) zawiera zestaw ogromną przedstawiający sposób wykonywania wszystko, co w języku F #, od bezwzględny dla początkujących użytkowników do bardzo zaawansowane wstawki fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="cf09a-136">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="cf09a-137">[Slack Foundation oprogramowania F #](http://fsharp.org/guides/slack/) jest doskonałym miejscem dla początkujących i ekspertów podobne, jest bardzo aktywny, a niektóre na świecie najlepsze F # programistów dla Czat.</span><span class="sxs-lookup"><span data-stu-id="cf09a-137">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="cf09a-138">Zdecydowanie zaleca się dołączenie.</span><span class="sxs-lookup"><span data-stu-id="cf09a-138">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="cf09a-139">Foundation oprogramowania F #</span><span class="sxs-lookup"><span data-stu-id="cf09a-139">The F# Software Foundation</span></span>

<span data-ttu-id="cf09a-140">Mimo że Microsoft głównej deweloperów języka F # i jej narzędzi w programie Visual Studio, F # nie jest również obsługiwana przez niezależnych foundation, F # oprogramowania Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="cf09a-140">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="cf09a-141">Misji Foundation oprogramowania F # jest podwyższyć poziom, ochronę i poprawić język programowania, F # i obsługuje i ułatwić rozwój różnych i międzynarodową społeczność programistów F #.</span><span class="sxs-lookup"><span data-stu-id="cf09a-141">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="cf09a-142">Aby dowiedzieć się więcej i angażowanie, zapoznaj się [fsharp.org](http://fsharp.org). Bezpłatnie do przyłączenia i deweloperów F # w podstawę sieci jest coś, których nie chcesz, aby pominąć w serwisie!</span><span class="sxs-lookup"><span data-stu-id="cf09a-142">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>