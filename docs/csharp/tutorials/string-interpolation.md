---
title: "Ciąg interpolacji - C#"
description: "Dowiedz się, jak działa interpolacji ciągu w języku C# 6"
keywords: .NET, .NET Core, C#, string
author: mgroves
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8806f6b-3ac7-4ee6-9b3e-c524d5301ae9
ms.openlocfilehash: db062ed2f832ae933941da1c49e84303090f4390
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="string-interpolation-in-c"></a><span data-ttu-id="e6c8d-104">Ciąg interpolacji w języku C#</span><span class="sxs-lookup"><span data-stu-id="e6c8d-104">String Interpolation in C#</span></span> #

<span data-ttu-id="e6c8d-105">Ciąg interpolacji jest sposób symbole zastępcze w ciągu zastępuje wartość zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-105">String Interpolation is the way that placeholders in a string are replaced by the value of a string variable.</span></span> <span data-ttu-id="e6c8d-106">Przed C# 6, jest sposób, w tym celu <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-106">Before C# 6, the way to do this is with <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e6c8d-107">To działanie jest zgoda, ale ponieważ używa numeru symbole zastępcze, może być trudniejsze do odczytu i pełniejsze.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-107">This works okay, but since it uses numbered placeholders, it can be harder to read and more verbose.</span></span>

<span data-ttu-id="e6c8d-108">Inne języki programowania miały interpolacji ciąg wbudowanych w języku jakiś czas.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-108">Other programming languages have had string interpolation built into the language for a while.</span></span> <span data-ttu-id="e6c8d-109">Na przykład w kodzie PHP:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-109">For instance, in PHP:</span></span>

```php
$name = "Jonas";
echo "My name is $name.";
// This will output "My name is Jonas."
```

<span data-ttu-id="e6c8d-110">W języku C# 6 koniec zostały tego stylu interpolacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-110">In C# 6, we finally have that style of string interpolation.</span></span> <span data-ttu-id="e6c8d-111">Można użyć `$` przed ciąg, aby wskazać, że należy zastąpić zmienne/wyrażenia ich wartości.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-111">You can use a `$` before a string to indicate that it should substitute variables/expressions for their values.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6c8d-112">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="e6c8d-112">Prerequisites</span></span>
<span data-ttu-id="e6c8d-113">Należy skonfigurować komputer z usługami .NET core.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-113">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="e6c8d-114">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-114">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="e6c8d-115">Można uruchomić tej aplikacji, w systemie Windows, Ubuntu Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-115">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="e6c8d-116">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-116">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="e6c8d-117">Opisy poniżej użyj [Visual Studio Code](https://code.visualstudio.com/) czyli typu open source cross platform edytora.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-117">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="e6c8d-118">Można jednak użyć dowolnego narzędzia potrafisz.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-118">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="e6c8d-119">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e6c8d-119">Create the Application</span></span>

<span data-ttu-id="e6c8d-120">Teraz, po zainstalowaniu wszystkich narzędzi, należy utworzyć nową aplikację platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-120">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="e6c8d-121">Aby użyć generatora wiersza polecenia, Utwórz katalog projektu, takie jak `interpolated`i uruchom następujące polecenie w ulubionych powłoki:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-121">To use the command line generator, create a directory for your project, such as `interpolated`, and execute the following command in your favorite shell:</span></span>

```
dotnet new console
```

<span data-ttu-id="e6c8d-122">To polecenie tworzy projekt .NET Core podstawowe z pliku projektu *interpolated.csproj*i pliku kodu źródłowego, *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-122">This command creates a barebones .NET Core project with a project file, *interpolated.csproj*, and a source code file, *Program.cs*.</span></span> <span data-ttu-id="e6c8d-123">Konieczne będzie wykonanie `dotnet restore` do przywrócenia zależności niezbędne do skompilowania tego projektu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-123">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="e6c8d-124">Do wykonania programu, należy użyć `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-124">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="e6c8d-125">Powinien zostać wyświetlony "tekst Hello, World" dane wyjściowe do konsoli.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-125">You should see "Hello, World" output to the console.</span></span>



## <a name="intro-to-string-interpolation"></a><span data-ttu-id="e6c8d-126">Wprowadzenie do ciągu interpolacji</span><span class="sxs-lookup"><span data-stu-id="e6c8d-126">Intro to String Interpolation</span></span>

<span data-ttu-id="e6c8d-127">Z <xref:System.String.Format%2A?displayProperty=nameWithType>, określ "symbole zastępcze" w ciągu, który zastępuje argumentów po ciągu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-127">With <xref:System.String.Format%2A?displayProperty=nameWithType>, you specify "placeholders" in a string that are replaced by the arguments following the string.</span></span> <span data-ttu-id="e6c8d-128">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-128">For instance:</span></span>

[!code-csharp[String.Format example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#StringFormatExample)]  

<span data-ttu-id="e6c8d-129">Który dane wyjściowe obejmują "mojej nazwy jest gajów Matt".</span><span class="sxs-lookup"><span data-stu-id="e6c8d-129">That will output "My name is Matt Groves".</span></span>

<span data-ttu-id="e6c8d-130">W języku C# 6, zamiast `String.Format`, zdefiniuj ciągu interpolowanym dołączając ją z `$` symboli, a następnie za pomocą zmiennych bezpośrednio w ciągu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-130">In C# 6, instead of using `String.Format`, you define an interpolated string by prepending it with the `$` symbol, and then using the variables directly in the string.</span></span> <span data-ttu-id="e6c8d-131">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-131">For instance:</span></span>

[!code-csharp[Interpolation example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExample)]  

<span data-ttu-id="e6c8d-132">Nie trzeba używać tylko zmienne.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-132">You don't have to use just variables.</span></span> <span data-ttu-id="e6c8d-133">Można użyć dowolnego wyrażenia w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-133">You can use any expression within the brackets.</span></span> <span data-ttu-id="e6c8d-134">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-134">For instance:</span></span>

[!code-csharp[Interpolation expression example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationExpressionExample)]  

<span data-ttu-id="e6c8d-135">Czy wyjściowy, który:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-135">Which would output:</span></span>

```
This is line number 1
This is line number 2
This is line number 3
This is line number 4
This is line number 5
```

## <a name="how-string-interpolation-works"></a><span data-ttu-id="e6c8d-136">Jak działa interpolacji ciągu</span><span class="sxs-lookup"><span data-stu-id="e6c8d-136">How string interpolation works</span></span>

<span data-ttu-id="e6c8d-137">W tle przetłumaczyć tej składni interpolacji ciąg `String.Format` przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-137">Behind the scenes, this string interpolation syntax is translated into `String.Format` by the compiler.</span></span> <span data-ttu-id="e6c8d-138">Tak, możesz zrobić [tego samego typu rzeczy wykonaniu przed z `String.Format` ](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e6c8d-138">So, you can do the [same type of stuff you've done before with `String.Format`](../../standard/base-types/formatting-types.md).</span></span>

<span data-ttu-id="e6c8d-139">Na przykład można dodać uzupełniania i formatowania liczbowa:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-139">For instance, you can add padding and numeric formatting:</span></span>

[!code-csharp[Interpolation formatting example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationFormattingExample)]  

<span data-ttu-id="e6c8d-140">Powyższe czy dane wyjściowe wyglądać mniej więcej tak:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-140">The above would output something like:</span></span>

```
998        5,177.67
999        6,719.30
1000       9,910.61
1001       529.34
1002       1,349.86
1003       2,660.82
1004       6,227.77
```

<span data-ttu-id="e6c8d-141">Jeśli nazwa zmiennej nie zostanie znaleziony, generowany jest błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-141">If a variable name is not found, then a compile-time error is generated.</span></span>

<span data-ttu-id="e6c8d-142">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-142">For instance:</span></span>

```csharp
var animal = "fox";
var localizeMe = $"The {adj} brown {animal} jumped over the lazy {otheranimal}";
var adj = "quick";
Console.WriteLine(localizeMe);
```

<span data-ttu-id="e6c8d-143">Jeśli kompilacja to występują błędy:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-143">If you compile this, you get errors:</span></span>
 
* <span data-ttu-id="e6c8d-144">`Cannot use local variable 'adj' before it is declared` - `adj` nie została zadeklarowana zmienna, do *po* ciągu interpolowanym.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-144">`Cannot use local variable 'adj' before it is declared` - the `adj` variable wasn't declared until *after* the interpolated string.</span></span>
* <span data-ttu-id="e6c8d-145">`The name 'otheranimal' does not exist in the current context` -zmiennej o nazwie `otheranimal` nawet nigdy nie został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-145">`The name 'otheranimal' does not exist in the current context` - a variable called `otheranimal` was never even declared</span></span>

## <a name="localization-and-internationalization"></a><span data-ttu-id="e6c8d-146">Lokalizacja i internacjonalizacji</span><span class="sxs-lookup"><span data-stu-id="e6c8d-146">Localization and Internationalization</span></span>

<span data-ttu-id="e6c8d-147">Obsługuje ciągu interpolowanym <xref:System.IFormattable?displayProperty=nameWithType> i <xref:System.FormattableString?displayProperty=nameWithType>, które mogą być przydatne w przypadku internacjonalizacji.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-147">An interpolated string supports <xref:System.IFormattable?displayProperty=nameWithType> and <xref:System.FormattableString?displayProperty=nameWithType>, which can be useful for internationalization.</span></span>

<span data-ttu-id="e6c8d-148">Domyślnie w ciągu interpolowanym używa bieżącej kultury.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-148">By default, an interpolated string uses the current culture.</span></span> <span data-ttu-id="e6c8d-149">Aby korzystać z inną kulturę, rzutowania w ciągu interpolowanym jako `IFormattable`.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-149">To use a different culture, cast an interpolated string as `IFormattable`.</span></span> <span data-ttu-id="e6c8d-150">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e6c8d-150">For instance:</span></span>

[!code-csharp[Interpolation internationalization example](../../../samples/snippets/csharp/new-in-6/string-interpolation.cs#InterpolationInternationalizationExample)]  

## <a name="conclusion"></a><span data-ttu-id="e6c8d-151">Wniosek</span><span class="sxs-lookup"><span data-stu-id="e6c8d-151">Conclusion</span></span> 

<span data-ttu-id="e6c8d-152">W tym samouczku przedstawiono sposób korzystania z funkcji interpolacji ciągu języka C# 6.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-152">In this tutorial, you learned how to use string interpolation features of C# 6.</span></span> <span data-ttu-id="e6c8d-153">Zasadniczo jest bardziej zwięzły sposób zapisywania prosty `String.Format` instrukcji z niektórych zastrzeżenia do bardziej zaawansowanych zastosowań.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-153">It's basically a more concise way of writing simple `String.Format` statements, with some caveats for more advanced uses.</span></span> <span data-ttu-id="e6c8d-154">Aby uzyskać więcej informacji, zobacz [ciągi interpolowane](../../csharp//language-reference/keywords/interpolated-strings.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="e6c8d-154">For more information, see the [Interpolated Strings](../../csharp//language-reference/keywords/interpolated-strings.md) topic.</span></span>
