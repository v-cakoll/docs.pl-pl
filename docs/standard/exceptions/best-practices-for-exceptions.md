---
title: Najlepsze praktyki dotyczące wyjątków — .NET
ms.date: 12/05/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- exceptions, best practices
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
ms.openlocfilehash: 752a7e5233d8b1d88b49be450972fc964f82d2c4
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690658"
---
# <a name="best-practices-for-exceptions"></a><span data-ttu-id="48ac4-102">Najlepsze praktyki dotyczące wyjątków</span><span class="sxs-lookup"><span data-stu-id="48ac4-102">Best practices for exceptions</span></span>

<span data-ttu-id="48ac4-103">Dobrze zaprojektowana aplikacja obsługuje wyjątki i błędy, aby zapobiegać awariom aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-103">A well-designed app handles exceptions and errors to prevent app crashes.</span></span> <span data-ttu-id="48ac4-104">W tej sekcji opisano najlepsze rozwiązania dotyczące obsługi i tworzenia wyjątków.</span><span class="sxs-lookup"><span data-stu-id="48ac4-104">This section describes best practices for handling and creating exceptions.</span></span>

## <a name="use-trycatchfinally-blocks-to-recover-from-errors-or-release-resources"></a><span data-ttu-id="48ac4-105">Bloki try/catch/finally umożliwia odzyskiwanie w razie błędów lub zwolnienia zasobów</span><span class="sxs-lookup"><span data-stu-id="48ac4-105">Use try/catch/finally blocks to recover from errors or release resources</span></span>

<span data-ttu-id="48ac4-106">Użyj `try` / `catch` bloki wokół kodu, który potencjalnie może generować wyjątek ***i*** kodu można odzyskać z tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-106">Use `try`/`catch` blocks around code that can potentially generate an exception ***and*** your code can recover from that exception.</span></span> <span data-ttu-id="48ac4-107">W `catch` blokuje zawsze porządkować wyjątki od najbardziej pochodnej do najmniej pochodnego.</span><span class="sxs-lookup"><span data-stu-id="48ac4-107">In `catch` blocks, always order exceptions from the most derived to the least derived.</span></span> <span data-ttu-id="48ac4-108">Wszystkie wyjątki pochodzić od <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="48ac4-108">All exceptions derive from <xref:System.Exception>.</span></span> <span data-ttu-id="48ac4-109">Bardziej pochodnego wyjątki nie są obsługiwane przez klauzuli catch, który jest poprzedzona klauzulą catch dla klasy bazowej wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-109">More derived exceptions are not handled by a catch clause that is preceded by a catch clause for a base exception class.</span></span> <span data-ttu-id="48ac4-110">Gdy kodu nie można odzyskać z wyjątku, nie Złap, ten wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-110">When your code cannot recover from an exception, don't catch that exception.</span></span> <span data-ttu-id="48ac4-111">Włącz metody dalsze górę stosu wywołań, aby odzyskać, jeśli jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="48ac4-111">Enable methods further up the call stack to recover if possible.</span></span>

<span data-ttu-id="48ac4-112">Czyszczenie zasobów przydzielonych z oboma `using` instrukcji lub `finally` bloków.</span><span class="sxs-lookup"><span data-stu-id="48ac4-112">Clean up resources allocated with either `using` statements, or `finally` blocks.</span></span> <span data-ttu-id="48ac4-113">Preferuj `using` instrukcji, aby automatycznie wyczyścić zasoby, gdy wyjątki zostaną zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="48ac4-113">Prefer `using` statements to automatically clean up resources when exceptions are thrown.</span></span> <span data-ttu-id="48ac4-114">Użyj `finally` bloków, aby wyczyścić zasoby, które nie implementują <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="48ac4-114">Use `finally` blocks to clean up resources that don't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="48ac4-115">Możesz pisać kod w `finally` klauzuli prawie zawsze jest wykonywane, nawet wtedy, gdy wyjątki zostaną zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="48ac4-115">Code in a `finally` clause is almost always executed even when exceptions are thrown.</span></span>

## <a name="handle-common-conditions-without-throwing-exceptions"></a><span data-ttu-id="48ac4-116">Obsługa typowe warunki bez zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="48ac4-116">Handle common conditions without throwing exceptions</span></span>

<span data-ttu-id="48ac4-117">Warunki, które mogą wystąpić, ale może być wywołanie wyjątku, należy wziąć pod uwagę ich obsługę w sposób, który pozwoli uniknąć wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-117">For conditions that are likely to occur but might trigger an exception, consider handling them in a way that will avoid the exception.</span></span> <span data-ttu-id="48ac4-118">Na przykład, jeśli użytkownik próbuje zamknąć połączenie, które jest już zamknięty, uzyskasz `InvalidOperationException`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-118">For example, if you try to close a connection that is already closed, you'll get an `InvalidOperationException`.</span></span> <span data-ttu-id="48ac4-119">Można uniknąć, za pomocą `if` instrukcję, aby sprawdzić stan połączenia przed podjęciem próby je zamknąć.</span><span class="sxs-lookup"><span data-stu-id="48ac4-119">You can avoid that by using an `if` statement to check the connection state before trying to close it.</span></span>

[!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
[!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
[!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]

<span data-ttu-id="48ac4-120">Jeśli nie możesz sprawdzić stan połączenia przed zamknięciem, możesz przechwytywać `InvalidOperationException` wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-120">If you don't check connection state before closing, you can catch the `InvalidOperationException` exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
[!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
[!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]

<span data-ttu-id="48ac4-121">Metoda wyboru zależy od tego, jak często oczekuje się wystąpienia danego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="48ac4-121">The method to choose depends on how often you expect the event to occur.</span></span>

- <span data-ttu-id="48ac4-122">Obsługi wyjątków należy używać, jeśli zdarzenie nie występuje zbyt często, a więc jeśli zdarzenie jest naprawdę wyjątkowe i wskazuje błąd, taki jak nieoczekiwany koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-122">Use exception handling if the event doesn't occur very often, that is, if the event is truly exceptional and indicates an error (such as an unexpected end-of-file).</span></span> <span data-ttu-id="48ac4-123">Użycie obsługi wyjątków powoduje, że mniej kodu jest wykonywanego w normalnych warunkach.</span><span class="sxs-lookup"><span data-stu-id="48ac4-123">When you use exception handling, less code is executed in normal conditions.</span></span>

- <span data-ttu-id="48ac4-124">Wyszukaj warunki błędów w kodzie, jeśli zdarzenie występuje często i może być traktowane jako część normalnego wykonywania.</span><span class="sxs-lookup"><span data-stu-id="48ac4-124">Check for error conditions in code if the event happens routinely and could be considered part of normal execution.</span></span> <span data-ttu-id="48ac4-125">Podczas sprawdzania dostępności typowe warunki błędów, mniej kodu jest wykonywanego, ponieważ pozwala uniknąć wyjątków.</span><span class="sxs-lookup"><span data-stu-id="48ac4-125">When you check for common error conditions, less code is executed because you avoid exceptions.</span></span>

## <a name="design-classes-so-that-exceptions-can-be-avoided"></a><span data-ttu-id="48ac4-126">Klasy należy projektować, dzięki czemu można uniknąć wyjątków</span><span class="sxs-lookup"><span data-stu-id="48ac4-126">Design classes so that exceptions can be avoided</span></span>

<span data-ttu-id="48ac4-127">Klasa może zapewnić metody lub właściwości, które pozwalają uniknąć nawiązywania połączenia, które będą wyzwalać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-127">A class can provide methods or properties that enable you to avoid making a call that would trigger an exception.</span></span> <span data-ttu-id="48ac4-128">Na przykład <xref:System.IO.FileStream> klasa dostarcza metody pomagające ustalić, czy osiągnięto koniec pliku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-128">For example, a <xref:System.IO.FileStream> class provides methods that help determine whether the end of the file has been reached.</span></span> <span data-ttu-id="48ac4-129">Mogą one używane w celu uniknięcia wyjątek, który jest zgłaszany w przypadku odczytu poza końcem pliku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-129">These can be used to avoid the exception that is thrown if you read past the end of the file.</span></span> <span data-ttu-id="48ac4-130">Poniższy przykład pokazuje, jak wykonać Odczyt do końca pliku bez powodowania wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-130">The following example shows how to read to the end of a file without triggering an exception.</span></span>

[!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
[!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
[!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]

<span data-ttu-id="48ac4-131">Innym sposobem na uniknięcie wyjątków jest do zwrócenia wartości null (lub domyślny) dla ekstremalnie częstych przypadków błędów zamiast zgłaszać wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-131">Another way to avoid exceptions is to return null (or default) for extremely common error cases instead of throwing an exception.</span></span> <span data-ttu-id="48ac4-132">Ekstremalnie częste przypadki błędów należy traktować jako normalny przepływ sterowania.</span><span class="sxs-lookup"><span data-stu-id="48ac4-132">An extremely common error case can be considered normal flow of control.</span></span> <span data-ttu-id="48ac4-133">Przez zwrócenie wartości null (lub domyślny) w tych przypadkach, można zminimalizować wpływ na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-133">By returning null (or default) in these cases, you minimize the performance impact to an app.</span></span>

<span data-ttu-id="48ac4-134">Dla typów wartości czy ma być używany `Nullable<T>` lub wartości domyślnych, ponieważ wskaźnik błędów jest coś, co należy wziąć pod uwagę dla określonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-134">For value types, whether to use `Nullable<T>` or default as your error indicator is something to consider for your particular app.</span></span> <span data-ttu-id="48ac4-135">Za pomocą `Nullable<Guid>`, `default` staje się `null` zamiast `Guid.Empty`.</span><span class="sxs-lookup"><span data-stu-id="48ac4-135">By using `Nullable<Guid>`, `default` becomes `null` instead of `Guid.Empty`.</span></span> <span data-ttu-id="48ac4-136">Dodając kilka razy `Nullable<T>` może spowodować przejrzyste gdy wartość jest obecne lub nieobecne.</span><span class="sxs-lookup"><span data-stu-id="48ac4-136">Some times, adding `Nullable<T>` can make it clearer when a value is present or absent.</span></span> <span data-ttu-id="48ac4-137">Innym razem, dodając `Nullable<T>` można tworzyć dodatkowe przypadki, upewnij się, że nie są niezbędne w celu tylko służą do tworzenia potencjalnymi przyczynami błędów.</span><span class="sxs-lookup"><span data-stu-id="48ac4-137">Other times, adding `Nullable<T>` can create extra cases to check that aren't necessary, and only serve to create potential sources of errors.</span></span> 

## <a name="throw-exceptions-instead-of-returning-an-error-code"></a><span data-ttu-id="48ac4-138">Zgłaszają wyjątki, zamiast zwracać kod błędu:</span><span class="sxs-lookup"><span data-stu-id="48ac4-138">Throw exceptions instead of returning an error code</span></span>

<span data-ttu-id="48ac4-139">Wyjątki upewnij się, że awarie nie niezauważone ponieważ wywołanie kodu nie Sprawdź kod powrotny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-139">Exceptions ensure that failures do not go unnoticed because calling code didn't check a return code.</span></span>

## <a name="use-the-predefined-net-exception-types"></a><span data-ttu-id="48ac4-140">Użyj wstępnie zdefiniowanych typów wyjątków platformy .NET</span><span class="sxs-lookup"><span data-stu-id="48ac4-140">Use the predefined .NET exception types</span></span>

<span data-ttu-id="48ac4-141">Wprowadzenie nowej klasy wyjątku tylko wtedy, gdy nie ma zastosowania jednego wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="48ac4-141">Introduce a new exception class only when a predefined one doesn't apply.</span></span> <span data-ttu-id="48ac4-142">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="48ac4-142">For example:</span></span>

- <span data-ttu-id="48ac4-143">Throw <xref:System.InvalidOperationException> wyjątek, jeśli właściwość zestawu lub wywołanie metody nie jest odpowiednie bieżącego stanu obiektu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-143">Throw an <xref:System.InvalidOperationException> exception if a property set or method call is not appropriate given the object's current state.</span></span>

- <span data-ttu-id="48ac4-144">Throw <xref:System.ArgumentException> wyjątku lub jeden z wstępnie zdefiniowanych klas, które wynikają z <xref:System.ArgumentException> Jeśli zostaną przekazane nieprawidłowe parametry.</span><span class="sxs-lookup"><span data-stu-id="48ac4-144">Throw an <xref:System.ArgumentException> exception or one of the predefined classes that derive from <xref:System.ArgumentException> if invalid parameters are passed.</span></span>

## <a name="end-exception-class-names-with-the-word-exception"></a><span data-ttu-id="48ac4-145">Nazwy klas wyjątków koniec wyrazu `Exception`</span><span class="sxs-lookup"><span data-stu-id="48ac4-145">End exception class names with the word `Exception`</span></span>

<span data-ttu-id="48ac4-146">Gdy konieczne jest niestandardowy wyjątek, nadaj mu nazwę odpowiednio i pochodzić z <xref:System.Exception> klasy.</span><span class="sxs-lookup"><span data-stu-id="48ac4-146">When a custom exception is necessary, name it appropriately and derive it from the <xref:System.Exception> class.</span></span> <span data-ttu-id="48ac4-147">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="48ac4-147">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
[!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
[!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]

## <a name="include-three-constructors-in-custom-exception-classes"></a><span data-ttu-id="48ac4-148">Obejmują trzy konstruktory w klasach niestandardowy wyjątek</span><span class="sxs-lookup"><span data-stu-id="48ac4-148">Include three constructors in custom exception classes</span></span>

<span data-ttu-id="48ac4-149">Użyj co najmniej trzech typowych konstruktorów, podczas tworzenia własnych klas wyjątków: konstruktora domyślnego, konstruktora przyjmującego komunikat w formacie ciągu oraz konstruktora przyjmującego komunikat w formacie ciągu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-149">Use at least the three common constructors when creating your own exception classes: the default constructor, a constructor that takes a string message, and a constructor that takes a string message and an inner exception.</span></span>

* <span data-ttu-id="48ac4-150"><xref:System.Exception.%23ctor>, który używa wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="48ac4-150"><xref:System.Exception.%23ctor>, which uses default values.</span></span>

* <span data-ttu-id="48ac4-151"><xref:System.Exception.%23ctor%28System.String%29>, który akceptuje komunikat w formacie ciągu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-151"><xref:System.Exception.%23ctor%28System.String%29>, which accepts a string message.</span></span>

* <span data-ttu-id="48ac4-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, który akceptuje komunikat w formacie ciągu i wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="48ac4-152"><xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, which accepts a string message and an inner exception.</span></span>

<span data-ttu-id="48ac4-153">Aby uzyskać przykład, zobacz [jak: Tworzenie wyjątków zdefiniowanych przez użytkownika](how-to-create-user-defined-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="48ac4-153">For an example, see [How to: Create User-Defined Exceptions](how-to-create-user-defined-exceptions.md).</span></span>

## <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a><span data-ttu-id="48ac4-154">Upewnij się, że wyjątku jest dostępny, gdy kod jest wykonywany zdalnie</span><span class="sxs-lookup"><span data-stu-id="48ac4-154">Ensure that exception data is available when code executes remotely</span></span>

<span data-ttu-id="48ac4-155">Podczas tworzenia wyjątków zdefiniowanych przez użytkownika, upewnij się, że metadane dla wyjątków dostępne dla zdalnie wykonywanego kodu.</span><span class="sxs-lookup"><span data-stu-id="48ac4-155">When you create user-defined exceptions, ensure that the metadata for the exceptions is available to code that is executing remotely.</span></span>

<span data-ttu-id="48ac4-156">Na przykład dotyczącej implementacji platformy .NET, które obsługują domen aplikacji, wyjątki mogą wystąpić w domenach aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-156">For example, on .NET implementations that support App Domains, exceptions may occur across App domains.</span></span> <span data-ttu-id="48ac4-157">Załóżmy, że domena aplikacji A tworzy domenę aplikacji B, która wykonuje kod zgłaszający wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-157">Suppose App Domain A creates App Domain B, which executes code that throws an exception.</span></span> <span data-ttu-id="48ac4-158">Aby domena aplikacji A mogła poprawnie przechwycić i obsłużyć wyjątek musi być w stanie znaleźć zestaw zawierający wyjątek zgłaszany przez domenę aplikacji B. Jeśli domena aplikacji B zgłosi wyjątek, który jest zawarty w zestawie, do jej podstawy aplikacji, ale nie w ramach podstawy aplikacji domeny aplikacji A, domena aplikacji A nie będzie można znaleźć wyjątku i środowisko uruchomieniowe języka wspólnego zgłosi <xref:System.IO.FileNotFoundException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-158">For App Domain A to properly catch and handle the exception, it must be able to find the assembly that contains the exception thrown by App Domain B. If App Domain B throws an exception that is contained in an assembly under its application base, but not under App Domain A's application base, App Domain A will not be able to find the exception, and the common language runtime will throw a <xref:System.IO.FileNotFoundException> exception.</span></span> <span data-ttu-id="48ac4-159">Aby uniknąć tej sytuacji, można na dwa sposoby wdrożyć zestaw zawierający informacje o wyjątku:</span><span class="sxs-lookup"><span data-stu-id="48ac4-159">To avoid this situation, you can deploy the assembly that contains the exception information in two ways:</span></span>

- <span data-ttu-id="48ac4-160">Umieszczając zestaw we wspólnej podstawie aplikacji współużytkowanej przez obie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-160">Put the assembly into a common application base shared by both app domains.</span></span>

    <span data-ttu-id="48ac4-161">\- lub —</span><span class="sxs-lookup"><span data-stu-id="48ac4-161">\- or -</span></span>

- <span data-ttu-id="48ac4-162">Jeśli domeny nie współużytkują podstawy aplikacji, można podpisać zestaw zawierający informacje o wyjątku, używając silnej nazwy, i wdrożyć ten zestaw w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="48ac4-162">If the domains do not share a common application base, sign the assembly that contains the exception information with a strong name and deploy the assembly into the global assembly cache.</span></span>

## <a name="use-grammatically-correct-error-messages"></a><span data-ttu-id="48ac4-163">Używać poprawnych gramatycznie komunikatów</span><span class="sxs-lookup"><span data-stu-id="48ac4-163">Use grammatically correct error messages</span></span>

<span data-ttu-id="48ac4-164">Pisz wyczyść zdania i obejmują kończące znaki interpunkcyjne.</span><span class="sxs-lookup"><span data-stu-id="48ac4-164">Write clear sentences and include ending punctuation.</span></span> <span data-ttu-id="48ac4-165">Każde zdanie w ciągu przypisane do <xref:System.Exception.Message?displayProperty=nameWithType> właściwość powinien kończyć się kropką.</span><span class="sxs-lookup"><span data-stu-id="48ac4-165">Each sentence in the string assigned to the <xref:System.Exception.Message?displayProperty=nameWithType> property should end in a period.</span></span> <span data-ttu-id="48ac4-166">Na przykład "przepełnienie tabeli dziennika."</span><span class="sxs-lookup"><span data-stu-id="48ac4-166">For example, "The log table has overflowed."</span></span> <span data-ttu-id="48ac4-167">może być ciągiem odpowiedni komunikat.</span><span class="sxs-lookup"><span data-stu-id="48ac4-167">would be an appropriate message string.</span></span>

## <a name="include-a-localized-string-message-in-every-exception"></a><span data-ttu-id="48ac4-168">Uwzględnij wiadomość zlokalizowany ciąg do każdego wyjątku</span><span class="sxs-lookup"><span data-stu-id="48ac4-168">Include a localized string message in every exception</span></span>

<span data-ttu-id="48ac4-169">Komunikat o błędzie widziany przez użytkownika jest tworzony na podstawie <xref:System.Exception.Message?displayProperty=nameWithType> właściwości wyjątku, który został zgłoszony, a nie od nazwy klasy wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-169">The error message that the user sees is derived from the <xref:System.Exception.Message?displayProperty=nameWithType> property of the exception that was thrown, and not from the name of the exception class.</span></span> <span data-ttu-id="48ac4-170">Zazwyczaj przypisanie wartości do <xref:System.Exception.Message?displayProperty=nameWithType> właściwości, przekazując ciąg wiadomości do `message` argument [konstruktora wyjątków](xref:System.Exception.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="48ac4-170">Typically, you assign a value to the <xref:System.Exception.Message?displayProperty=nameWithType>  property by passing the message string to the `message` argument of an [Exception constructor](xref:System.Exception.%23ctor%2A).</span></span>

<span data-ttu-id="48ac4-171">W przypadku zlokalizowanych aplikacji należy Podaj ciąg zlokalizowany komunikat każdy wyjątek, który może zgłosić aplikacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-171">For localized applications, you should provide a localized message string for every exception that your application can throw.</span></span> <span data-ttu-id="48ac4-172">Pliki zasobów umożliwia zapewniają lokalizowane komunikaty o błędzie.</span><span class="sxs-lookup"><span data-stu-id="48ac4-172">You use resource files to provide localized error messages.</span></span> <span data-ttu-id="48ac4-173">Informacje na temat lokalizowanie aplikacji i pobieranie zlokalizowanych ciągów, zobacz [zasoby w aplikacjach pulpitu](../../framework/resources/index.md) i <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="48ac4-173">For information on localizing applications and retrieving localized strings, see [Resources in Desktop Apps](../../framework/resources/index.md) and <xref:System.Resources.ResourceManager?displayProperty=nameWithType>.</span></span>

## <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a><span data-ttu-id="48ac4-174">Niestandardowe wyjątki zapewniają dodatkowe właściwości, zgodnie z potrzebami</span><span class="sxs-lookup"><span data-stu-id="48ac4-174">In custom exceptions, provide additional properties as needed</span></span>

<span data-ttu-id="48ac4-175">Podaj dodatkowe właściwości, dla wyjątku (oprócz ciąg niestandardowy komunikat) tylko wtedy, gdy istnieje scenariusz programowy, w których jest użyteczny dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="48ac4-175">Provide additional properties for an exception (in addition to the custom message string) only when there's a programmatic scenario where the additional information is useful.</span></span> <span data-ttu-id="48ac4-176">Na przykład <xref:System.IO.FileNotFoundException> zapewnia <xref:System.IO.FileNotFoundException.FileName> właściwości.</span><span class="sxs-lookup"><span data-stu-id="48ac4-176">For example, the <xref:System.IO.FileNotFoundException> provides the <xref:System.IO.FileNotFoundException.FileName> property.</span></span>

## <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a><span data-ttu-id="48ac4-177">Umieść throw — instrukcje, aby ślad stosu okaże się pomocna</span><span class="sxs-lookup"><span data-stu-id="48ac4-177">Place throw statements so that the stack trace will be helpful</span></span>

<span data-ttu-id="48ac4-178">Ślad stosu zaczyna się od instrukcji, gdy wyjątek jest wyrzucany i kończy się na `catch` instrukcję, która przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="48ac4-178">The stack trace begins at the statement where the exception is thrown and ends at the `catch` statement that catches the exception.</span></span>

## <a name="use-exception-builder-methods"></a><span data-ttu-id="48ac4-179">Używać metod konstruktora wyjątków</span><span class="sxs-lookup"><span data-stu-id="48ac4-179">Use exception builder methods</span></span>

<span data-ttu-id="48ac4-180">Klasy często zgłaszają takie same wyjątki z różnych miejsc w swojej implementacji.</span><span class="sxs-lookup"><span data-stu-id="48ac4-180">It is common for a class to throw the same exception from different places in its implementation.</span></span> <span data-ttu-id="48ac4-181">Aby uniknąć nadmiernej ilości kodu, należy używać metod pomocników, które tworzą wyjątki i je zwracają.</span><span class="sxs-lookup"><span data-stu-id="48ac4-181">To avoid excessive code, use helper methods that create the exception and return it.</span></span> <span data-ttu-id="48ac4-182">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="48ac4-182">For example:</span></span>

[!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
[!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
[!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]

<span data-ttu-id="48ac4-183">W niektórych przypadkach jest bardziej odpowiednie użycie konstruktora wyjątków w celu utworzenia wyjątku.</span><span class="sxs-lookup"><span data-stu-id="48ac4-183">In some cases, it's more appropriate to use the exception's constructor to build the exception.</span></span> <span data-ttu-id="48ac4-184">Przykładem jest klasą globalnych <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="48ac4-184">An example is a global exception class such as <xref:System.ArgumentException>.</span></span>

## <a name="restore-state-when-methods-dont-complete-due-to-exceptions"></a><span data-ttu-id="48ac4-185">Przywracanie stanu, gdy metody nie zakończą się z powodu wyjątków</span><span class="sxs-lookup"><span data-stu-id="48ac4-185">Restore state when methods don't complete due to exceptions</span></span>

<span data-ttu-id="48ac4-186">Obiekty wywołujące powinny być w stanie założyć, że nie występują efekty uboczne, gdy wyjątek jest zgłaszany przez metodę.</span><span class="sxs-lookup"><span data-stu-id="48ac4-186">Callers should be able to assume that there are no side effects when an exception is thrown from a method.</span></span> <span data-ttu-id="48ac4-187">Na przykład jeśli kod, który przesyła pieniądze wycofania z jednego konta, a zdeponowanie na innym koncie, a wyjątek jest zgłaszany podczas wykonywania złożenia, nie chcesz wycofania do obowiązywać.</span><span class="sxs-lookup"><span data-stu-id="48ac4-187">For example, if you have code that transfers money by withdrawing from one account and depositing in another account, and an exception is thrown while executing the deposit, you don't want the withdrawal to remain in effect.</span></span>

```csharp
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect.
    to.Deposit(amount);
}
```

<span data-ttu-id="48ac4-188">Powyższej metody bezpośrednio nie generuje żadnych wyjątków, ale musi być pamiętać o napisana tak, aby w przypadku niepowodzenia operacji złożenia wycofanie została odwrócona.</span><span class="sxs-lookup"><span data-stu-id="48ac4-188">The method above does not directly throw any exceptions, but must be written defensively so that if the deposit operation fails, the withdrawal is reversed.</span></span>

<span data-ttu-id="48ac4-189">Jednym ze sposobów, aby obsłużyć taką sytuację jest przechwytywać wyjątki zgłaszane przez transakcję depozytu i wycofać wycofania.</span><span class="sxs-lookup"><span data-stu-id="48ac4-189">One way to handle this situation is to catch any exceptions thrown by the deposit transaction and roll back the withdrawal.</span></span>

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

<span data-ttu-id="48ac4-190">Ten przykład ilustruje użycie `throw` ponownie zgłosić oryginalny wyjątek, który może ułatwić aby wywołujący mogli zobaczyć przyczyny rzeczywistego problemu bez konieczności zbadać <xref:System.Exception.InnerException> właściwości.</span><span class="sxs-lookup"><span data-stu-id="48ac4-190">This example illustrates the use of `throw` to re-throw the original exception, which can make it easier for callers to see the real cause of the problem without having to examine the <xref:System.Exception.InnerException> property.</span></span> <span data-ttu-id="48ac4-191">Alternatywą jest nowy wyjątku i obejmują oryginalnego wyjątku, ponieważ wyjątek wewnętrzny:</span><span class="sxs-lookup"><span data-stu-id="48ac4-191">An alternative is to throw a new exception and include the original exception as the inner exception:</span></span>

```csharp
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new TransferFundsException("Withdrawal failed", innerException: ex)
    {
        From = from,
        To = to,
        Amount = amount
    };
}
```

## <a name="see-also"></a><span data-ttu-id="48ac4-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="48ac4-192">See also</span></span>

- [<span data-ttu-id="48ac4-193">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="48ac4-193">Exceptions</span></span>](index.md)
