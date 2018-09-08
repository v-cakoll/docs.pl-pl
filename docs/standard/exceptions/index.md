---
title: Obsługa i zgłaszanie wyjątków na platformie .NET
ms.date: 06/19/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions [.NET], handling
- runtime, exceptions
- filtering exceptions
- errors [.NET], exceptions
- exceptions [.NET], throwing
- exceptions [.NET]
- common language runtime, exceptions
ms.assetid: f99a1d29-a2a8-47af-9707-9909f9010735
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 263e6394a57ec3e7ef00eb79671d9b8ac47e724f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44177238"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="5e774-102">Obsługa i zgłaszanie wyjątków na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="5e774-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="5e774-103">Aplikacje muszą mieć możliwość obsługi błędów występujących podczas wykonywania w spójny sposób.</span><span class="sxs-lookup"><span data-stu-id="5e774-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="5e774-104">.NET udostępnia model dotyczące powiadamiania aplikacji o błędach w jednolity sposób: operacje .NET wskazać błąd przez zgłaszanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e774-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="5e774-105">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="5e774-105">Exceptions</span></span>

<span data-ttu-id="5e774-106">Wyjątek to każdy warunek błędu i nieoczekiwane zachowanie, które zostanie osiągnięty, wykonywania programu.</span><span class="sxs-lookup"><span data-stu-id="5e774-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="5e774-107">Wyjątki mogą zostać wygenerowane z powodu błędów w kodzie lub kod, który można wywoływać (np. biblioteki udostępnionej), zasobów niedostępny systemu operacyjnego, nieoczekiwane warunki, które środowisko uruchomieniowe napotka (na przykład kod, którego nie można zweryfikować) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="5e774-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="5e774-108">Aplikację można odzyskać z niektórych z tych warunków, ale nie od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="5e774-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="5e774-109">Mimo że można odzyskać z większości aplikacji wyjątki, nie można odzyskać z większości wyjątki środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="5e774-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="5e774-110">Na platformie .NET, wyjątek jest obiektem, który dziedziczy z <xref:System.Exception?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="5e774-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="5e774-111">Wyjątek jest generowany przy użyciu obszaru kodu, w którym wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="5e774-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="5e774-112">Wyjątek jest przekazywany w górę stosu, dopóki aplikacja obsługuje ją lub program zakończy.</span><span class="sxs-lookup"><span data-stu-id="5e774-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="5e774-113">Wyjątki a tradycyjnych metod obsługi błędów</span><span class="sxs-lookup"><span data-stu-id="5e774-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="5e774-114">Tradycyjnie modelu obsługi błędów języka skorzystała w unikatowy sposób wykrywania błędów i lokalizowania programy obsługi dla nich zarówno w języku lub na mechanizmu obsługi błędów, dostarczone przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5e774-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="5e774-115">Sposób .NET implementuje obsługę wyjątków zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="5e774-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="5e774-116">Wyjątek zostanie zgłoszony i obsługa działa tak samo, dla języków programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="5e774-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="5e774-117">Nie wymaga żadnych składni konkretnego języka dla obsługi wyjątków, ale pozwala zdefiniować własną składnię dla każdego języka.</span><span class="sxs-lookup"><span data-stu-id="5e774-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="5e774-118">Wyjątki mogą zostać wygenerowane w procesie i nawet granic.</span><span class="sxs-lookup"><span data-stu-id="5e774-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="5e774-119">Kod obsługi wyjątków, można dodać do aplikacji w celu zwiększenia niezawodności programu.</span><span class="sxs-lookup"><span data-stu-id="5e774-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="5e774-120">Wyjątki oferują przewagę nad innymi metodami powiadomienia o błędzie, takich jak kody powrotne.</span><span class="sxs-lookup"><span data-stu-id="5e774-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="5e774-121">Błędy nie niezauważone, ponieważ jeśli wyjątek jest generowany i nie można go obsłużyć, środowisko uruchomieniowe kończy działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e774-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="5e774-122">Nieprawidłowe wartości nie w dalszym ciągu propagować przez system w wyniku kod, który zakończy się niepowodzeniem, aby sprawdzić, czy zwracany kod błędu.</span><span class="sxs-lookup"><span data-stu-id="5e774-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="5e774-123">Typowe wyjątki</span><span class="sxs-lookup"><span data-stu-id="5e774-123">Common exceptions</span></span>

<span data-ttu-id="5e774-124">W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami co mogą być ich przyczyną.</span><span class="sxs-lookup"><span data-stu-id="5e774-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="5e774-125">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="5e774-125">Exception type</span></span> | <span data-ttu-id="5e774-126">Opis</span><span class="sxs-lookup"><span data-stu-id="5e774-126">Description</span></span> | <span data-ttu-id="5e774-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e774-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="5e774-128">Klasa bazowa dla wszystkich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e774-128">Base class for all exceptions.</span></span> | <span data-ttu-id="5e774-129">Brak (Użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="5e774-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="5e774-130">Element zgłaszany przez środowisko uruchomieniowe, tylko wtedy, gdy tablica jest indeksowana nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="5e774-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="5e774-131">Indeksowanie tablicy poza prawidłowym zakresem:</span><span class="sxs-lookup"><span data-stu-id="5e774-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="5e774-132">Element zgłaszany przez środowisko uruchomieniowe, tylko wtedy, gdy odwołuje się do obiektu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="5e774-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="5e774-133">Zgłoszony przez metody, gdy jest w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="5e774-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="5e774-134">Wywoływanie `Enumerator.MoveNext()` po usunięciu elementu z kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="5e774-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="5e774-135">Klasa bazowa dla wszystkich wyjątków argumentów.</span><span class="sxs-lookup"><span data-stu-id="5e774-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="5e774-136">Brak (Użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="5e774-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="5e774-137">Zgłoszony przez metody, które nie zezwalają na argument mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="5e774-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="5e774-138">Zgłoszony przez metody, które Sprawdź, czy argumenty są w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="5e774-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="5e774-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e774-139">See also</span></span>

- [<span data-ttu-id="5e774-140">Właściwości i klasy wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e774-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)  
- [<span data-ttu-id="5e774-141">Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e774-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)  
- [<span data-ttu-id="5e774-142">Instrukcje: Używanie określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="5e774-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)  
- [<span data-ttu-id="5e774-143">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e774-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)  
- [<span data-ttu-id="5e774-144">Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e774-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)  
- [<span data-ttu-id="5e774-145">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="5e774-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)  
- [<span data-ttu-id="5e774-146">Instrukcje: Używanie bloków finally</span><span class="sxs-lookup"><span data-stu-id="5e774-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)  
- [<span data-ttu-id="5e774-147">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="5e774-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)  
- [<span data-ttu-id="5e774-148">Najlepsze rozwiązania dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="5e774-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)  
- <span data-ttu-id="5e774-149">[Co Dev co trzeba wiedzieć o wyjątków w środowisku uruchomieniowym](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="5e774-149">[What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md).</span></span>
