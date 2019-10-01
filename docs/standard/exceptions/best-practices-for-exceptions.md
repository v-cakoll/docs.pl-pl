---
title: Najlepsze rozwiązania dotyczące wyjątków — .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 6a165c3e0f41603ef7233669d7148dd44b1d3ce6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696765"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="510f5-102">Najlepsze rozwiązania dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="510f5-102">Best practices for exceptions</span></span>

<span data-ttu-id="510f5-103">Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji.</span><span class="sxs-lookup"><span data-stu-id="510f5-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="510f5-104">W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="510f5-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="510f5-105">Użyj bloków try/catch/finally do odzyskania po błędach lub zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="510f5-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="510f5-106">Użyj `try` @ no__t-1 @ no__t-2 bloków wokół kodu, który może potencjalnie generować wyjątek ***, a*** kod może zostać odzyskany od tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="510f5-107">W blokach `catch` zawsze Porządkuj wyjątki od najbardziej pochodnych do najmniej pochodnych.</span><span class="sxs-lookup"><span data-stu-id="510f5-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="510f5-108">Wszystkie wyjątki pochodzą z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="510f5-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="510f5-109">Bardziej pochodne wyjątki nie są obsługiwane przez klauzulę catch, która poprzedza klauzulę catch dla bazowej klasy wyjątków.</span><span class="sxs-lookup"><span data-stu-id="510f5-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="510f5-110">Jeśli kod nie może odzyskać z wyjątku, nie należy przechwytywać tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="510f5-111">Włącz metody, aby zwiększyć stos wywołań, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="510f5-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="510f5-112">Wyczyść zasoby przydzieloną z użyciem instrukcji `using` lub bloków `finally`.</span><span class="sxs-lookup"><span data-stu-id="510f5-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="510f5-113">Preferuj `using` instrukcji, aby automatycznie czyścić zasoby po zgłoszeniu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="510f5-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="510f5-114">Użyj bloków `finally`, aby wyczyścić zasoby, które nie implementują <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="510f5-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="510f5-115">Kod w klauzuli `finally` jest prawie zawsze wykonywany nawet wtedy, gdy są zgłaszane wyjątki.</span><span class="sxs-lookup"><span data-stu-id="510f5-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="510f5-116">Obsługa typowych warunków bez zgłaszania wyjątków</span><span class="sxs-lookup"><span data-stu-id="510f5-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="510f5-117">W przypadku warunków, które mogą wystąpić, ale mogą wyzwolić wyjątek, należy rozważyć obsługę ich w taki sposób, aby uniknąć tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="510f5-118">Na przykład jeśli spróbujesz zamknąć połączenie, które zostało już zamknięte, uzyskasz `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="510f5-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="510f5-119">Można uniknąć używania instrukcji `if`, aby sprawdzić stan połączenia przed próbą zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="510f5-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="510f5-120">Jeśli nie sprawdzasz stanu połączenia przed zamknięciem, możesz przechwycić wyjątek `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="510f5-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="510f5-121">Metoda do wyboru zależy od częstotliwości wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="510f5-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="510f5-122">Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="510f5-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="510f5-123">Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="510f5-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="510f5-124">Sprawdź, czy w kodzie wystąpią błędy, jeśli zdarzenie jest wykonywane rutynowo i może być uważane za część normalnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="510f5-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="510f5-125">Po sprawdzeniu typowych warunków błędu jest wykonywany mniej kodu, ponieważ unikasz wyjątków.</span><span class="sxs-lookup"><span data-stu-id="510f5-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="510f5-126">Klasy projektowania umożliwiające uniknięcie wyjątków</span><span class="sxs-lookup"><span data-stu-id="510f5-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="510f5-127">Klasa może udostępniać metody lub właściwości, które umożliwiają uniknięcie wywołania, które wywoła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="510f5-128">Na przykład Klasa <xref:System.IO.FileStream> zawiera metody, które ułatwiają określenie, czy osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="510f5-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="510f5-129">Można ich użyć, aby uniknąć zgłoszonego wyjątku w przypadku odczytu poza końcem pliku.</span><span class="sxs-lookup"><span data-stu-id="510f5-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="510f5-130">Poniższy przykład pokazuje, jak odczytać na końcu pliku bez wyzwalania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="510f5-131">Inny sposób, aby uniknąć wyjątków, ma zwrócić wartość null (lub wartość domyślną) dla skrajnie typowych przypadków błędów zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="510f5-132">Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania.</span><span class="sxs-lookup"><span data-stu-id="510f5-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="510f5-133">Zwracając wartość null (lub domyślną) w takich przypadkach można zminimalizować wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="510f5-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="510f5-134">W przypadku typów wartości, niezależnie od tego, czy dla konkretnej aplikacji ma być używany `Nullable<T>` czy jako wskaźnik błędu.</span><span class="sxs-lookup"><span data-stu-id="510f5-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="510f5-135">Za pomocą `Nullable<Guid>`, `default` zostanie `null` zamiast `Guid.Empty`.</span><span class="sxs-lookup"><span data-stu-id="510f5-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="510f5-136">Czasami dodanie `Nullable<T>` może sprawić, że jest to wyraźniejsze, gdy wartość jest obecna lub nieobecna.</span><span class="sxs-lookup"><span data-stu-id="510f5-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="510f5-137">Czasami dodanie `Nullable<T>` może stworzyć dodatkowe przypadki, aby sprawdzić, czy nie są potrzebne, i służy tylko do tworzenia potencjalnych źródeł błędów.</span><span class="sxs-lookup"><span data-stu-id="510f5-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span> 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="510f5-138">Zgłoś wyjątki zamiast zwracać kod błędu</span><span class="sxs-lookup"><span data-stu-id="510f5-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="510f5-139">Wyjątki zapewniają, że niepowodzenia nie są niezauważalne, ponieważ wywołanie kodu nie sprawdza kodu powrotu.</span><span class="sxs-lookup"><span data-stu-id="510f5-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="510f5-140">Użyj wstępnie zdefiniowanych typów wyjątków platformy .NET</span><span class="sxs-lookup"><span data-stu-id="510f5-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="510f5-141">Wprowadź nową klasę wyjątku tylko wtedy, gdy wstępnie zdefiniowany element nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="510f5-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="510f5-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="510f5-142">For example:</span></span>

- <span data-ttu-id="510f5-143">Zgłoś wyjątek <xref:System.InvalidOperationException>, jeśli zestaw właściwości lub wywołanie metody nie jest odpowiedni dla bieżącego stanu obiektu.</span><span class="sxs-lookup"><span data-stu-id="510f5-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="510f5-144">Zgłoś wyjątek <xref:System.ArgumentException> lub jedną ze wstępnie zdefiniowanych klas, które pochodzą od <xref:System.ArgumentException>, jeśli przechodzą nieprawidłowe parametry.</span><span class="sxs-lookup"><span data-stu-id="510f5-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="510f5-145">Zakończ nazwy klas wyjątków za pomocą słowa `Exception`</span><span class="sxs-lookup"><span data-stu-id="510f5-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="510f5-146">Gdy niestandardowa jest konieczna, nadaj jej odpowiednią nazwę i pokieruj ją z klasy <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="510f5-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="510f5-147">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="510f5-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="510f5-148">Dołącz trzy konstruktory do klas wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="510f5-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="510f5-149">Podczas tworzenia własnych klas wyjątków należy używać co najmniej trzech typowych konstruktorów: Konstruktor bez parametrów, Konstruktor, który pobiera komunikat ciągu, oraz Konstruktor, który pobiera komunikat ciągu i wewnętrzny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="510f5-150"><xref:System.Exception.%23ctor>, który używa wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="510f5-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="510f5-151"><xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat ciągu.</span><span class="sxs-lookup"><span data-stu-id="510f5-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="510f5-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat ciągu i wewnętrzny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="510f5-153">Aby zapoznać się z przykładem, zobacz [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="510f5-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="510f5-154">Upewnij się, że dane wyjątków są dostępne, gdy kod jest wykonywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="510f5-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="510f5-155">Podczas tworzenia wyjątków zdefiniowanych przez użytkownika upewnij się, że metadane dla tych wyjątków są dostępne dla kodu, który jest wykonywany zdalnie.</span><span class="sxs-lookup"><span data-stu-id="510f5-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="510f5-156">Na przykład w przypadku implementacji platformy .NET obsługujących domeny aplikacji mogą wystąpić wyjątki między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="510f5-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="510f5-157">Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod, który zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="510f5-158">W przypadku domeny aplikacji A, aby prawidłowo przechwycić i obsłużyć wyjątek, musi być w stanie znaleźć zestaw zawierający wyjątek zgłoszony przez domenę aplikacji B. Jeśli domena aplikacji B zgłosi wyjątek, który jest zawarty w zestawie w jego bazie aplikacji, ale nie pod bazą aplikacji domeny aplikacji A, domena aplikacji A nie będzie mogła znaleźć wyjątku, a środowisko uruchomieniowe języka wspólnego zgłosi wyjątek <xref:System.IO.FileNotFoundException>.</span><span class="sxs-lookup"><span data-stu-id="510f5-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="510f5-159">Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="510f5-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="510f5-160">Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="510f5-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="510f5-161">\- lub-</span><span class="sxs-lookup"><span data-stu-id="510f5-161">\- or -</span></span>

- <span data-ttu-id="510f5-162">Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="510f5-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="510f5-163">Używaj komunikatów o błędach z prawidłowymi gramatykami</span><span class="sxs-lookup"><span data-stu-id="510f5-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="510f5-164">Napisz jasne zdania i Dołącz kończące znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="510f5-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="510f5-165">Każde zdanie w ciągu przypisanym do właściwości <xref:System.Exception.Message?displayProperty=nameWithType> powinno kończyć się kropką.</span><span class="sxs-lookup"><span data-stu-id="510f5-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="510f5-166">Na przykład "tabela dziennika ma przepełnienie".</span><span class="sxs-lookup"><span data-stu-id="510f5-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="510f5-167">być prawidłowym ciągiem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="510f5-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="510f5-168">Dołącz zlokalizowany komunikat ciągu w każdym wyjątku</span><span class="sxs-lookup"><span data-stu-id="510f5-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="510f5-169">Komunikat o błędzie, który użytkownik widzi, pochodzi od właściwości <xref:System.Exception.Message?displayProperty=nameWithType> zgłoszonego wyjątku, a nie z nazwy klasy wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="510f5-170">Zwykle przypisujesz wartość do właściwości <xref:System.Exception.Message?displayProperty=nameWithType> przez przekazanie ciągu komunikatu do argumentu `message` [konstruktora wyjątków](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="510f5-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="510f5-171">W przypadku zlokalizowanych aplikacji należy podać zlokalizowany ciąg komunikatu dla każdego wyjątku, który aplikacja może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="510f5-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="510f5-172">Pliki zasobów są używane do udostępniania zlokalizowanych komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="510f5-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="510f5-173">Aby uzyskać informacje na temat lokalizowania aplikacji i pobierania zlokalizowanych ciągów, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="510f5-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="510f5-174">Instrukcje: Tworzenie wyjątków zdefiniowanych przez użytkownika przy użyciu zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="510f5-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="510f5-175">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="510f5-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md) 
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="510f5-176">W niestandardowych wyjątkach podaj dodatkowe właściwości zgodnie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="510f5-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="510f5-177">Podaj dodatkowe właściwości wyjątku (oprócz niestandardowego ciągu wiadomości) tylko wtedy, gdy istnieje scenariusz programistyczny, w którym dodatkowe informacje są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="510f5-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="510f5-178">Na przykład <xref:System.IO.FileNotFoundException> zawiera właściwość <xref:System.IO.FileNotFoundException.FileName>.</span><span class="sxs-lookup"><span data-stu-id="510f5-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="510f5-179">Umieść instrukcje throw, aby ułatwić śledzenie stosu</span><span class="sxs-lookup"><span data-stu-id="510f5-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="510f5-180">Ślad stosu rozpoczyna się w instrukcji, w której jest zgłaszany wyjątek i jest kończący na instrukcji `catch`, która przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="510f5-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="510f5-181">Korzystanie z metod konstruktora wyjątków</span><span class="sxs-lookup"><span data-stu-id="510f5-181">Use exception builder methods</span></span>

<span data-ttu-id="510f5-182">Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji.</span><span class="sxs-lookup"><span data-stu-id="510f5-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="510f5-183">Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają.</span><span class="sxs-lookup"><span data-stu-id="510f5-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="510f5-184">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="510f5-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="510f5-185">W niektórych przypadkach bardziej odpowiednie jest użycie konstruktora wyjątku do skompilowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="510f5-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="510f5-186">Przykładem jest globalna Klasa wyjątków, taka jak <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="510f5-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="510f5-187">Przywróć stan, gdy nie ukończono metod z powodu wyjątków</span><span class="sxs-lookup"><span data-stu-id="510f5-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="510f5-188">Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="510f5-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="510f5-189">Na przykład jeśli masz kod, który transferuje pieniądze przez wycofanie z jednego konta i zdeponowanie na innym koncie, a podczas wykonywania depozytu zostanie zgłoszony wyjątek, nie chcesz, aby wycofanie zadziałało.</span><span class="sxs-lookup"><span data-stu-id="510f5-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

```vb
Public Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    from.Withdrawal(amount)
    ' If the deposit fails, the withdrawal shouldn't remain in effect.
    [to].Deposit(amount)
End Sub
```

<span data-ttu-id="510f5-190">Powyższa metoda nie generuje bezpośrednio żadnych wyjątków, ale musi być pisemnie zapisywana, aby w przypadku niepowodzenia operacji depozytu wycofanie zostało cofnięte.</span><span class="sxs-lookup"><span data-stu-id="510f5-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="510f5-191">Jednym ze sposobów obsługi tej sytuacji jest przechwycenie wszelkich wyjątków zgłoszonych przez transakcję przelewu i wycofanie wycofania.</span><span class="sxs-lookup"><span data-stu-id="510f5-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

```vb
Private Shared Sub TransferFunds(from As Account, [to] As Account, amount As Decimal)
    Dim withdrawalTrxID As String = from.Withdrawal(amount)
    Try
        [to].Deposit(amount)
    Catch
        from.RollbackTransaction(withdrawalTrxID)
        Throw
    End Try
End Sub
```

<span data-ttu-id="510f5-192">Ten przykład ilustruje użycie `throw` w celu ponownego wygenerowania oryginalnego wyjątku, co może ułatwić wywoływanie przez wywołujących problemów z rzeczywistą przyczyną problemu bez konieczności badania właściwości <xref:System.Exception.InnerException>.</span><span class="sxs-lookup"><span data-stu-id="510f5-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="510f5-193">Alternatywą jest zgłoszenie nowego wyjątku i uwzględnienie pierwotnego wyjątku jako wyjątku wewnętrznego:</span><span class="sxs-lookup"><span data-stu-id="510f5-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed.", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

```vb
Catch ex As Exception
    from.RollbackTransaction(withdrawalTrxID)
    Throw New TransferFundsException("Withdrawal failed.", innerException:=ex) With
    {
        .From = from,
        .[To] = [to],
        .Amount = amount
    }
End Try
```

## <a name="see-also"></a><span data-ttu-id="510f5-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="510f5-194">See also</span></span>

- [<span data-ttu-id="510f5-195">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="510f5-195">Exceptions</span></span>](index.md)
