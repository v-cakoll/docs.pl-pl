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
ms.openlocfilehash: 0f430edce99513b0de9ef437d70648a128b336b8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352819"
---
# <a name="synclock-statement"></a><span data-ttu-id="e232f-102">SyncLock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e232f-102">SyncLock Statement</span></span>
<span data-ttu-id="e232f-103">Uzyskuje blokadę na wyłączność dla bloku instrukcji przed wykonaniem bloku.</span><span class="sxs-lookup"><span data-stu-id="e232f-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e232f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e232f-104">Syntax</span></span>  
  
```vb  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="e232f-105">Części</span><span class="sxs-lookup"><span data-stu-id="e232f-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="e232f-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e232f-106">Required.</span></span> <span data-ttu-id="e232f-107">Wyrażenie, którego wynikiem jest odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="e232f-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="e232f-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e232f-108">Optional.</span></span> <span data-ttu-id="e232f-109">Blok instrukcji, które mają zostać wykonane po pozyskaniu blokady.</span><span class="sxs-lookup"><span data-stu-id="e232f-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="e232f-110">Kończy blok `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e232f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e232f-111">Remarks</span></span>  
 <span data-ttu-id="e232f-112">Instrukcja `SyncLock` zapewnia, że wiele wątków nie wykonuje w tym samym czasie bloku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e232f-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="e232f-113">`SyncLock` uniemożliwia każdemu wątkowi przejście do bloku, dopóki nie zostanie on uruchomiony przez inny wątek.</span><span class="sxs-lookup"><span data-stu-id="e232f-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="e232f-114">Typowym zastosowaniem `SyncLock` jest ochrona danych przed aktualizacją przez więcej niż jeden wątek jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e232f-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="e232f-115">Jeśli instrukcje dotyczące manipulowania danymi muszą przejść do zakończenia bez zakłóceń, umieścić je wewnątrz bloku `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="e232f-116">Blok instrukcji chroniony przez blokadę wyłączną jest czasami nazywany *sekcją krytyczną*.</span><span class="sxs-lookup"><span data-stu-id="e232f-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="e232f-117">Reguły</span><span class="sxs-lookup"><span data-stu-id="e232f-117">Rules</span></span>  
  
- <span data-ttu-id="e232f-118">Rozgałęzianie.</span><span class="sxs-lookup"><span data-stu-id="e232f-118">Branching.</span></span> <span data-ttu-id="e232f-119">Nie można rozgałęzić do bloku `SyncLock` spoza bloku.</span><span class="sxs-lookup"><span data-stu-id="e232f-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
- <span data-ttu-id="e232f-120">Wartość blokady obiektu.</span><span class="sxs-lookup"><span data-stu-id="e232f-120">Lock Object Value.</span></span> <span data-ttu-id="e232f-121">Nie można `Nothing`wartości `lockobject`.</span><span class="sxs-lookup"><span data-stu-id="e232f-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="e232f-122">Należy utworzyć obiekt blokady przed użyciem go w instrukcji `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="e232f-123">Nie można zmienić wartości `lockobject` podczas wykonywania bloku `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="e232f-124">Mechanizm wymaga, aby obiekt blokady pozostał niezmieniony.</span><span class="sxs-lookup"><span data-stu-id="e232f-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
- <span data-ttu-id="e232f-125">Nie można użyć operatora [await](../../../visual-basic/language-reference/operators/await-operator.md) w bloku `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="e232f-126">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="e232f-126">Behavior</span></span>  
  
- <span data-ttu-id="e232f-127">Ustanawia.</span><span class="sxs-lookup"><span data-stu-id="e232f-127">Mechanism.</span></span> <span data-ttu-id="e232f-128">Gdy wątek osiągnie instrukcję `SyncLock`, oblicza wyrażenie `lockobject` i wstrzymuje wykonywanie do momentu uzyskania blokady na wyłączność obiektu zwróconego przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="e232f-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="e232f-129">Gdy inny wątek osiągnie instrukcję `SyncLock`, nie uzyskuje blokady do momentu wykonania instrukcji `End SyncLock` przez pierwszy wątek.</span><span class="sxs-lookup"><span data-stu-id="e232f-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
- <span data-ttu-id="e232f-130">Chronione dane.</span><span class="sxs-lookup"><span data-stu-id="e232f-130">Protected Data.</span></span> <span data-ttu-id="e232f-131">Jeśli `lockobject` jest zmienną `Shared`, blokada wyłączna zapobiega wykonywaniu przez wątek w jakimkolwiek wystąpieniu klasy `SyncLock` bloku, gdy wykonuje inny wątek.</span><span class="sxs-lookup"><span data-stu-id="e232f-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="e232f-132">Chroni to dane, które są współużytkowane przez wszystkie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e232f-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="e232f-133">Jeśli `lockobject` jest zmienną wystąpienia (nie `Shared`), blokada uniemożliwia `SyncLock` wykonywanie wątku uruchomionego w bieżącym wystąpieniu w tym samym czasie co inny wątek w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="e232f-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="e232f-134">Zapewnia to ochronę danych przechowywanych przez poszczególne wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e232f-134">This protects data maintained by the individual instance.</span></span>  
  
- <span data-ttu-id="e232f-135">Pozyskiwanie i wydanie.</span><span class="sxs-lookup"><span data-stu-id="e232f-135">Acquisition and Release.</span></span> <span data-ttu-id="e232f-136">Blok `SyncLock` zachowuje się jak konstrukcja `Try...Finally`, w której blok `Try` uzyskuje blokadę na wyłączność na `lockobject` i zwalnia ją przez blok `Finally`.</span><span class="sxs-lookup"><span data-stu-id="e232f-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="e232f-137">W związku z tym blok `SyncLock` gwarantuje wydanie blokady bez względu na sposób zamykania bloku.</span><span class="sxs-lookup"><span data-stu-id="e232f-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="e232f-138">Jest to prawdziwe nawet w przypadku nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e232f-138">This is true even in the case of an unhandled exception.</span></span>  
  
- <span data-ttu-id="e232f-139">Wywołania struktury.</span><span class="sxs-lookup"><span data-stu-id="e232f-139">Framework Calls.</span></span> <span data-ttu-id="e232f-140">Blok `SyncLock` uzyskuje i zwalnia blokadę wyłączną, wywołując metody `Enter` i `Exit` klasy `Monitor` w przestrzeni nazw <xref:System.Threading>.</span><span class="sxs-lookup"><span data-stu-id="e232f-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="e232f-141">Praktyki programowania</span><span class="sxs-lookup"><span data-stu-id="e232f-141">Programming Practices</span></span>  
 <span data-ttu-id="e232f-142">Wyrażenie `lockobject` powinno zawsze być oceniane do obiektu, który należy wyłącznie do klasy.</span><span class="sxs-lookup"><span data-stu-id="e232f-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="e232f-143">Należy zadeklarować zmienną obiektu `Private`, aby chronić dane należące do bieżącego wystąpienia, lub zmienną obiektu `Private Shared` do ochrony danych wspólnych dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="e232f-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="e232f-144">Nie należy używać słowa kluczowego `Me`, aby zapewnić obiekt blokady dla danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e232f-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="e232f-145">Jeśli kod zewnętrzny dla klasy ma odwołanie do wystąpienia klasy, może użyć tego odwołania jako obiektu blokady dla bloku `SyncLock` całkowicie innego niż ty, chroniąc różne dane.</span><span class="sxs-lookup"><span data-stu-id="e232f-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="e232f-146">W ten sposób Klasa i inna Klasa mogą blokować wykonywanie ich niepowiązanych bloków `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="e232f-147">Podobne blokowanie na ciągu może być problematyczne, ponieważ jakikolwiek inny kod w procesie, który używa tego samego ciągu, będzie współużytkować tę samą blokadę.</span><span class="sxs-lookup"><span data-stu-id="e232f-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="e232f-148">Nie należy również używać metody `Me.GetType`, aby zapewnić obiekt blokady dla danych udostępnionych.</span><span class="sxs-lookup"><span data-stu-id="e232f-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="e232f-149">Jest to spowodowane tym, że `GetType` zawsze zwraca ten sam obiekt `Type` dla danej nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="e232f-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="e232f-150">Kod zewnętrzny może wywoływać `GetType` w klasie i uzyskać ten sam obiekt blokady, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="e232f-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="e232f-151">Spowoduje to, że dwie klasy blokują siebie nawzajem z ich bloków `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e232f-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e232f-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="e232f-153">Opis</span><span class="sxs-lookup"><span data-stu-id="e232f-153">Description</span></span>  
 <span data-ttu-id="e232f-154">Poniższy przykład przedstawia klasę, która utrzymuje prostą listę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e232f-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="e232f-155">Przechowuje komunikaty w tablicy i ostatni używany element tej tablicy w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e232f-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="e232f-156">Procedura `addAnotherMessage` zwiększa ostatni element i zapisuje nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="e232f-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="e232f-157">Te dwie operacje są chronione przez instrukcje `SyncLock` i `End SyncLock`, ponieważ po zwiększeniu ostatniego elementu nowy komunikat musi być przechowywany przed ponownym zwiększeniem ostatniego elementu.</span><span class="sxs-lookup"><span data-stu-id="e232f-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="e232f-158">Jeśli Klasa `simpleMessageList` udostępnia jedną listę komunikatów między wszystkimi wystąpieniami, zmienne `messagesList` i `messagesLast` byłyby zadeklarowane jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="e232f-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="e232f-159">W takim przypadku zmienna `messagesLock` powinna być również `Shared`, dzięki czemu będzie on miał pojedynczy obiekt blokady używany przez każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e232f-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e232f-160">Kod</span><span class="sxs-lookup"><span data-stu-id="e232f-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/Class1.vb#1)]  
  
### <a name="description"></a><span data-ttu-id="e232f-161">Opis</span><span class="sxs-lookup"><span data-stu-id="e232f-161">Description</span></span>  
 <span data-ttu-id="e232f-162">W poniższym przykładzie są wykorzystywane wątki i `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="e232f-163">Tak długo, jak jest obecna instrukcja `SyncLock`, blok instrukcji jest sekcją krytyczną, a `balance` nigdy nie będzie liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="e232f-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="e232f-164">Można skomentować instrukcje `SyncLock` i `End SyncLock`, aby zobaczyć efekt opuszczania słowa kluczowego `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="e232f-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e232f-165">Kod</span><span class="sxs-lookup"><span data-stu-id="e232f-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrThreading/VB/class2.vb#21)]  
  
### <a name="comments"></a><span data-ttu-id="e232f-166">Komentarze</span><span class="sxs-lookup"><span data-stu-id="e232f-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e232f-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e232f-167">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="e232f-168">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="e232f-168">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
