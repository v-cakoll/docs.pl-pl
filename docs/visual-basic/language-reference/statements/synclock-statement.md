---
title: SyncLock — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
ms.openlocfilehash: fd932a20af274faf2b56136a94675b28399989b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404164"
---
# <a name="synclock-statement"></a><span data-ttu-id="06f52-102">SyncLock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="06f52-102">SyncLock Statement</span></span>
<span data-ttu-id="06f52-103">Uzyskuje blokadę na wyłączność dla bloku instrukcji przed wykonaniem bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06f52-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06f52-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="06f52-105">Części</span><span class="sxs-lookup"><span data-stu-id="06f52-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="06f52-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="06f52-106">Required.</span></span> <span data-ttu-id="06f52-107">Wyrażenie, którego wynikiem jest odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="06f52-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="06f52-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="06f52-108">Optional.</span></span> <span data-ttu-id="06f52-109">Blok instrukcji, które mają zostać wykonane po pozyskaniu blokady.</span><span class="sxs-lookup"><span data-stu-id="06f52-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="06f52-110">Kończy `SyncLock` blok.</span><span class="sxs-lookup"><span data-stu-id="06f52-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06f52-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06f52-111">Remarks</span></span>  
 <span data-ttu-id="06f52-112">`SyncLock`Instrukcja zapewnia, że wiele wątków nie wykonuje w tym samym czasie bloku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="06f52-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="06f52-113">`SyncLock`zapobiega wprowadzaniu bloku przez każdy wątek do momentu wykonania innego wątku.</span><span class="sxs-lookup"><span data-stu-id="06f52-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="06f52-114">Najbardziej typowym zastosowaniem `SyncLock` jest ochrona danych przed aktualizacją przez więcej niż jeden wątek jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="06f52-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="06f52-115">Jeśli instrukcje dotyczące manipulowania danymi muszą przejść do zakończenia bez zakłóceń, umieścić je wewnątrz `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="06f52-116">Blok instrukcji chroniony przez blokadę wyłączną jest czasami nazywany *sekcją krytyczną*.</span><span class="sxs-lookup"><span data-stu-id="06f52-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="06f52-117">Reguły</span><span class="sxs-lookup"><span data-stu-id="06f52-117">Rules</span></span>  
  
- <span data-ttu-id="06f52-118">Rozgałęzianie.</span><span class="sxs-lookup"><span data-stu-id="06f52-118">Branching.</span></span> <span data-ttu-id="06f52-119">Nie można rozgałęzić `SyncLock` bloku spoza bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="06f52-120">Wartość blokady obiektu.</span><span class="sxs-lookup"><span data-stu-id="06f52-120">Lock Object Value.</span></span> <span data-ttu-id="06f52-121">Wartość `lockobject` nie może być `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="06f52-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="06f52-122">Należy utworzyć obiekt blokady przed użyciem go w `SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="06f52-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="06f52-123">Nie można zmienić wartości `lockobject` podczas wykonywania `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="06f52-124">Mechanizm wymaga, aby obiekt blokady pozostał niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="06f52-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="06f52-125">Nie można użyć operatora [await](../operators/await-operator.md) w `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-125">You can't use the [Await](../operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="06f52-126">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="06f52-126">Behavior</span></span>  
  
- <span data-ttu-id="06f52-127">Ustanawia.</span><span class="sxs-lookup"><span data-stu-id="06f52-127">Mechanism.</span></span> <span data-ttu-id="06f52-128">Gdy wątek osiągnie `SyncLock` instrukcję, oblicza `lockobject` wyrażenie i wstrzymuje wykonywanie do momentu uzyskania blokady na wyłączność obiektu zwróconego przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="06f52-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="06f52-129">Gdy inny wątek osiągnie `SyncLock` instrukcję, nie uzyskuje blokady do momentu wykonania instrukcji przez pierwszy wątek `End SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="06f52-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="06f52-130">Chronione dane.</span><span class="sxs-lookup"><span data-stu-id="06f52-130">Protected Data.</span></span> <span data-ttu-id="06f52-131">Jeśli `lockobject` jest `Shared` zmienną, blokada wyłączna uniemożliwia wątek w dowolnym wystąpieniu klasy z wykonywania `SyncLock` bloku, gdy wykonuje inny wątek.</span><span class="sxs-lookup"><span data-stu-id="06f52-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="06f52-132">Chroni to dane, które są współużytkowane przez wszystkie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06f52-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="06f52-133">Jeśli `lockobject` jest zmienną wystąpienia (nie `Shared` ), blokada uniemożliwia wykonywanie przez wątek w bieżącym wystąpieniu `SyncLock` bloku w tym samym czasie co inny wątek w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="06f52-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="06f52-134">Zapewnia to ochronę danych przechowywanych przez poszczególne wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06f52-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="06f52-135">Pozyskiwanie i wydanie.</span><span class="sxs-lookup"><span data-stu-id="06f52-135">Acquisition and Release.</span></span> <span data-ttu-id="06f52-136">`SyncLock`Blok zachowuje się jak konstrukcja, `Try...Finally` w której `Try` blok uzyskuje blokadę na wyłączność `lockobject` i `Finally` blokuje ją.</span><span class="sxs-lookup"><span data-stu-id="06f52-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="06f52-137">W związku z tym `SyncLock` blok gwarantuje wydanie blokady bez względu na sposób zamykania bloku.</span><span class="sxs-lookup"><span data-stu-id="06f52-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="06f52-138">Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="06f52-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="06f52-139">Wywołania struktury.</span><span class="sxs-lookup"><span data-stu-id="06f52-139">Framework Calls.</span></span> <span data-ttu-id="06f52-140">`SyncLock`Blok uzyskuje i zwalnia blokadę na wyłączność, wywołując `Enter` `Exit` metody i `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="06f52-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="06f52-141">Praktyki programowania</span><span class="sxs-lookup"><span data-stu-id="06f52-141">Programming Practices</span></span>  
 <span data-ttu-id="06f52-142">`lockobject`Wyrażenie powinno zawsze być oceniane do obiektu, który należy wyłącznie do klasy.</span><span class="sxs-lookup"><span data-stu-id="06f52-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="06f52-143">Należy zadeklarować `Private` zmienną obiektu, aby chronić dane należące do bieżącego wystąpienia, lub `Private Shared` zmienną obiektu, aby chronić dane wspólne dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="06f52-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="06f52-144">Nie należy używać `Me` słowa kluczowego, aby dostarczyć obiekt blokady dla danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06f52-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="06f52-145">Jeśli kod zewnętrzny dla klasy zawiera odwołanie do wystąpienia klasy, może użyć tego odwołania jako obiektu blokady dla `SyncLock` bloku całkowicie innego niż ty, chroniąc różne dane.</span><span class="sxs-lookup"><span data-stu-id="06f52-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="06f52-146">W ten sposób Klasa i inna Klasa mogą blokować wykonywanie ich niepowiązanych `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="06f52-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="06f52-147">Podobne blokowanie na ciągu może być problematyczne, ponieważ jakikolwiek inny kod w procesie, który używa tego samego ciągu, będzie współużytkować tę samą blokadę.</span><span class="sxs-lookup"><span data-stu-id="06f52-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="06f52-148">Nie należy również używać metody, `Me.GetType` Aby zapewnić obiekt blokady dla danych udostępnionych.</span><span class="sxs-lookup"><span data-stu-id="06f52-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="06f52-149">Jest to spowodowane tym `GetType` , że zawsze zwraca ten sam `Type` obiekt dla danej nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="06f52-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="06f52-150">Kod zewnętrzny może wywoływać `GetType` w klasie i uzyskać ten sam obiekt blokady, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="06f52-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="06f52-151">Spowoduje to, że dwie klasy blokują siebie nawzajem z ich `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="06f52-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="06f52-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="06f52-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="06f52-153">Opis</span><span class="sxs-lookup"><span data-stu-id="06f52-153">Description</span></span>  
 <span data-ttu-id="06f52-154">Poniższy przykład przedstawia klasę, która utrzymuje prostą listę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="06f52-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="06f52-155">Przechowuje komunikaty w tablicy i ostatni używany element tej tablicy w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="06f52-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="06f52-156">`addAnotherMessage`Procedura zwiększa ostatni element i zapisuje nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="06f52-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="06f52-157">Te dwie operacje są chronione przez `SyncLock` instrukcje i `End SyncLock` , ponieważ po zwiększeniu ostatniego elementu nowy komunikat musi być przechowywany przed ponownym zwiększeniem ostatniego elementu.</span><span class="sxs-lookup"><span data-stu-id="06f52-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="06f52-158">Jeśli `simpleMessageList` Klasa udostępnia jedną listę komunikatów między wszystkimi wystąpieniami, zmienne `messagesList` i `messagesLast` byłyby zadeklarowane jako `Shared` .</span><span class="sxs-lookup"><span data-stu-id="06f52-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="06f52-159">W takim przypadku zmienna `messagesLock` powinna również być `Shared` , tak aby istniał pojedynczy obiekt blokady używany przez każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="06f52-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="06f52-160">Kod</span><span class="sxs-lookup"><span data-stu-id="06f52-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="06f52-161">Opis</span><span class="sxs-lookup"><span data-stu-id="06f52-161">Description</span></span>  
 <span data-ttu-id="06f52-162">W poniższym przykładzie zastosowano wątki i `SyncLock` .</span><span class="sxs-lookup"><span data-stu-id="06f52-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="06f52-163">Tak długo, jak `SyncLock` jest obecna instrukcja, blok instrukcji jest sekcją krytyczną i `balance` nigdy nie jest liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="06f52-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="06f52-164">Można dodać komentarz `SyncLock` `End SyncLock` do instrukcji i, aby zobaczyć efekt opuszczenia `SyncLock` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="06f52-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="06f52-165">Kod</span><span class="sxs-lookup"><span data-stu-id="06f52-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="06f52-166">Komentarze</span><span class="sxs-lookup"><span data-stu-id="06f52-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06f52-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06f52-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="06f52-168">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="06f52-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
