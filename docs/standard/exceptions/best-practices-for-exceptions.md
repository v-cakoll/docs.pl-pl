---
title: Najlepsze rozwiązania dotyczące wyjątków — .NET
description: Poznaj najlepsze rozwiązania dotyczące wyjątków, takich jak korzystanie z try/catch/finally, obsługa typowych warunków bez wyjątków i używanie wstępnie zdefiniowanych typów wyjątków platformy .NET.
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 90dda00acd32852b032fc383580c5f34022ec9b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447098"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="feb38-103">Najlepsze rozwiązania dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="feb38-103">Best practices for exceptions</span></span>

<span data-ttu-id="feb38-104">Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-104">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="feb38-105">W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="feb38-105">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="feb38-106">Użyj bloków try/catch/finally do odzyskania po błędach lub zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="feb38-106">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="feb38-107">Używaj `try` / `catch` bloków otaczających kod, który może potencjalnie generować wyjątek ***, a*** kod można odzyskać z tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-107">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="feb38-108">W `catch` blokach zawsze Porządkuj wyjątki od najbardziej pochodnych do najmniej pochodnych.</span><span class="sxs-lookup"><span data-stu-id="feb38-108">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="feb38-109">Wszystkie wyjątki pochodzą od <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="feb38-109">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="feb38-110">Bardziej pochodne wyjątki nie są obsługiwane przez klauzulę catch, która poprzedza klauzulę catch dla bazowej klasy wyjątków.</span><span class="sxs-lookup"><span data-stu-id="feb38-110">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="feb38-111">Jeśli kod nie może odzyskać z wyjątku, nie należy przechwytywać tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-111">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="feb38-112">Włącz metody, aby zwiększyć stos wywołań, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="feb38-112">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="feb38-113">Wyczyść zasoby przyłączone do obu `using` instrukcji lub `finally` bloków.</span><span class="sxs-lookup"><span data-stu-id="feb38-113">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="feb38-114">Preferuj `using` instrukcje automatycznego czyszczenia zasobów po zgłoszeniu wyjątków.</span><span class="sxs-lookup"><span data-stu-id="feb38-114">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="feb38-115">Użyj `finally` bloków, aby wyczyścić zasoby, które nie implementują <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="feb38-115">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="feb38-116">Kod w `finally` klauzuli jest prawie zawsze wykonywany nawet wtedy, gdy są zgłaszane wyjątki.</span><span class="sxs-lookup"><span data-stu-id="feb38-116">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="feb38-117">Obsługa typowych warunków bez zgłaszania wyjątków</span><span class="sxs-lookup"><span data-stu-id="feb38-117">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="feb38-118">W przypadku warunków, które mogą wystąpić, ale mogą wyzwolić wyjątek, należy rozważyć obsługę ich w taki sposób, aby uniknąć tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-118">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="feb38-119">Na przykład jeśli spróbujesz zamknąć połączenie, które zostało już zamknięte, uzyskasz `InvalidOperationException` .</span><span class="sxs-lookup"><span data-stu-id="feb38-119">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="feb38-120">Można uniknąć użycia `if` instrukcji w celu sprawdzenia stanu połączenia przed próbą zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="feb38-120">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="feb38-121">Jeśli nie sprawdzasz stanu połączenia przed zamknięciem, możesz wychwycić `InvalidOperationException` wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-121">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="feb38-122">Metoda do wyboru zależy od częstotliwości wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="feb38-122">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="feb38-123">Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="feb38-123">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="feb38-124">Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="feb38-124">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="feb38-125">Sprawdź, czy w kodzie wystąpią błędy, jeśli zdarzenie jest wykonywane rutynowo i może być uważane za część normalnego wykonania.</span><span class="sxs-lookup"><span data-stu-id="feb38-125">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="feb38-126">Po sprawdzeniu typowych warunków błędu jest wykonywany mniej kodu, ponieważ unikasz wyjątków.</span><span class="sxs-lookup"><span data-stu-id="feb38-126">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="feb38-127">Klasy projektowania umożliwiające uniknięcie wyjątków</span><span class="sxs-lookup"><span data-stu-id="feb38-127">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="feb38-128">Klasa może udostępniać metody lub właściwości, które umożliwiają uniknięcie wywołania, które wywoła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-128">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="feb38-129">Na przykład <xref:System.IO.FileStream> Klasa zawiera metody, które ułatwiają określenie, czy osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="feb38-129">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="feb38-130">Można ich użyć, aby uniknąć zgłoszonego wyjątku w przypadku odczytu poza końcem pliku.</span><span class="sxs-lookup"><span data-stu-id="feb38-130">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="feb38-131">Poniższy przykład pokazuje, jak odczytać na końcu pliku bez wyzwalania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-131">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="feb38-132">Inny sposób, aby uniknąć wyjątków, ma zwrócić wartość null (lub wartość domyślną) dla skrajnie typowych przypadków błędów zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-132">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="feb38-133">Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania.</span><span class="sxs-lookup"><span data-stu-id="feb38-133">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="feb38-134">Zwracając wartość null (lub domyślną) w takich przypadkach można zminimalizować wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-134">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="feb38-135">W przypadku typów wartości, niezależnie `Nullable<T>` od tego, czy jako wskaźnik błędu mają być brane pod uwagę w przypadku konkretnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-135">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="feb38-136">Przy użyciu `Nullable<Guid>` , `default` otrzymuje `null` zamiast `Guid.Empty` .</span><span class="sxs-lookup"><span data-stu-id="feb38-136">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="feb38-137">Czasami dodanie `Nullable<T>` może sprawiać, że jest to wyraźniejsze, gdy wartość jest obecna lub nieobecna.</span><span class="sxs-lookup"><span data-stu-id="feb38-137">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="feb38-138">Czasami dodanie `Nullable<T>` może spowodować utworzenie dodatkowych przypadków do sprawdzenia, że nie jest to konieczne, i służy tylko do tworzenia potencjalnych źródeł błędów.</span><span class="sxs-lookup"><span data-stu-id="feb38-138">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="feb38-139">Zgłoś wyjątki zamiast zwracać kod błędu</span><span class="sxs-lookup"><span data-stu-id="feb38-139">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="feb38-140">Wyjątki zapewniają, że niepowodzenia nie są niezauważalne, ponieważ wywołanie kodu nie sprawdza kodu powrotu.</span><span class="sxs-lookup"><span data-stu-id="feb38-140">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="feb38-141">Użyj wstępnie zdefiniowanych typów wyjątków platformy .NET</span><span class="sxs-lookup"><span data-stu-id="feb38-141">Use the predefined .NET exception types</span></span>

<span data-ttu-id="feb38-142">Wprowadź nową klasę wyjątku tylko wtedy, gdy wstępnie zdefiniowany element nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="feb38-142">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="feb38-143">Przykład:</span><span class="sxs-lookup"><span data-stu-id="feb38-143">For example:</span></span>

- <span data-ttu-id="feb38-144">Zgłoś <xref:System.InvalidOperationException> wyjątek, jeśli zestaw właściwości lub wywołanie metody nie jest odpowiedni dla bieżącego stanu obiektu.</span><span class="sxs-lookup"><span data-stu-id="feb38-144">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="feb38-145">Zgłoś <xref:System.ArgumentException> wyjątek lub jedną ze wstępnie zdefiniowanych klas, które pochodzą z, <xref:System.ArgumentException> Jeśli są spełnione nieprawidłowe parametry.</span><span class="sxs-lookup"><span data-stu-id="feb38-145">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="feb38-146">Koniec nazw klas wyjątków z słowem`Exception`</span><span class="sxs-lookup"><span data-stu-id="feb38-146">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="feb38-147">Gdy niestandardowa jest konieczna, nadaj jej odpowiednią nazwę i utwórz ją z <xref:System.Exception> klasy.</span><span class="sxs-lookup"><span data-stu-id="feb38-147">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="feb38-148">Przykład:</span><span class="sxs-lookup"><span data-stu-id="feb38-148">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="feb38-149">Dołącz trzy konstruktory do klas wyjątków niestandardowych</span><span class="sxs-lookup"><span data-stu-id="feb38-149">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="feb38-150">Podczas tworzenia własnych klas wyjątków należy używać co najmniej trzech typowych konstruktorów: Konstruktor bez parametrów, Konstruktor, który pobiera komunikat ciągu, oraz Konstruktor, który pobiera komunikat ciągu i wewnętrzny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-150">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="feb38-151"><xref:System.Exception.%23ctor>, który używa wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="feb38-151"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="feb38-152"><xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat ciągu.</span><span class="sxs-lookup"><span data-stu-id="feb38-152"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="feb38-153"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat ciągu i wewnętrzny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-153"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="feb38-154">Aby zapoznać się z przykładem, zobacz [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="feb38-154">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="feb38-155">Upewnij się, że dane wyjątków są dostępne, gdy kod jest wykonywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="feb38-155">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="feb38-156">Podczas tworzenia wyjątków zdefiniowanych przez użytkownika upewnij się, że metadane dla tych wyjątków są dostępne dla kodu, który jest wykonywany zdalnie.</span><span class="sxs-lookup"><span data-stu-id="feb38-156">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="feb38-157">Na przykład w przypadku implementacji platformy .NET obsługujących domeny aplikacji mogą wystąpić wyjątki między domenami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-157">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="feb38-158">Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod, który zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-158">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="feb38-159">W przypadku domeny aplikacji A, aby prawidłowo przechwycić i obsłużyć wyjątek, musi być w stanie znaleźć zestaw zawierający wyjątek zgłoszony przez domenę aplikacji B. Jeśli domena aplikacji B zgłosi wyjątek, który jest zawarty w zestawie w jego bazie aplikacji, ale nie pod bazą aplikacji domeny aplikacji A, domena aplikacji A nie będzie mogła znaleźć wyjątku, a środowisko uruchomieniowe języka wspólnego zgłosi <xref:System.IO.FileNotFoundException> wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-159">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="feb38-160">Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="feb38-160">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="feb38-161">Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-161">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="feb38-162">\-oraz</span><span class="sxs-lookup"><span data-stu-id="feb38-162">\- or -</span></span>

- <span data-ttu-id="feb38-163">Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="feb38-163">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="feb38-164">Używaj komunikatów o błędach z prawidłowymi gramatykami</span><span class="sxs-lookup"><span data-stu-id="feb38-164">Use grammatically correct error messages</span></span>

<span data-ttu-id="feb38-165">Napisz jasne zdania i Dołącz kończące znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="feb38-165">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="feb38-166">Każde zdanie w ciągu przypisanym do <xref:System.Exception.Message?displayProperty=nameWithType> Właściwości powinno kończyć się kropką.</span><span class="sxs-lookup"><span data-stu-id="feb38-166">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="feb38-167">Na przykład "tabela dziennika ma przepełnienie".</span><span class="sxs-lookup"><span data-stu-id="feb38-167">For example, "The log table has overflowed."</span></span> <span data-ttu-id="feb38-168">być prawidłowym ciągiem komunikatów.</span><span class="sxs-lookup"><span data-stu-id="feb38-168">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="feb38-169">Dołącz zlokalizowany komunikat ciągu w każdym wyjątku</span><span class="sxs-lookup"><span data-stu-id="feb38-169">Include a localized string message in every exception</span></span>

<span data-ttu-id="feb38-170">Komunikat o błędzie, który użytkownik widzi, pochodzi od <xref:System.Exception.Message?displayProperty=nameWithType> Właściwości zgłoszonego wyjątku, a nie z nazwy klasy wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-170">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="feb38-171">Zwykle przypisujesz wartość do <xref:System.Exception.Message?displayProperty=nameWithType> Właściwości przez przekazanie ciągu komunikatu do `message` argumentu [konstruktora wyjątków](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="feb38-171">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="feb38-172">W przypadku zlokalizowanych aplikacji należy podać zlokalizowany ciąg komunikatu dla każdego wyjątku, który aplikacja może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="feb38-172">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="feb38-173">Pliki zasobów są używane do udostępniania zlokalizowanych komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="feb38-173">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="feb38-174">Aby uzyskać informacje na temat lokalizowania aplikacji i pobierania zlokalizowanych ciągów, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="feb38-174">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="feb38-175">Instrukcje: tworzenie wyjątków zdefiniowanych przez użytkownika z zastosowaniem zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="feb38-175">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="feb38-176">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="feb38-176">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="feb38-177">W niestandardowych wyjątkach podaj dodatkowe właściwości zgodnie z wymaganiami</span><span class="sxs-lookup"><span data-stu-id="feb38-177">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="feb38-178">Podaj dodatkowe właściwości wyjątku (oprócz niestandardowego ciągu wiadomości) tylko wtedy, gdy istnieje scenariusz programistyczny, w którym dodatkowe informacje są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="feb38-178">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="feb38-179">Na przykład <xref:System.IO.FileNotFoundException> zawiera <xref:System.IO.FileNotFoundException.FileName> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="feb38-179">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="feb38-180">Umieść instrukcje throw, aby ułatwić śledzenie stosu</span><span class="sxs-lookup"><span data-stu-id="feb38-180">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="feb38-181">Ślad stosu rozpoczyna się w instrukcji, w której wyjątek jest zgłaszany i kończąc na `catch` instrukcji, która przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="feb38-181">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="feb38-182">Korzystanie z metod konstruktora wyjątków</span><span class="sxs-lookup"><span data-stu-id="feb38-182">Use exception builder methods</span></span>

<span data-ttu-id="feb38-183">Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji.</span><span class="sxs-lookup"><span data-stu-id="feb38-183">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="feb38-184">Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają.</span><span class="sxs-lookup"><span data-stu-id="feb38-184">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="feb38-185">Przykład:</span><span class="sxs-lookup"><span data-stu-id="feb38-185">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="feb38-186">W niektórych przypadkach bardziej odpowiednie jest użycie konstruktora wyjątku do skompilowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="feb38-186">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="feb38-187">Przykładem jest globalna Klasa wyjątków, taka jak <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="feb38-187">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="feb38-188">Przywróć stan, gdy nie ukończono metod z powodu wyjątków</span><span class="sxs-lookup"><span data-stu-id="feb38-188">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="feb38-189">Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="feb38-189">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="feb38-190">Na przykład jeśli masz kod, który transferuje pieniądze przez wycofanie z jednego konta i zdeponowanie na innym koncie, a podczas wykonywania depozytu zostanie zgłoszony wyjątek, nie chcesz, aby wycofanie zadziałało.</span><span class="sxs-lookup"><span data-stu-id="feb38-190">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

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

<span data-ttu-id="feb38-191">Powyższa metoda nie generuje bezpośrednio żadnych wyjątków, ale musi być pisemnie zapisywana, aby w przypadku niepowodzenia operacji depozytu wycofanie zostało cofnięte.</span><span class="sxs-lookup"><span data-stu-id="feb38-191">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="feb38-192">Jednym ze sposobów obsługi tej sytuacji jest przechwycenie wszelkich wyjątków zgłoszonych przez transakcję przelewu i wycofanie wycofania.</span><span class="sxs-lookup"><span data-stu-id="feb38-192">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="feb38-193">Ten przykład ilustruje użycie programu `throw` w celu ponownego wygenerowania oryginalnego wyjątku, co może ułatwić wywoływanie, aby poznać rzeczywistą przyczynę problemu bez konieczności badania <xref:System.Exception.InnerException> właściwości.</span><span class="sxs-lookup"><span data-stu-id="feb38-193">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="feb38-194">Alternatywą jest zgłoszenie nowego wyjątku i uwzględnienie pierwotnego wyjątku jako wyjątku wewnętrznego:</span><span class="sxs-lookup"><span data-stu-id="feb38-194">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="feb38-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="feb38-195">See also</span></span>

- [<span data-ttu-id="feb38-196">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="feb38-196">Exceptions</span></span>](index.md)
