---
title: "Najlepsze praktyki dotyczące wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: "28"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4c5ea19077ff9ce8e36a33601b7e5e87c64afe60
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="35bb3-102">Najlepsze praktyki dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="35bb3-102">Best practices for exceptions</span></span>

<span data-ttu-id="35bb3-103">Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35bb3-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="35bb3-104">W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i Tworzenie wyjątków.</span><span class="sxs-lookup"><span data-stu-id="35bb3-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks"></a><span data-ttu-id="35bb3-105">Użyj bloki try/catch/finally</span><span class="sxs-lookup"><span data-stu-id="35bb3-105">Use try/catch/finally blocks</span></span>

<span data-ttu-id="35bb3-106">Użyj `try` / `catch` / `finally` bloki wokół kod, który może potencjalnie wygenerować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35bb3-106">Use `try`/`catch`/`finally` blocks around code that can potentially generate an exception.</span></span> 

<span data-ttu-id="35bb3-107">W `catch` blokuje zawsze wyjątki w kolejności od najbardziej właściwe do najmniej specyficznych.</span><span class="sxs-lookup"><span data-stu-id="35bb3-107">In `catch` blocks, always order exceptions from the most specific to the least specific.</span></span>

<span data-ttu-id="35bb3-108">Użyj `finally` bloku, aby wyczyścić zasoby, czy użytkownik może odzyskać lub nie.</span><span class="sxs-lookup"><span data-stu-id="35bb3-108">Use a `finally` block to clean up resources, whether you can recover or not.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="35bb3-109">Obsługi typowe warunki bez zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="35bb3-109">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="35bb3-110">Warunki, które mogą wystąpić, ale może powodować powstanie wyjątku, należy rozważyć ich obsługę w taki sposób, aby uniknąć tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-110">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="35bb3-111">Na przykład, Jeśli spróbujesz zamknąć połączenie, które jest już zamknięty, otrzymasz `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="35bb3-111">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="35bb3-112">Można uniknąć który za pomocą `if` instrukcji, aby sprawdzić stan połączenia przed podjęciem próby go zamknąć.</span><span class="sxs-lookup"><span data-stu-id="35bb3-112">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  

<span data-ttu-id="35bb3-113">Jeśli nie zaznaczysz stan połączenia przed zamknięciem, można przechwycić `InvalidOperationException` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-113">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  

<span data-ttu-id="35bb3-114">Wybierz metodę zależy od tego, częstotliwość wystąpienie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="35bb3-114">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="35bb3-115">Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-115">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="35bb3-116">Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="35bb3-116">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="35bb3-117">Sprawdź, czy warunki błędów w kodzie, jeśli zdarzenie wykonywany jest rutynowo i może zostać uznana za część normalnego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="35bb3-117">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="35bb3-118">Podczas sprawdzania dostępności typowe warunki błędów, mniejsza ilość kodu jest wykonywana, ponieważ uniknąć wyjątków.</span><span class="sxs-lookup"><span data-stu-id="35bb3-118">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="35bb3-119">Projektowanie klas, aby uniknąć wyjątków</span><span class="sxs-lookup"><span data-stu-id="35bb3-119">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="35bb3-120">Klasa może zapewnić metody lub właściwości, które pozwalają uniknąć nawiązywania połączenia, który może powodować powstanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-120">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="35bb3-121">Na przykład <xref:System.IO.FileStream> klasa dostarcza metody, które pomagają w ustaleniu, czy osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-121">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="35bb3-122">Mogą one używane w celu uniknięcia wyjątek, który jest generowany, jeśli odczytu poza końcem pliku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-122">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="35bb3-123">Poniższy przykład pokazuje, jak można odczytać na końcu pliku bez wyzwalania Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35bb3-123">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  

<span data-ttu-id="35bb3-124">Innym sposobem uniknięcia wyjątków jest zwracana wartość null dla bardzo typowych przypadkach błąd zamiast generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-124">Another way to avoid exceptions is to return null for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="35bb3-125">Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania.</span><span class="sxs-lookup"><span data-stu-id="35bb3-125">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="35bb3-126">Zwracanie w takich przypadkach wartości null minimalizuje ich wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35bb3-126">By returning null in these cases, you minimize the performance impact to an app.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="35bb3-127">Zgłaszanie wyjątków zamiast zwróciło kod błędu</span><span class="sxs-lookup"><span data-stu-id="35bb3-127">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="35bb3-128">Wyjątki upewnij się, że błędy nie niezauważone ponieważ wywoływanie kodu nie Sprawdź kod powrotu.</span><span class="sxs-lookup"><span data-stu-id="35bb3-128">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span> 

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="35bb3-129">Użyj wstępnie zdefiniowanych typów wyjątków .NET</span><span class="sxs-lookup"><span data-stu-id="35bb3-129">Use the predefined .NET exception types</span></span>

<span data-ttu-id="35bb3-130">Wprowadzenie nowej klasy wyjątku tylko wtedy, gdy jeden wstępnie zdefiniowanych nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="35bb3-130">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="35bb3-131">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="35bb3-131">For example:</span></span>

- <span data-ttu-id="35bb3-132">Throw <xref:System.InvalidOperationException> wyjątek, jeśli właściwość zestawu lub wywołanie metody nie jest odpowiedni podane bieżącego stanu obiektu.</span><span class="sxs-lookup"><span data-stu-id="35bb3-132">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="35bb3-133">Throw <xref:System.ArgumentException> wyjątku lub jednej z wstępnie zdefiniowanych klas pochodzących od <xref:System.ArgumentException> Jeżeli nie przekazano nieprawidłowe parametry.</span><span class="sxs-lookup"><span data-stu-id="35bb3-133">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="35bb3-134">Nazwy klasy wyjątków zakończenia wyraz`Exception`</span><span class="sxs-lookup"><span data-stu-id="35bb3-134">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="35bb3-135">Gdy konieczne jest niestandardowy wyjątek, odpowiednio nazwę i pochodzi ona z <xref:System.Exception> klasy.</span><span class="sxs-lookup"><span data-stu-id="35bb3-135">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="35bb3-136">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="35bb3-136">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="35bb3-137">Obejmują trzy konstruktorów w klasach niestandardowego wyjątku</span><span class="sxs-lookup"><span data-stu-id="35bb3-137">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="35bb3-138">Użyj co najmniej trzy konstruktorów wspólnej podczas tworzenia własnych klas wyjątek: konstruktora domyślnego konstruktora przyjmującego ciąg komunikatu i konstruktora przyjmującego ciąg komunikatu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="35bb3-138">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="35bb3-139"><xref:System.Exception.%23ctor>, które są używane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="35bb3-139"><xref:System.Exception.%23ctor>, which uses default values.</span></span>
  
* <span data-ttu-id="35bb3-140"><xref:System.Exception.%23ctor%28System.String%29>, która akceptuje ciąg komunikatu.</span><span class="sxs-lookup"><span data-stu-id="35bb3-140"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>  
  
* <span data-ttu-id="35bb3-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, która akceptuje ciąg komunikatu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="35bb3-141"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>  
  
<span data-ttu-id="35bb3-142">Na przykład zobacz [porady: wyjątki Create User-Defined](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="35bb3-142">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="35bb3-143">Upewnij się, dane wyjątku jest dostępna, gdy kod jest wykonywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="35bb3-143">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="35bb3-144">Podczas tworzenia wyjątki zdefiniowane przez użytkownika, upewnij się, że metadane dla wyjątków jest dostępny do kodu, który jest wykonywany zdalnie.</span><span class="sxs-lookup"><span data-stu-id="35bb3-144">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span> 

<span data-ttu-id="35bb3-145">Na przykład w implementacjach .NET, które obsługują domen aplikacji, wyjątki między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35bb3-145">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="35bb3-146">Załóżmy, że domena aplikacji A tworzy aplikację domeny B, który wykonuje kod, który zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35bb3-146">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="35bb3-147">Domeny aplikacji A Aby prawidłowo wychwycić i obsłużyć wyjątek musi być w stanie odnaleźć zestawu, który zawiera wyjątku zgłoszonego przez B. domeny aplikacji Jeśli aplikacja domena B zgłasza wyjątek, który jest zawarty w zestawie w swojej bazie aplikacji, ale nie w domenie aplikacji, A baza aplikacji, domena aplikacji, A nie będzie można znaleźć w wyjątku i zgłosi środowisko uruchomieniowe języka wspólnego <xref:System.IO.FileNotFoundException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-147">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="35bb3-148">Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="35bb3-148">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="35bb3-149">Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="35bb3-149">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="35bb3-150">\-lub -</span><span class="sxs-lookup"><span data-stu-id="35bb3-150">\- or -</span></span>

- <span data-ttu-id="35bb3-151">Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="35bb3-151">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="include-a-localized-description-string-in-every-exception"></a><span data-ttu-id="35bb3-152">Zawierają ciąg zlokalizowany opis w każdym wyjątku</span><span class="sxs-lookup"><span data-stu-id="35bb3-152">Include a localized description string in every exception</span></span>

<span data-ttu-id="35bb3-153">Użytkownik zobaczy następujący komunikat o błędzie jest uzyskiwany z ciąg opisu wyjątku, który został zgłoszony, a nie z nazwa klasy wyjątku.</span><span class="sxs-lookup"><span data-stu-id="35bb3-153">The error message that the user sees is derived from the description string of the exception that was thrown, and not from the name of the exception class.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="35bb3-154">Użyj gramatycznie Popraw komunikaty o błędach</span><span class="sxs-lookup"><span data-stu-id="35bb3-154">Use grammatically correct error messages</span></span>

<span data-ttu-id="35bb3-155">Zapisz wyczyść zdań i dołączyć końcowy znaków interpunkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="35bb3-155">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="35bb3-156">Każde zdanie w ciągu opisu wyjątku powinno być zakończone kropką.</span><span class="sxs-lookup"><span data-stu-id="35bb3-156">Each sentence in a description string of an exception should end in a period.</span></span> <span data-ttu-id="35bb3-157">Na przykład "w tabeli dziennika jest przepełniony."</span><span class="sxs-lookup"><span data-stu-id="35bb3-157">For example, "The log table has overflowed."</span></span> <span data-ttu-id="35bb3-158">może być ciągiem opis.</span><span class="sxs-lookup"><span data-stu-id="35bb3-158">would be an appropriate description string.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="35bb3-159">W niestandardowymi wyjątkami udostępniają dodatkowe właściwości, w razie potrzeby</span><span class="sxs-lookup"><span data-stu-id="35bb3-159">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="35bb3-160">Podaj dodatkowe właściwości dla wyjątku (oprócz ciąg opisu) tylko wtedy, gdy programowe scenariusz, w którym przydaje się dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="35bb3-160">Provide additional properties for an exception (in addition to the description string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="35bb3-161">Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwości.</span><span class="sxs-lookup"><span data-stu-id="35bb3-161">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="35bb3-162">Miejsce throw — instrukcje, aby ślad stosu okaże się pomocna</span><span class="sxs-lookup"><span data-stu-id="35bb3-162">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="35bb3-163">Ślad stosu zaczyna się od instrukcji, gdzie wyjątek jest zgłaszany i kończy się na `catch` instrukcji, która przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="35bb3-163">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="35bb3-164">Użyj metody konstruktora wyjątku</span><span class="sxs-lookup"><span data-stu-id="35bb3-164">Use exception builder methods</span></span>

<span data-ttu-id="35bb3-165">Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji.</span><span class="sxs-lookup"><span data-stu-id="35bb3-165">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="35bb3-166">Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają.</span><span class="sxs-lookup"><span data-stu-id="35bb3-166">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="35bb3-167">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="35bb3-167">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
<span data-ttu-id="35bb3-168">W niektórych przypadkach jest bardziej odpowiednia umożliwia utworzenie wyjątek obsługi wyjątku konstruktora.</span><span class="sxs-lookup"><span data-stu-id="35bb3-168">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="35bb3-169">Przykładem jest klasa wyjątków globalne <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="35bb3-169">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="clean-up-intermediate-results-when-throwing-an-exception"></a><span data-ttu-id="35bb3-170">Wyczyść wyniki pośrednie po zgłoszeniu wyjątku</span><span class="sxs-lookup"><span data-stu-id="35bb3-170">Clean up intermediate results when throwing an exception</span></span>

<span data-ttu-id="35bb3-171">Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="35bb3-171">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="35bb3-172">Na przykład jeśli kod, który przesyła pieniędzy wycofania z jednego konta i złożenie na innym koncie, a wyjątek podczas wykonywania złożenia, nie mają wycofania do obowiązują.</span><span class="sxs-lookup"><span data-stu-id="35bb3-172">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

<span data-ttu-id="35bb3-173">Jednym ze sposobów obsłużyć taką sytuację jest catch wszelkie wyjątki zgłaszane przez transakcji wpłaty i wycofać wycofanie.</span><span class="sxs-lookup"><span data-stu-id="35bb3-173">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

```csharp
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw;
    }
}
```

<span data-ttu-id="35bb3-174">W tym przykładzie przedstawiono użycie `throw` ponowne wygenerowanie oryginalnego wyjątków, które mogą ułatwić wywołań wyświetlić rzeczywiste przyczyną problemu bez konieczności zbadać <xref:System.Exception.InnerException> właściwości.</span><span class="sxs-lookup"><span data-stu-id="35bb3-174">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="35bb3-175">Alternatywą jest zgłoszenie wyjątku nowy i zawiera pierwotny wyjątek jako wyjątek wewnętrzny:</span><span class="sxs-lookup"><span data-stu-id="35bb3-175">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a><span data-ttu-id="35bb3-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="35bb3-176">See Also</span></span>  
[<span data-ttu-id="35bb3-177">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="35bb3-177">Exceptions</span></span>](index.md)
