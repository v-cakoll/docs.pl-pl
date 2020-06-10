---
title: Obsługa i zgłaszanie wyjątków w programie .NET
description: Dowiedz się, jak obsługiwać i generować wyjątki w programie .NET. Wyjątki to sposób, w jaki operacje .NET wskazują niepowodzenie aplikacji.
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
ms.openlocfilehash: 89d88e3128917125d1a09466ed4e230604d6978c
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662774"
---
# <a name="handling-and-throwing-exceptions-in-net"></a><span data-ttu-id="7687e-104">Obsługa i zgłaszanie wyjątków w programie .NET</span><span class="sxs-lookup"><span data-stu-id="7687e-104">Handling and throwing exceptions in .NET</span></span>

<span data-ttu-id="7687e-105">Aplikacje muszą być w stanie obsługiwać błędy występujące podczas wykonywania w spójny sposób.</span><span class="sxs-lookup"><span data-stu-id="7687e-105">Applications must be able to handle errors that occur during execution in a consistent manner.</span></span> <span data-ttu-id="7687e-106">Platforma .NET udostępnia model do powiadamiania aplikacji o błędach w jednolity sposób: operacje platformy .NET wskazują na awarię przez wyrzucanie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7687e-106">.NET provides a model for notifying applications of errors in a uniform way: .NET operations indicate failure by throwing exceptions.</span></span>

## <a name="exceptions"></a><span data-ttu-id="7687e-107">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="7687e-107">Exceptions</span></span>

<span data-ttu-id="7687e-108">Wyjątek jest dowolnym warunkiem błędu lub nieoczekiwanym zachowaniem napotkanym przez program wykonujący.</span><span class="sxs-lookup"><span data-stu-id="7687e-108">An exception is any error condition or unexpected behavior that is encountered by an executing program.</span></span> <span data-ttu-id="7687e-109">Wyjątki mogą być zgłaszane z powodu błędu w kodzie lub kodu, który jest wywoływany (na przykład biblioteki udostępnionej), niedostępnych zasobów systemu operacyjnego, nieoczekiwanych warunków napotkanych przez środowisko uruchomieniowe (takich jak kod, którego nie można zweryfikować) itd.</span><span class="sxs-lookup"><span data-stu-id="7687e-109">Exceptions can be thrown because of a fault in your code or in code that you call (such as a shared library), unavailable operating system resources, unexpected conditions that the runtime encounters (such as code that can't be verified), and so on.</span></span> <span data-ttu-id="7687e-110">Aplikacja może wykonać odzyskiwanie z niektórych z tych warunków, ale nie od innych.</span><span class="sxs-lookup"><span data-stu-id="7687e-110">Your application can recover from some of these conditions, but not from others.</span></span> <span data-ttu-id="7687e-111">Chociaż można wykonać odzyskiwanie z większości wyjątków aplikacji, nie można odzyskać sprawności z większości wyjątków czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7687e-111">Although you can recover from most application exceptions, you can't recover from most runtime exceptions.</span></span>

<span data-ttu-id="7687e-112">W programie .NET wyjątek jest obiektem, który dziedziczy z <xref:System.Exception?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="7687e-112">In .NET, an exception is an object that inherits from the <xref:System.Exception?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7687e-113">Wyjątek jest generowany z obszaru kodu, w którym wystąpił problem.</span><span class="sxs-lookup"><span data-stu-id="7687e-113">An exception is thrown from an area of code where a problem has occurred.</span></span> <span data-ttu-id="7687e-114">Wyjątek jest przenoszona do momentu, aż aplikacja obsłuży go lub zakończy działanie programu.</span><span class="sxs-lookup"><span data-stu-id="7687e-114">The exception is passed up the stack until the application handles it or the program terminates.</span></span>

## <a name="exceptions-vs-traditional-error-handling-methods"></a><span data-ttu-id="7687e-115">Wyjątki a tradycyjne metody obsługi błędów</span><span class="sxs-lookup"><span data-stu-id="7687e-115">Exceptions vs. traditional error-handling methods</span></span>

<span data-ttu-id="7687e-116">Tradycyjnie model obsługi błędów języka opiera się na unikatowym sposobie wykrywania błędów i lokalizowania programów obsługi albo w mechanizmie obsługi błędów dostarczonym przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="7687e-116">Traditionally, a language's error-handling model relied on either the language's unique way of detecting errors and locating handlers for them, or on the error-handling mechanism provided by the operating system.</span></span> <span data-ttu-id="7687e-117">Sposób, w jaki program .NET implementuje obsługę wyjątków, zapewnia następujące korzyści:</span><span class="sxs-lookup"><span data-stu-id="7687e-117">The way .NET implements exception handling provides the following advantages:</span></span>

- <span data-ttu-id="7687e-118">Przerzucanie i obsługa wyjątków działa tak samo dla języków programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="7687e-118">Exception throwing and handling works the same for .NET programming languages.</span></span>

- <span data-ttu-id="7687e-119">Nie wymaga żadnej określonej składni języka do obsługi wyjątków, ale umożliwia każdemu językowi zdefiniowanie własnej składni.</span><span class="sxs-lookup"><span data-stu-id="7687e-119">Doesn't require any particular language syntax for handling exceptions, but allows each language to define its own syntax.</span></span>

- <span data-ttu-id="7687e-120">Wyjątki mogą być zgłaszane między procesami, a nawet granicami maszyn.</span><span class="sxs-lookup"><span data-stu-id="7687e-120">Exceptions can be thrown across process and even machine boundaries.</span></span>

- <span data-ttu-id="7687e-121">Kod obsługi wyjątków można dodać do aplikacji w celu zwiększenia niezawodności programu.</span><span class="sxs-lookup"><span data-stu-id="7687e-121">Exception-handling code can be added to an application to increase program reliability.</span></span>

<span data-ttu-id="7687e-122">Wyjątki oferują zalety w porównaniu z innymi metodami powiadamiania o błędach, takich jak kody powrotne.</span><span class="sxs-lookup"><span data-stu-id="7687e-122">Exceptions offer advantages over other methods of error notification, such as return codes.</span></span> <span data-ttu-id="7687e-123">Niepowodzenia nie są wyrzucane, ponieważ jeśli wystąpi wyjątek, a jego nie obsłużysz, środowisko uruchomieniowe zakończy działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7687e-123">Failures don't go unnoticed because if an exception is thrown and you don't handle it, the runtime terminates your application.</span></span> <span data-ttu-id="7687e-124">Nieprawidłowe wartości nie są nadal propagowane przez system w wyniku kodu, który nie może sprawdzić kodu powrotu błędu.</span><span class="sxs-lookup"><span data-stu-id="7687e-124">Invalid values don't continue to propagate through the system as a result of code that fails to check for a failure return code.</span></span>

## <a name="common-exceptions"></a><span data-ttu-id="7687e-125">Typowe wyjątki</span><span class="sxs-lookup"><span data-stu-id="7687e-125">Common exceptions</span></span>

<span data-ttu-id="7687e-126">W poniższej tabeli wymieniono niektóre typowe wyjątki z przykładami, które mogą je spowodować.</span><span class="sxs-lookup"><span data-stu-id="7687e-126">The following table lists some common exceptions with examples of what can cause them.</span></span>

| <span data-ttu-id="7687e-127">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="7687e-127">Exception type</span></span> | <span data-ttu-id="7687e-128">Opis</span><span class="sxs-lookup"><span data-stu-id="7687e-128">Description</span></span> | <span data-ttu-id="7687e-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="7687e-129">Example</span></span> |
| -------------- | ----------- | ------- |
| <xref:System.Exception> | <span data-ttu-id="7687e-130">Klasa bazowa dla wszystkich wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7687e-130">Base class for all exceptions.</span></span> | <span data-ttu-id="7687e-131">Brak (Użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="7687e-131">None (use a derived class of this exception).</span></span> |
| <xref:System.IndexOutOfRangeException> | <span data-ttu-id="7687e-132">Zgłoszone przez środowisko uruchomieniowe tylko wtedy, gdy tablica jest indeksowana nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="7687e-132">Thrown by the runtime only when an array is indexed improperly.</span></span> | <span data-ttu-id="7687e-133">Indeksowanie tablicy poza prawidłowym zakresem:</span><span class="sxs-lookup"><span data-stu-id="7687e-133">Indexing an array outside its valid range:</span></span> <br /> `arr[arr.Length+1]` |
| <xref:System.NullReferenceException> | <span data-ttu-id="7687e-134">Zgłoszone przez środowisko uruchomieniowe tylko wtedy, gdy istnieje odwołanie do obiektu o wartości null.</span><span class="sxs-lookup"><span data-stu-id="7687e-134">Thrown by the runtime only when a null object is referenced.</span></span> | `object o = null;` <br /> `o.ToString();` |
| <xref:System.InvalidOperationException> | <span data-ttu-id="7687e-135">Zgłoszone przez metody w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="7687e-135">Thrown by methods when in an invalid state.</span></span> | <span data-ttu-id="7687e-136">Wywoływanie `Enumerator.MoveNext()` po usunięciu elementu z kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="7687e-136">Calling `Enumerator.MoveNext()` after removing an item from the underlying collection.</span></span> |
| <xref:System.ArgumentException> | <span data-ttu-id="7687e-137">Klasa bazowa dla wszystkich wyjątków argumentów.</span><span class="sxs-lookup"><span data-stu-id="7687e-137">Base class for all argument exceptions.</span></span> | <span data-ttu-id="7687e-138">Brak (Użyj klasy pochodnej tego wyjątku).</span><span class="sxs-lookup"><span data-stu-id="7687e-138">None (use a derived class of this exception).</span></span> |
| <xref:System.ArgumentNullException> | <span data-ttu-id="7687e-139">Zgłoszone przez metody, które nie zezwalają argumentu na wartość null.</span><span class="sxs-lookup"><span data-stu-id="7687e-139">Thrown by methods that do not allow an argument to be null.</span></span> | `String s = null;` <br /> `"Calculate".IndexOf(s);`|
| <xref:System.ArgumentOutOfRangeException> | <span data-ttu-id="7687e-140">Zgłoszone przez metody, które weryfikują, że argumenty znajdują się w danym zakresie.</span><span class="sxs-lookup"><span data-stu-id="7687e-140">Thrown by methods that verify that arguments are in a given range.</span></span> | `String s = "string";` <br /> `s.Substring(s.Length+1);` |

## <a name="see-also"></a><span data-ttu-id="7687e-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7687e-141">See also</span></span>

- [<span data-ttu-id="7687e-142">Klasa wyjątku i właściwości</span><span class="sxs-lookup"><span data-stu-id="7687e-142">Exception Class and Properties</span></span>](exception-class-and-properties.md)
- [<span data-ttu-id="7687e-143">Instrukcje: Używanie bloku try/catch do przechwytywania wyjątków</span><span class="sxs-lookup"><span data-stu-id="7687e-143">How to: Use the Try-Catch Block to Catch Exceptions</span></span>](how-to-use-the-try-catch-block-to-catch-exceptions.md)
- [<span data-ttu-id="7687e-144">Instrukcje: Używanie określonych wyjątków w bloku catch</span><span class="sxs-lookup"><span data-stu-id="7687e-144">How to: Use Specific Exceptions in a Catch Block</span></span>](how-to-use-specific-exceptions-in-a-catch-block.md)
- [<span data-ttu-id="7687e-145">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="7687e-145">How to: Explicitly Throw Exceptions</span></span>](how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="7687e-146">Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7687e-146">How to: Create User-Defined Exceptions</span></span>](how-to-create-user-defined-exceptions.md)
- [<span data-ttu-id="7687e-147">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="7687e-147">Using User-Filtered Exception Handlers</span></span>](using-user-filtered-exception-handlers.md)
- [<span data-ttu-id="7687e-148">Instrukcje: Używanie bloków finally</span><span class="sxs-lookup"><span data-stu-id="7687e-148">How to: Use Finally Blocks</span></span>](how-to-use-finally-blocks.md)
- [<span data-ttu-id="7687e-149">Obsługa wyjątków międzyoperacyjności COM</span><span class="sxs-lookup"><span data-stu-id="7687e-149">Handling COM Interop Exceptions</span></span>](handling-com-interop-exceptions.md)
- [<span data-ttu-id="7687e-150">Najlepsze rozwiązania dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="7687e-150">Best Practices for Exceptions</span></span>](best-practices-for-exceptions.md)
- [<span data-ttu-id="7687e-151">Co każdy Deweloper musi wiedzieć o wyjątkach w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="7687e-151">What Every Dev needs to Know About Exceptions in the Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/exceptions.md)
