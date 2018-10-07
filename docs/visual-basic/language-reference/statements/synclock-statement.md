---
title: SyncLock — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: 5a931199ff8d09412d536a173f3cd12e451def64
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2018
ms.locfileid: "48845983"
---
# <a name="synclock-statement"></a><span data-ttu-id="50701-102">SyncLock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="50701-102">SyncLock Statement</span></span>
<span data-ttu-id="50701-103">Uzyskuje blokady na wyłączność dla bloku instrukcji, przed wykonaniem tego bloku.</span><span class="sxs-lookup"><span data-stu-id="50701-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50701-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50701-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="50701-105">Części</span><span class="sxs-lookup"><span data-stu-id="50701-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="50701-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="50701-106">Required.</span></span> <span data-ttu-id="50701-107">Wyrażenie, którego wynikiem jest odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="50701-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="50701-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="50701-108">Optional.</span></span> <span data-ttu-id="50701-109">Blok instrukcji, które są do wykonania, gdy jest blokada.</span><span class="sxs-lookup"><span data-stu-id="50701-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="50701-110">Kończy blok `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="50701-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50701-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50701-111">Remarks</span></span>  
 <span data-ttu-id="50701-112">`SyncLock` Instrukcji zapewnia, że wiele wątków nie wykonuje bloku instrukcji w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="50701-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="50701-113">`SyncLock` Każdy wątek uniemożliwia wprowadzanie bloku, dopóki go wykonuje nie innych wątków.</span><span class="sxs-lookup"><span data-stu-id="50701-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="50701-114">Najbardziej powszechnym zastosowaniem programu `SyncLock` jest ochrona danych przed jest aktualizowana przez więcej niż jeden wątek jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="50701-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="50701-115">Jeśli instrukcji, które manipulowania danymi muszą przejść do zakończenia bez przeszkód, umieść je wewnątrz `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="50701-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="50701-116">Blok instrukcji, chronione przez blokady na wyłączność jest czasami nazywane *sekcję krytyczną*.</span><span class="sxs-lookup"><span data-stu-id="50701-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="50701-117">reguły</span><span class="sxs-lookup"><span data-stu-id="50701-117">Rules</span></span>  
  
-   <span data-ttu-id="50701-118">Podręcznik rozgałęziania.</span><span class="sxs-lookup"><span data-stu-id="50701-118">Branching.</span></span> <span data-ttu-id="50701-119">Nie można rozgałęzić do `SyncLock` uniemożliwiaj poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="50701-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="50701-120">Wartość obiektu blokady.</span><span class="sxs-lookup"><span data-stu-id="50701-120">Lock Object Value.</span></span> <span data-ttu-id="50701-121">Wartość `lockobject` nie może być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="50701-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="50701-122">Należy utworzyć obiekt blokady, zanim użyjesz go w `SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50701-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="50701-123">Nie można zmienić wartość `lockobject` podczas wykonywania `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="50701-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="50701-124">Mechanizm wymaga, aby zablokować obiektu pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="50701-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="50701-125">Nie można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="50701-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="50701-126">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="50701-126">Behavior</span></span>  
  
-   <span data-ttu-id="50701-127">Mechanizm.</span><span class="sxs-lookup"><span data-stu-id="50701-127">Mechanism.</span></span> <span data-ttu-id="50701-128">Gdy wątek osiągnie `SyncLock` instrukcji, ocenia `lockobject` wyrażenia i zawiesza wykonywanie, dopóki nie otrzymuje blokady na wyłączność w obiekcie zwracanym przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="50701-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="50701-129">Gdy inny wątek osiągnie `SyncLock` instrukcji, go nie uzyskania blokady do momentu pierwszego wątek `End SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="50701-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="50701-130">Chronione dane.</span><span class="sxs-lookup"><span data-stu-id="50701-130">Protected Data.</span></span> <span data-ttu-id="50701-131">Jeśli `lockobject` jest `Shared` zmiennej blokady na wyłączność zapobiega wątku w żadnym wystąpieniu klasy wykonywania `SyncLock` blokowania podczas jego wykonywania innych wątków.</span><span class="sxs-lookup"><span data-stu-id="50701-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="50701-132">Chroni to dane, które jest współużytkowana przez wszystkie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50701-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="50701-133">Jeśli `lockobject` jest zmienną instance (nie `Shared`), Blokada zapobiega wątku działającego w ramach bieżącego wystąpienia wykonania `SyncLock` bloku, w tym samym czasie jako inny wątek w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="50701-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="50701-134">Chroni to danych obsługiwanych przez poszczególne wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="50701-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="50701-135">Pozyskiwanie i wersji.</span><span class="sxs-lookup"><span data-stu-id="50701-135">Acquisition and Release.</span></span> <span data-ttu-id="50701-136">A `SyncLock` blok, który zachowuje się jak `Try...Finally` konstrukcji, w którym `Try` bloku uzyskuje blokady na wyłączność w `lockobject` i `Finally` bloku zwalnia go.</span><span class="sxs-lookup"><span data-stu-id="50701-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="50701-137">W związku z tym `SyncLock` bloku gwarantuje wydanie lock, niezależnie od tego, jak zamknąć blok.</span><span class="sxs-lookup"><span data-stu-id="50701-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="50701-138">Ta zasada obowiązuje nawet w przypadku nieobsługiwanego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="50701-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="50701-139">Struktura wywołuje.</span><span class="sxs-lookup"><span data-stu-id="50701-139">Framework Calls.</span></span> <span data-ttu-id="50701-140">`SyncLock` Blok uzyskuje i zwalnia blokady na wyłączność przez wywołanie metody `Enter` i `Exit` metody `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="50701-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="50701-141">Programowanie rozwiązań</span><span class="sxs-lookup"><span data-stu-id="50701-141">Programming Practices</span></span>  
 <span data-ttu-id="50701-142">`lockobject` Wyrażenia zawsze powinna być obiekt, który należy wyłącznie do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="50701-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="50701-143">Należy zadeklarować `Private` zmiennej obiektu, aby chronić dane należące do bieżącego wystąpienia lub `Private Shared` zmiennej obiektu, aby chronić dane wspólne dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="50701-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="50701-144">Nie należy używać `Me` — słowo kluczowe, aby zapewnić blokadę dla wystąpienia obiektu danych.</span><span class="sxs-lookup"><span data-stu-id="50701-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="50701-145">Jeśli kod zewnętrzny klasy zawiera odwołanie do wystąpienia klasy, można użyć tego odwołania jako obiekt blokady dla `SyncLock` bloku zupełnie inne niż należy do Ciebie, ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="50701-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="50701-146">W ten sposób klasy i inne klasy może zablokować wzajemnie wykonanie ich niepowiązanych `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="50701-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="50701-147">Podobnie blokowania na ciąg może być problematyczne, ponieważ każdy inny kod proces, korzystając z tych samych parametrach współużytkują ten sam blokady.</span><span class="sxs-lookup"><span data-stu-id="50701-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="50701-148">Ponadto nie należy korzystać z `Me.GetType` metody w celu zapewnienia obiektu blokady dla udostępnionych danych.</span><span class="sxs-lookup"><span data-stu-id="50701-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="50701-149">Jest to spowodowane `GetType` zawsze zwraca wartość taka sama `Type` obiektu dla nazwy danej klasy.</span><span class="sxs-lookup"><span data-stu-id="50701-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="50701-150">Można wywołać kod zewnętrzny `GetType` na klasie i uzyskania tego samego obiektu blokady są używane.</span><span class="sxs-lookup"><span data-stu-id="50701-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="50701-151">Spowodowałoby to dwie klasy blokuje wzajemnie z ich `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="50701-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="50701-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="50701-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="50701-153">Opis</span><span class="sxs-lookup"><span data-stu-id="50701-153">Description</span></span>  
 <span data-ttu-id="50701-154">Poniższy przykład przedstawia klasę zawierającą prostą listę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="50701-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="50701-155">Przechowuje komunikaty w tablicy, a ostatnio używany element tablicy w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="50701-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="50701-156">`addAnotherMessage` Procedury zwiększa ostatni element i zapisuje nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="50701-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="50701-157">Te dwie operacje są chronione przez `SyncLock` i `End SyncLock` instrukcji, ponieważ po ostatnim elemencie została zwiększona, Nowa wiadomość musi być przechowywany przed innych wątków można zwiększyć po ostatnim elemencie ponownie.</span><span class="sxs-lookup"><span data-stu-id="50701-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="50701-158">Jeśli `simpleMessageList` klasy udostępnione jedną listę komunikatów między wszystkie jego wystąpienia, zmienne `messagesList` i `messagesLast` może być zadeklarowana jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="50701-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="50701-159">W tym przypadku zmienna `messagesLock` powinny być `Shared`, dzięki czemu będzie obiektem pojedynczego blokady używany przez każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="50701-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="50701-160">Kod</span><span class="sxs-lookup"><span data-stu-id="50701-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="50701-161">Opis</span><span class="sxs-lookup"><span data-stu-id="50701-161">Description</span></span>  
 <span data-ttu-id="50701-162">W poniższym przykładzie użyto wątków i `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="50701-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="50701-163">Tak długo, jak `SyncLock` instrukcji, blok instrukcji to sekcja krytycznego i `balance` nigdy nie stanie się liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="50701-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="50701-164">Możesz przekształcić w komentarz `SyncLock` i `End SyncLock` instrukcje, aby zobaczyć efekt pomijając `SyncLock` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="50701-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="50701-165">Kod</span><span class="sxs-lookup"><span data-stu-id="50701-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="50701-166">Komentarze</span><span class="sxs-lookup"><span data-stu-id="50701-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50701-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50701-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="50701-168">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="50701-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
