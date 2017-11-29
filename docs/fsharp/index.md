---
title: 'Przewodnik F #'
description: "Więcej informacji na temat języka F # programowania, języka open source dla platformy .NET, która zapewnia najwyższej jakości pomoc techniczną programowanie funkcjonalne."
keywords: .NET, .NET core
author: jackfoxy
ms.author: phcart
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: 4ddd77cef6cf70a63f1af81359d82eda27a01593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="f-guide"></a><span data-ttu-id="93b8c-104">Przewodnik F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-104">F# Guide</span></span>

<span data-ttu-id="93b8c-105">F # i platform typu open source język programowania dla platformy .NET, co zapewnia najwyższej jakości pomoc techniczną dla programowanie funkcjonalne, wraz z możliwością programowanie zorientowane obiektowo i konieczne jest.</span><span class="sxs-lookup"><span data-stu-id="93b8c-105">F# is a cross-platform, open source programming language for .NET which provides first-class support for functional programming, along with support of object-oriented and imperative programming.</span></span>  <span data-ttu-id="93b8c-106">Kompilator Visual F # i narzędzi są implementacji i narzędzi języka F # język programowania, przez co F # członkiem najwyższej jakości .NET firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="93b8c-106">The Visual F# compiler and tooling are Microsoft's implementation and tooling for the F# programming language, making F# a first-class member of .NET.</span></span>

## <a name="if-youre-new-to-f"></a><span data-ttu-id="93b8c-107">Jeśli jesteś nowym użytkownikiem F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-107">If You're New to F#</span></span> #

<span data-ttu-id="93b8c-108">Jeśli jesteś nowym użytkownikiem F #, rozpoczynać się od [samouczek programu F #](tour.md) , aby uzyskać przegląd języka.</span><span class="sxs-lookup"><span data-stu-id="93b8c-108">If you're new to F#, begin with the [Tour of F#](tour.md) to get an overview of the language.</span></span>

<span data-ttu-id="93b8c-109">Zalecane jest również, czy można przejść przez [działa jako wartości pierwszej klasy](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> informacji funkcjonalności programowania pojęcia, które są niezbędne do pracy z F #.</span><span class="sxs-lookup"><span data-stu-id="93b8c-109">It's also recommended that you go through the [Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Progamming](introduction-to-functional-programming/index.md)--> to learn Functional Programming concepts which are essential to working with F#.</span></span>

<span data-ttu-id="93b8c-110">[Samouczki](tutorials/getting-started/index.md) mają także przewodniki krok po kroku dla różnych poziomów umiejętności i funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="93b8c-110">The [Tutorials](tutorials/getting-started/index.md) also have step-by-step guides for various skill levels and features of the language.</span></span>

## <a name="if-youre-experienced-with-f"></a><span data-ttu-id="93b8c-111">Jeśli masz doświadczenie w języku F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-111">If You're Experienced with F#</span></span> #

<span data-ttu-id="93b8c-112">Jeśli znasz nawigację F # można znaleźć wykorzystywany w [materiały referencyjne dotyczące języka](language-reference/index.md), który dokumentów każdego aspektu języka dokładnie, uzupełnione o wiele przykładów kodu.</span><span class="sxs-lookup"><span data-stu-id="93b8c-112">If you know your way around F#, you'll find a lot of use in the [Language Reference](language-reference/index.md), which documents each aspect of the language thoroughly, supplemented by numerous code samples.</span></span>  <span data-ttu-id="93b8c-113">Można również znaleźć wykorzystywany w [F # odwołanie do biblioteki podstawowej](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span><span class="sxs-lookup"><span data-stu-id="93b8c-113">You'll also find a lot of use in the [F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference).</span></span>  <span data-ttu-id="93b8c-114">Dokumentacja biblioteki podstawowej F # po pewnym czasie zostanie przesunięty w kierunku od MSDN i do tych dokumentów bieżącego.</span><span class="sxs-lookup"><span data-stu-id="93b8c-114">The F# Core Library Reference will eventually move away from MSDN and into these current docs.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="93b8c-115">Foundation oprogramowania F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-115">The F# Software Foundation</span></span>

<span data-ttu-id="93b8c-116">Mimo że Microsoft głównej deweloperów języka F # i Visual F # narzędzi, F # nie jest również obsługiwana przez niezależnych foundation, F # oprogramowania Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="93b8c-116">Although Microsoft is the primary developer of the F# language and Visual F# Tooling, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="93b8c-117">Misji Foundation oprogramowania F # jest podwyższyć poziom, ochronę i poprawić język programowania, F # i obsługuje i ułatwić rozwój różnych i międzynarodową społeczność programistów F #.</span><span class="sxs-lookup"><span data-stu-id="93b8c-117">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="93b8c-118">Aby dowiedzieć się więcej i angażowanie, zapoznaj się [fsharp.org](http://fsharp.org).</span><span class="sxs-lookup"><span data-stu-id="93b8c-118">To learn more and get involved, check out [fsharp.org](http://fsharp.org).</span></span>

## <a name="documentation"></a><span data-ttu-id="93b8c-119">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="93b8c-119">Documentation</span></span>

* [<span data-ttu-id="93b8c-120">Samouczki</span><span class="sxs-lookup"><span data-stu-id="93b8c-120">Tutorials</span></span>](tutorials/getting-started/index.md)
* <span data-ttu-id="93b8c-121">[Funkcje jako wartości pierwszej klasy](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span><span class="sxs-lookup"><span data-stu-id="93b8c-121">[Functions as First-Class Values](introduction-to-functional-programming/functions-as-first-class-values.md)<!--[Introduction to Functional Programming](introduction-to-functional-programming/index.md)--></span></span>
* [<span data-ttu-id="93b8c-122">Odwołanie językowe</span><span class="sxs-lookup"><span data-stu-id="93b8c-122">Language Reference</span></span>](language-reference/index.md)
* [<span data-ttu-id="93b8c-123">Odwołanie do biblioteki podstawowej F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-123">F# Core Library Reference</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference)

## <a name="online-reading-resources"></a><span data-ttu-id="93b8c-124">Online odczytu zasobów</span><span class="sxs-lookup"><span data-stu-id="93b8c-124">Online Reading Resources</span></span>

* [<span data-ttu-id="93b8c-125">F # dla zabawy i Gitbook zysku</span><span class="sxs-lookup"><span data-stu-id="93b8c-125">F# for Fun and Profit Gitbook</span></span>](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) 
* [<span data-ttu-id="93b8c-126">Wikibook programowania w języku F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-126">F# Programming Wikibook</span></span>](https://en.wikibooks.org/wiki/F_Sharp_Programming)

## <a name="video-learning-resources"></a><span data-ttu-id="93b8c-127">Materiałów szkoleniowych wideo</span><span class="sxs-lookup"><span data-stu-id="93b8c-127">Video Learning Resources</span></span>

* [<span data-ttu-id="93b8c-128">Wprowadzenie do programowania w języku F # serii na YouTube</span><span class="sxs-lookup"><span data-stu-id="93b8c-128">Introduction to Programming with F# series on YouTube</span></span>](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC)
* [<span data-ttu-id="93b8c-129">Wprowadzenie do serii F # na FSharpTV</span><span class="sxs-lookup"><span data-stu-id="93b8c-129">Introduction to F# series on FSharpTV</span></span>](https://fsharp.tv/courses/fsharp-programming-intro/)

## <a name="further-resources"></a><span data-ttu-id="93b8c-130">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="93b8c-130">Further Resources</span></span>

* [<span data-ttu-id="93b8c-131">Materiałów szkoleniowych w fsharp.org F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-131">F# Learning Resources on fsharp.org</span></span>](http://fsharp.org/learn.html)
* [<span data-ttu-id="93b8c-132">Witryny sieci Web wstawki kodu programu F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-132">F# Snippets Website</span></span>](http://www.fssnip.net)
* [<span data-ttu-id="93b8c-133">Foundation oprogramowania F #</span><span class="sxs-lookup"><span data-stu-id="93b8c-133">F# Software Foundation</span></span>](http://fsharp.org)
