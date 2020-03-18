---
title: Obsługa i zgłaszanie wyjątków w .NET
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
ms.openlocfilehash: 8e78b2a8d7a815637e143eeb88bcfb51ded33771
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75741353"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="0974a-102">Obsługa i zgłaszanie wyjątków w .NET</span><span class="sxs-lookup"><span data-stu-id="0974a-102">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="0974a-103">Aplikacje muszą być w stanie obsługiwać błędy, które występują podczas wykonywania w sposób spójny.</span><span class="sxs-lookup"><span data-stu-id="0974a-103">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="0974a-104">.NET udostępnia model powiadamiania aplikacji o błędach w jednolity sposób: operacje .NET wskazują na błąd, zgłaszając wyjątki.</span><span class="sxs-lookup"><span data-stu-id="0974a-104">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="0974a-105">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="0974a-105">Exceptions</span></span>

<span data-ttu-id="0974a-106">Wyjątkiem jest dowolny warunek błędu lub nieoczekiwane zachowanie napotkane przez program wykonujący.</span><span class="sxs-lookup"><span data-stu-id="0974a-106">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="0974a-107">Wyjątki mogą być generowane z powodu błędu w kodzie lub w kodzie, który wywołasz (na przykład biblioteki udostępnionej), niedostępnych zasobów systemu operacyjnego, nieoczekiwanych warunków, które napotka czas uruchomieniowy (takich jak kod, który nie może być zweryfikowany) i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0974a-107">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="0974a-108">Aplikacja może odzyskać z niektórych z tych warunków, ale nie od innych.</span><span class="sxs-lookup"><span data-stu-id="0974a-108">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="0974a-109">Mimo że można odzyskać z większości wyjątków aplikacji, nie można odzyskać z większości wyjątków czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0974a-109">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="0974a-110">W .NET wyjątek jest obiektem, który <xref:System.Exception?displayProperty=nameWithType> dziedziczy z klasy.</span><span class="sxs-lookup"><span data-stu-id="0974a-110">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="0974a-111">Wyjątek jest zgłaszany z obszaru kodu, w którym wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="0974a-111">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="0974a-112">Wyjątek jest przekazywany w górę stosu, dopóki aplikacja obsługuje go lub program kończy.</span><span class="sxs-lookup"><span data-stu-id="0974a-112">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="0974a-113">Wyjątki a tradycyjne metody obsługi błędów</span><span class="sxs-lookup"><span data-stu-id="0974a-113">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="0974a-114">Tradycyjnie model obsługi błędów języka opierał się na unikatowym sposobie wykrywania błędów i lokalizowaniu dla nich obsługi języka lub na mechanizmie obsługi błędów zapewnianym przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="0974a-114">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="0974a-115">Sposób, w jaki platforma .NET implementuje obsługę wyjątków, zapewnia następujące zalety:</span><span class="sxs-lookup"><span data-stu-id="0974a-115">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="0974a-116">Zgłaszanie wyjątków i obsługa działa tak samo dla języków programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="0974a-116">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="0974a-117">Nie wymaga żadnej składni określonego języka do obsługi wyjątków, ale umożliwia każdemu językowi zdefiniowanie własnej składni.</span><span class="sxs-lookup"><span data-stu-id="0974a-117">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="0974a-118">Wyjątki mogą być generowane przez proces, a nawet granice maszyny.</span><span class="sxs-lookup"><span data-stu-id="0974a-118">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="0974a-119">Kod obsługi wyjątków można dodać do aplikacji, aby zwiększyć niezawodność programu.</span><span class="sxs-lookup"><span data-stu-id="0974a-119">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="0974a-120">Wyjątki oferują zalety w stosunku do innych metod powiadamiania o błędach, takich jak kody zwrotne.</span><span class="sxs-lookup"><span data-stu-id="0974a-120">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="0974a-121">Błędy nie pozostają niezauważone, ponieważ jeśli wyjątek zostanie zgłoszony i nie obsługujesz go, czas wykonywania kończy działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0974a-121">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="0974a-122">Nieprawidłowe wartości nie są nadal propagowane przez system w wyniku kodu, który nie może sprawdzić, czy kod zwrotny nie jest wynikiem błędu.</span><span class="sxs-lookup"><span data-stu-id="0974a-122">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="0974a-123">Typowe wyjątki</span><span class="sxs-lookup"><span data-stu-id="0974a-123">Common exceptions</span></span>

<span data-ttu-id="0974a-124">W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami, co może je powodować.</span><span class="sxs-lookup"><span data-stu-id="0974a-124">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="0974a-125">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="0974a-125">Exception type</span></span> | <span data-ttu-id="0974a-126">Opis</span><span class="sxs-lookup"><span data-stu-id="0974a-126">Description</span></span> | <span data-ttu-id="0974a-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="0974a-127">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="0974a-128">Klasa podstawowa dla wszystkich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="0974a-128">Base class for all exceptions.</span></span> | <span data-ttu-id="0974a-129">Brak (użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="0974a-129">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="0974a-130">Generowane przez czas wykonywania tylko wtedy, gdy tablica jest indeksowana nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0974a-130">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="0974a-131">Indeksowanie tablicy poza jej prawidłowym zakresem:</span><span class="sxs-lookup"><span data-stu-id="0974a-131">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="0974a-132">Generowane przez czas wykonywania tylko wtedy, gdy odwołuje się do obiektu null.</span><span class="sxs-lookup"><span data-stu-id="0974a-132">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="0974a-133">Generowane przez metody, gdy w stanie nieprawidłowym.</span><span class="sxs-lookup"><span data-stu-id="0974a-133">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="0974a-134">Wywołanie `Enumerator.MoveNext()` po usunięciu elementu z podstawowej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0974a-134">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="0974a-135">Klasa podstawowa dla wszystkich wyjątków argumentów.</span><span class="sxs-lookup"><span data-stu-id="0974a-135">Base class for all argument exceptions.</span></span> | <span data-ttu-id="0974a-136">Brak (użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="0974a-136">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="0974a-137">Generowane przez metody, które nie zezwalają na argument ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="0974a-137">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="0974a-138">Generowane przez metody, które sprawdzają, czy argumenty znajdują się w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="0974a-138">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="0974a-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0974a-139">See also</span></span>

- [<span data-ttu-id="0974a-140">Właściwości i klasy wyjątków</span><span class="sxs-lookup"><span data-stu-id="0974a-140">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="0974a-141">Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków</span><span class="sxs-lookup"><span data-stu-id="0974a-141">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="0974a-142">Instrukcje: Używanie określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="0974a-142">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="0974a-143">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="0974a-143">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="0974a-144">Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="0974a-144">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="0974a-145">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="0974a-145">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="0974a-146">Instrukcje: Używanie bloków finally</span><span class="sxs-lookup"><span data-stu-id="0974a-146">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="0974a-147">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="0974a-147">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="0974a-148">Najlepsze rozwiązania dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="0974a-148">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="0974a-149">Co każdy deweloper musi wiedzieć o wyjątkach w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="0974a-149">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
