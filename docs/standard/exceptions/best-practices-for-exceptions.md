---
title: Najważniejsze wskazówki dotyczące wyjątków - .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 1de231b01e3fa97e78a87ae6b0595a9b5536374e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160173"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="9fa8c-102">Najważniejsze wskazówki dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-102">Best practices for exceptions</span></span>

<span data-ttu-id="9fa8c-103">Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="9fa8c-104">W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="9fa8c-105">Użyj try/catch/finally blocks, aby odzyskać od błędów lub zwolnić zasoby</span><span class="sxs-lookup"><span data-stu-id="9fa8c-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="9fa8c-106">`try` / Użyj `catch` bloków wokół kodu, który może potencjalnie wygenerować wyjątek ***i*** kod można odzyskać z tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="9fa8c-107">W `catch` blokach zawsze porządku wyjątki od najbardziej pochodnych do najmniej pochodnych.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="9fa8c-108">Wszystkie wyjątki wynikają <xref:System.Exception>z .</span><span class="sxs-lookup"><span data-stu-id="9fa8c-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="9fa8c-109">Więcej pochodnych wyjątków nie są obsługiwane przez catch klauzuli, która jest poprzedzona catch klauzuli dla klasy wyjątku podstawowego.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="9fa8c-110">Gdy kod nie można odzyskać z wyjątku, nie przechwycić tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="9fa8c-111">Włącz metody dalej stosu wywołań, aby odzyskać, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="9fa8c-112">Oczyść zasoby `using` przydzielone `finally` za pomocą instrukcji lub bloków.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="9fa8c-113">Wolisz `using` instrukcje do automatycznego oczyszczania zasobów, gdy wyjątki są generowane.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="9fa8c-114">Użyj `finally` bloków, aby oczyścić <xref:System.IDisposable>zasoby, które nie implementują .</span><span class="sxs-lookup"><span data-stu-id="9fa8c-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="9fa8c-115">Kod w `finally` klauzuli jest prawie zawsze wykonywane nawet wtedy, gdy wyjątki są generowane.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="9fa8c-116">Obsługa typowych warunków bez zgłaszania wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="9fa8c-117">W przypadku warunków, które mogą wystąpić, ale może wyzwolić wyjątek, należy rozważyć obsługę ich w sposób, który pozwoli uniknąć wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="9fa8c-118">Na przykład, jeśli spróbujesz zamknąć połączenie, które jest `InvalidOperationException`już zamknięte, otrzymasz plik .</span><span class="sxs-lookup"><span data-stu-id="9fa8c-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="9fa8c-119">Można tego uniknąć za `if` pomocą instrukcji, aby sprawdzić stan połączenia przed próbą zamknięcia go.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="9fa8c-120">Jeśli nie sprawdzić stan połączenia przed zamknięciem, `InvalidOperationException` można przechwycić wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="9fa8c-121">Metoda do wybrania zależy od tego, jak często można oczekiwać wystąpienia zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="9fa8c-122">Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="9fa8c-123">Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="9fa8c-124">Sprawdź, czy warunki błędów w kodzie, jeśli zdarzenie dzieje się rutynowo i może być uznane za część normalnego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="9fa8c-125">Podczas sprawdzania typowych warunków błędu wykonywany jest mniej kodu, ponieważ można uniknąć wyjątków.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="9fa8c-126">Klasy projektowania, dzięki czemu można uniknąć wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="9fa8c-127">Klasa może zapewnić metody lub właściwości, które umożliwiają uniknięcie wywołania, które wyzwoliłoby wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="9fa8c-128">Na przykład <xref:System.IO.FileStream> klasa zawiera metody, które pomagają określić, czy osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="9fa8c-129">Mogą one służyć do uniknięcia wyjątku, który jest generowany, jeśli czytasz poza końcem pliku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="9fa8c-130">W poniższym przykładzie pokazano, jak odczytywać na końcu pliku bez wyzwalania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="9fa8c-131">Innym sposobem uniknięcia wyjątków jest zwrócenie wartości null (lub domyślnej) dla bardzo typowych przypadków błędów zamiast zgłaszania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="9fa8c-132">Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="9fa8c-133">Zwracając null (lub domyślnie) w takich przypadkach, można zminimalizować wpływ na wydajność do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="9fa8c-134">W przypadku typów wartości, czy użyć `Nullable<T>` lub domyślnie jako wskaźnik błędu jest coś do rozważenia dla danej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="9fa8c-135">Za `Nullable<Guid>`pomocą `default` , `null` staje `Guid.Empty`się zamiast .</span><span class="sxs-lookup"><span data-stu-id="9fa8c-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="9fa8c-136">Czasami dodawanie `Nullable<T>` może uczynić go jaśniejszym, gdy wartość jest obecna lub nieobecna.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="9fa8c-137">Innym razem `Nullable<T>` dodawanie można utworzyć dodatkowe sprawy, aby sprawdzić, które nie są konieczne i służyć tylko do tworzenia potencjalnych źródeł błędów.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span>

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="9fa8c-138">Zgłaszanie wyjątków zamiast zwracania kodu błędu</span><span class="sxs-lookup"><span data-stu-id="9fa8c-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="9fa8c-139">Wyjątki upewnij się, że błędy nie pozostają niezauważone, ponieważ kod wywołujący nie sprawdzić kod zwrotny.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="9fa8c-140">Używanie wstępnie zdefiniowanych typów wyjątków .NET</span><span class="sxs-lookup"><span data-stu-id="9fa8c-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="9fa8c-141">Wprowadź nową klasę wyjątku tylko wtedy, gdy wstępnie zdefiniowana nie ma zastosowania.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="9fa8c-142">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-142">For example:</span></span>

- <span data-ttu-id="9fa8c-143">Zgłaszanie <xref:System.InvalidOperationException> wyjątku, jeśli zestaw właściwości lub wywołanie metody nie jest właściwe, biorąc pod uwagę bieżący stan obiektu.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="9fa8c-144">Zgłaszanie <xref:System.ArgumentException> wyjątku lub jednej ze wstępnie zdefiniowanych klas, które pochodzą z <xref:System.ArgumentException> jeśli są przekazywane nieprawidłowe parametry.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="9fa8c-145">Kończenie nazw klas wyjątków słowem`Exception`</span><span class="sxs-lookup"><span data-stu-id="9fa8c-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="9fa8c-146">Gdy wyjątek niestandardowy jest konieczne, należy odpowiednio nazwać <xref:System.Exception> go i wyprowadzić go z klasy.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="9fa8c-147">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="9fa8c-148">Dołącz trzy konstruktory w niestandardowych klasach wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="9fa8c-149">Użyj co najmniej trzech typowych konstruktorów podczas tworzenia własnych klas wyjątków: konstruktora bezparametrowego, konstruktora, który przyjmuje komunikat ciągu i konstruktora, który przyjmuje komunikat ciągu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-149">Use at least the three common constructors when creating your own exception classes: the parameterless constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

- <span data-ttu-id="9fa8c-150"><xref:System.Exception.%23ctor>, który używa wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

- <span data-ttu-id="9fa8c-151"><xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat ciągu.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

- <span data-ttu-id="9fa8c-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat ciągu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="9fa8c-153">Na przykład zobacz [Jak: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="9fa8c-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="9fa8c-154">Upewnij się, że dane wyjątku są dostępne, gdy kod jest wykonywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="9fa8c-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="9fa8c-155">Podczas tworzenia wyjątków zdefiniowanych przez użytkownika upewnij się, że metadane wyjątków są dostępne dla kodu, który jest wykonywany zdalnie.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="9fa8c-156">Na przykład w implementacjach .NET, które obsługują domeny aplikacji, mogą wystąpić wyjątki w domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="9fa8c-157">Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod, który zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="9fa8c-158">Dla domeny aplikacji A poprawnie złapać i obsługiwać wyjątek, musi być w stanie znaleźć zestaw, który zawiera wyjątek zgłoszony przez domenę aplikacji B. Jeśli domena aplikacji B zgłasza wyjątek, który znajduje się w zestawie w ramach jego bazy aplikacji, ale nie w ramach bazy aplikacji domeny aplikacji <xref:System.IO.FileNotFoundException> A, domena aplikacji A nie będzie mógł znaleźć wyjątek, a czas wykonywania języka wspólnego spowoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="9fa8c-159">Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="9fa8c-160">Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="9fa8c-161">\-lub -</span><span class="sxs-lookup"><span data-stu-id="9fa8c-161">\- or -</span></span>

- <span data-ttu-id="9fa8c-162">Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="9fa8c-163">Używanie komunikatów o błędach poprawne gramatycznie</span><span class="sxs-lookup"><span data-stu-id="9fa8c-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="9fa8c-164">Napisz jasne zdania i dołącz końcową interpunkcję.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="9fa8c-165">Każde zdanie w ciągu przypisanym do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości powinno zakończyć się kropką.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="9fa8c-166">Na przykład "Tabela dziennika została przepełniona."</span><span class="sxs-lookup"><span data-stu-id="9fa8c-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="9fa8c-167">będzie odpowiedni ciąg komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="9fa8c-168">Dołączanie zlokalizowanej wiadomości ciągu w każdym wyjątku</span><span class="sxs-lookup"><span data-stu-id="9fa8c-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="9fa8c-169">Komunikat o błędzie, który widzi <xref:System.Exception.Message?displayProperty=nameWithType> użytkownik pochodzi od właściwości wyjątku, który został zgłoszony, a nie od nazwy klasy wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="9fa8c-170">Zazwyczaj można przypisać wartość do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości, przekazując ciąg `message` komunikatu do argumentu [konstruktora wyjątku](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="9fa8c-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="9fa8c-171">W przypadku zlokalizowanych aplikacji należy podać zlokalizowany ciąg komunikatów dla każdego wyjątku, który aplikacja może zgłosić.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="9fa8c-172">Pliki zasobów służy do dostarczania zlokalizowanych komunikatów o błędach.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="9fa8c-173">Aby uzyskać informacje na temat lokalizowania aplikacji i pobierania zlokalizowanych ciągów, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-173">For information on localizing applications and retrieving localized strings, see the following articles:</span></span>

- [<span data-ttu-id="9fa8c-174">Instrukcje: tworzenie wyjątków zdefiniowanych przez użytkownika z zastosowaniem zlokalizowanych komunikatów o wyjątkach</span><span class="sxs-lookup"><span data-stu-id="9fa8c-174">How to: create user-defined exceptions with localized exception messages</span></span>](how-to-create-localized-exception-messages.md)
- [<span data-ttu-id="9fa8c-175">Zasoby w aplikacjach klasycznych</span><span class="sxs-lookup"><span data-stu-id="9fa8c-175">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
- <xref:System.Resources.ResourceManager?displayProperty=nameWithType>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="9fa8c-176">W wyjątkach niestandardowych podaj dodatkowe właściwości zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="9fa8c-176">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="9fa8c-177">Podaj dodatkowe właściwości dla wyjątku (oprócz niestandardowego ciągu komunikatu) tylko wtedy, gdy istnieje scenariusz programowy, w którym przydatne są dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-177">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="9fa8c-178">Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwość.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-178">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="9fa8c-179">Umieść instrukcje throw, aby śledzenie stosu było pomocne</span><span class="sxs-lookup"><span data-stu-id="9fa8c-179">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="9fa8c-180">Śledzenie stosu rozpoczyna się od instrukcji, `catch` gdzie wyjątek jest zgłaszany i kończy się na instrukcji, która przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-180">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="9fa8c-181">Używanie metod konstruktowania wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-181">Use exception builder methods</span></span>

<span data-ttu-id="9fa8c-182">Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-182">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="9fa8c-183">Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-183">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="9fa8c-184">Przykład:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-184">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](~/samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="9fa8c-185">W niektórych przypadkach jest bardziej odpowiednie do użycia konstruktora wyjątku do tworzenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-185">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="9fa8c-186">Przykładem jest klasa wyjątków <xref:System.ArgumentException>globalnych, takich jak .</span><span class="sxs-lookup"><span data-stu-id="9fa8c-186">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="9fa8c-187">Przywracanie stanu, gdy metody nie są ukończone z powodu wyjątków</span><span class="sxs-lookup"><span data-stu-id="9fa8c-187">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="9fa8c-188">Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-188">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="9fa8c-189">Na przykład, jeśli masz kod, który przelewa pieniądze, wypłacając pieniądze z jednego konta i deponując na innym koncie, a podczas wykonywania wpłaty pojawia się wyjątek, nie chcesz, aby wypłata pozostała w mocy.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-189">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

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

<span data-ttu-id="9fa8c-190">Powyższa metoda nie powoduje bezpośrednio żadnych wyjątków, ale musi być napisana defensywnie, aby w przypadku niepowodzenia operacji wpłaty wycofanie zostało odwrócone.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-190">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="9fa8c-191">Jednym ze sposobów radzenia sobie z tą sytuacją jest złapanie wszelkich wyjątków zgłoszonych przez transakcję wpłaty i wycofanie wypłaty.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-191">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="9fa8c-192">W tym przykładzie przedstawiono `throw` użycie do ponownego zgłosić oryginalny wyjątek, który może ułatwić wywołujących, aby zobaczyć <xref:System.Exception.InnerException> rzeczywistą przyczynę problemu bez konieczności badania właściwości.</span><span class="sxs-lookup"><span data-stu-id="9fa8c-192">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="9fa8c-193">Alternatywą jest zgłosić nowy wyjątek i dołączyć oryginalny wyjątek jako wyjątek wewnętrzny:</span><span class="sxs-lookup"><span data-stu-id="9fa8c-193">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9fa8c-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fa8c-194">See also</span></span>

- [<span data-ttu-id="9fa8c-195">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="9fa8c-195">Exceptions</span></span>](index.md)
