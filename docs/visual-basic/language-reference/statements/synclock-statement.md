---
title: "SyncLock — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c826e1ba592dfc4f2899a26102466d2e7df54f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="synclock-statement"></a><span data-ttu-id="b4630-102">SyncLock — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="b4630-102">SyncLock Statement</span></span>
<span data-ttu-id="b4630-103">Uzyskuje wyłącznej blokady dla blok instrukcji, przed wykonaniem bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-103">Acquires an exclusive lock for a statement block before executing the block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4630-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4630-104">Syntax</span></span>  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a><span data-ttu-id="b4630-105">Części</span><span class="sxs-lookup"><span data-stu-id="b4630-105">Parts</span></span>  
 `lockobject`  
 <span data-ttu-id="b4630-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b4630-106">Required.</span></span> <span data-ttu-id="b4630-107">Wyrażenie obliczane do odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b4630-107">Expression that evaluates to an object reference.</span></span>  
  
 `block`  
 <span data-ttu-id="b4630-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="b4630-108">Optional.</span></span> <span data-ttu-id="b4630-109">Blok instrukcji, które są do wykonania, gdy są uzyskiwane blokady.</span><span class="sxs-lookup"><span data-stu-id="b4630-109">Block of statements that are to execute when the lock is acquired.</span></span>  
  
 `End SyncLock`  
 <span data-ttu-id="b4630-110">Kończy `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-110">Terminates a `SyncLock` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4630-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4630-111">Remarks</span></span>  
 <span data-ttu-id="b4630-112">`SyncLock` Instrukcji gwarantuje, że wiele wątków nie wykonuje bloku instrukcji w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b4630-112">The `SyncLock` statement ensures that multiple threads do not execute the statement block at the same time.</span></span> <span data-ttu-id="b4630-113">`SyncLock`Każdy wątek uniemożliwia wprowadzanie bloku, dopóki nie innego wątku jest jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="b4630-113">`SyncLock` prevents each thread from entering the block until no other thread is executing it.</span></span>  
  
 <span data-ttu-id="b4630-114">Najczęściej używane `SyncLock` ma chronić dane przed aktualizowana przez więcej niż jeden wątek jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b4630-114">The most common use of `SyncLock` is to protect data from being updated by more than one thread simultaneously.</span></span> <span data-ttu-id="b4630-115">Jeśli instrukcji, które manipulowania danymi muszą przejść do ukończenia bez przeszkód, umieść je w `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-115">If the statements that manipulate the data must go to completion without interruption, put them inside a `SyncLock` block.</span></span>  
  
 <span data-ttu-id="b4630-116">Blok instrukcji chronione w trybie wyłączności jest czasami nazywany *sekcja krytyczna*.</span><span class="sxs-lookup"><span data-stu-id="b4630-116">A statement block protected by an exclusive lock is sometimes called a *critical section*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b4630-117">Reguły</span><span class="sxs-lookup"><span data-stu-id="b4630-117">Rules</span></span>  
  
-   <span data-ttu-id="b4630-118">Rozgałęzianie.</span><span class="sxs-lookup"><span data-stu-id="b4630-118">Branching.</span></span> <span data-ttu-id="b4630-119">Nie można rozgałęzić do `SyncLock` zablokować poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="b4630-119">You cannot branch into a `SyncLock` block from outside the block.</span></span>  
  
-   <span data-ttu-id="b4630-120">Wartość obiektu blokady.</span><span class="sxs-lookup"><span data-stu-id="b4630-120">Lock Object Value.</span></span> <span data-ttu-id="b4630-121">Wartość `lockobject` nie może być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b4630-121">The value of `lockobject` cannot be `Nothing`.</span></span> <span data-ttu-id="b4630-122">Należy utworzyć obiekt blokady przed użyciem go w `SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b4630-122">You must create the lock object before you use it in a `SyncLock` statement.</span></span>  
  
     <span data-ttu-id="b4630-123">Nie można zmienić wartości `lockobject` podczas wykonywania `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-123">You cannot change the value of `lockobject` while executing a `SyncLock` block.</span></span> <span data-ttu-id="b4630-124">Mechanizm wymaga, aby zablokować obiektu pozostają niezmienione.</span><span class="sxs-lookup"><span data-stu-id="b4630-124">The mechanism requires that the lock object remain unchanged.</span></span>  
  
-   <span data-ttu-id="b4630-125">Nie można użyć [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora w `SyncLock` bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-125">You can't use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in a `SyncLock` block.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b4630-126">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="b4630-126">Behavior</span></span>  
  
-   <span data-ttu-id="b4630-127">Mechanizm.</span><span class="sxs-lookup"><span data-stu-id="b4630-127">Mechanism.</span></span> <span data-ttu-id="b4630-128">Gdy osiągnie wątku `SyncLock` instrukcji, ocenia `lockobject` wyrażenie i wstrzymuje wykonywanie do momentu otrzymuje wyłącznej blokady obiektu zwróconego przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b4630-128">When a thread reaches the `SyncLock` statement, it evaluates the `lockobject` expression and suspends execution until it acquires an exclusive lock on the object returned by the expression.</span></span> <span data-ttu-id="b4630-129">Gdy osiągnie inny wątek `SyncLock` instrukcji go nie uzyskania blokady dopóki wykonuje pierwszym wątkiem `End SyncLock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b4630-129">When another thread reaches the `SyncLock` statement, it does not acquire a lock until the first thread executes the `End SyncLock` statement.</span></span>  
  
-   <span data-ttu-id="b4630-130">Chronionych danych.</span><span class="sxs-lookup"><span data-stu-id="b4630-130">Protected Data.</span></span> <span data-ttu-id="b4630-131">Jeśli `lockobject` jest `Shared` zmiennej, blokada na wyłączność uniemożliwia wątku w żadnym wystąpieniu klasy wykonywania `SyncLock` zablokowanie, gdy jest jej wykonanie innego wątku.</span><span class="sxs-lookup"><span data-stu-id="b4630-131">If `lockobject` is a `Shared` variable, the exclusive lock prevents a thread in any instance of the class from executing the `SyncLock` block while any other thread is executing it.</span></span> <span data-ttu-id="b4630-132">Pozwala to chronić dane, które jest współdzielona przez wszystkie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4630-132">This protects data that is shared among all the instances.</span></span>  
  
     <span data-ttu-id="b4630-133">Jeśli `lockobject` jest zmienna wystąpienia (nie `Shared`), blokada uniemożliwia uruchomiony w bieżącym wystąpieniu wykonywanie wątku `SyncLock` bloku, w tym samym czasie jako inny wątek w tym samym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="b4630-133">If `lockobject` is an instance variable (not `Shared`), the lock prevents a thread running in the current instance from executing the `SyncLock` block at the same time as another thread in the same instance.</span></span> <span data-ttu-id="b4630-134">Jest to zabezpieczenie danych obsługiwanych przez poszczególne wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4630-134">This protects data maintained by the individual instance.</span></span>  
  
-   <span data-ttu-id="b4630-135">Nabycia i wersji.</span><span class="sxs-lookup"><span data-stu-id="b4630-135">Acquisition and Release.</span></span> <span data-ttu-id="b4630-136">A `SyncLock` bloku zachowuje się jak `Try...Finally` konstrukcji, w którym `Try` bloku uzyskuje w trybie wyłączności na `lockobject` i `Finally` zwolnieniem bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-136">A `SyncLock` block behaves like a `Try...Finally` construction in which the `Try` block acquires an exclusive lock on `lockobject` and the `Finally` block releases it.</span></span> <span data-ttu-id="b4630-137">W związku z tym `SyncLock` bloku gwarantuje wersji blokady, niezależnie od tego, jak zakończyć bloku.</span><span class="sxs-lookup"><span data-stu-id="b4630-137">Because of this, the `SyncLock` block guarantees release of the lock, no matter how you exit the block.</span></span> <span data-ttu-id="b4630-138">Dotyczy to nawet w przypadku nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="b4630-138">This is true even in the case of an unhandled exception.</span></span>  
  
-   <span data-ttu-id="b4630-139">Wywołania Framework.</span><span class="sxs-lookup"><span data-stu-id="b4630-139">Framework Calls.</span></span> <span data-ttu-id="b4630-140">`SyncLock` Blok uzyskuje i zwalnia blokada na wyłączność przez wywołanie metody `Enter` i `Exit` metody `Monitor` klasy w <xref:System.Threading> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4630-140">The `SyncLock` block acquires and releases the exclusive lock by calling the `Enter` and `Exit` methods of the `Monitor` class in the <xref:System.Threading> namespace.</span></span>  
  
## <a name="programming-practices"></a><span data-ttu-id="b4630-141">Rozwiązania w zakresie programowania</span><span class="sxs-lookup"><span data-stu-id="b4630-141">Programming Practices</span></span>  
 <span data-ttu-id="b4630-142">`lockobject` Wyrażenia zawsze powinna być obiekt, który należy wyłącznie do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="b4630-142">The `lockobject` expression should always evaluate to an object that belongs exclusively to your class.</span></span> <span data-ttu-id="b4630-143">Powinien deklarować `Private` zmienna obiektu do ochrony danych należących do bieżącego wystąpienia lub `Private Shared` zmienna obiektu, aby chronić dane wspólne dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="b4630-143">You should declare a `Private` object variable to protect data belonging to the current instance, or a `Private Shared` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="b4630-144">Nie należy używać `Me` — słowo kluczowe w celu zapewnienia blokady dla wystąpienia obiektu danych.</span><span class="sxs-lookup"><span data-stu-id="b4630-144">You should not use the `Me` keyword to provide a lock object for instance data.</span></span> <span data-ttu-id="b4630-145">Jeśli kod zewnętrzny klasy zawiera odwołanie do wystąpienia klasy, można użyć tego odwołania dla obiekt blokady `SyncLock` bloku całkowicie różni się od należy do Ciebie, ochrony danych.</span><span class="sxs-lookup"><span data-stu-id="b4630-145">If code external to your class has a reference to an instance of your class, it could use that reference as a lock object for a `SyncLock` block completely different from yours, protecting different data.</span></span> <span data-ttu-id="b4630-146">W ten sposób, klasy i inne klasy można zablokować wzajemnie wykonywanie ich niepowiązanych `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="b4630-146">In this way, your class and the other class could block each other from executing their unrelated `SyncLock` blocks.</span></span> <span data-ttu-id="b4630-147">Podobnie blokowania na ciąg może sprawiać problemy, ponieważ innego kodu w procesie przy użyciu tych samych parametrach współużytkują tego samego blokady.</span><span class="sxs-lookup"><span data-stu-id="b4630-147">Similarly locking on a string can be problematic since any other code in the process using the same string will share the same lock.</span></span>  
  
 <span data-ttu-id="b4630-148">Ponadto nie należy korzystać z `Me.GetType` metodę w celu zapewnienia obiektu blokady dla udostępnionych danych.</span><span class="sxs-lookup"><span data-stu-id="b4630-148">You should also not use the `Me.GetType` method to provide a lock object for shared data.</span></span> <span data-ttu-id="b4630-149">Jest to spowodowane `GetType` zawsze zwraca takie same `Type` obiektu dla nazwy danej klasy.</span><span class="sxs-lookup"><span data-stu-id="b4630-149">This is because `GetType` always returns the same `Type` object for a given class name.</span></span> <span data-ttu-id="b4630-150">Kod zewnętrzny można wywołać `GetType` w klasie i uzyskać ten sam obiekt blokady używasz.</span><span class="sxs-lookup"><span data-stu-id="b4630-150">External code could call `GetType` on your class and obtain the same lock object you are using.</span></span> <span data-ttu-id="b4630-151">Spowodowałoby to dwie klasy blokuje siebie z ich `SyncLock` bloków.</span><span class="sxs-lookup"><span data-stu-id="b4630-151">This would result in the two classes blocking each other from their `SyncLock` blocks.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b4630-152">Przykłady</span><span class="sxs-lookup"><span data-stu-id="b4630-152">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="b4630-153">Opis</span><span class="sxs-lookup"><span data-stu-id="b4630-153">Description</span></span>  
 <span data-ttu-id="b4630-154">Poniższy przykład przedstawia klasę zawierającą prostą listę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b4630-154">The following example shows a class that maintains a simple list of messages.</span></span> <span data-ttu-id="b4630-155">Przechowuje komunikaty w tablicy i ostatniego używany element tablicy w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b4630-155">It holds the messages in an array and the last used element of that array in a variable.</span></span> <span data-ttu-id="b4630-156">`addAnotherMessage` Procedury zwiększa ostatnim elementem i przechowuje nowy komunikat.</span><span class="sxs-lookup"><span data-stu-id="b4630-156">The `addAnotherMessage` procedure increments the last element and stores the new message.</span></span> <span data-ttu-id="b4630-157">Tych dwóch operacji są chronione przez `SyncLock` i `End SyncLock` instrukcji, ponieważ po ostatnim elemencie została zwiększona, nowej wiadomości musi być przechowywany przed innego wątku może zwiększyć ostatni element ponownie.</span><span class="sxs-lookup"><span data-stu-id="b4630-157">Those two operations are protected by the `SyncLock` and `End SyncLock` statements, because once the last element has been incremented, the new message must be stored before any other thread can increment the last element again.</span></span>  
  
 <span data-ttu-id="b4630-158">Jeśli `simpleMessageList` klasy udostępnionych jedną listę komunikatów między wszystkie jego wystąpienia, zmienne `messagesList` i `messagesLast` może być zadeklarowana jako `Shared`.</span><span class="sxs-lookup"><span data-stu-id="b4630-158">If the `simpleMessageList` class shared one list of messages among all its instances, the variables `messagesList` and `messagesLast` would be declared as `Shared`.</span></span> <span data-ttu-id="b4630-159">W tym przypadku zmiennej `messagesLock` należy również `Shared`, dzięki czemu będzie obiektu jedną blokadą używane przez każde wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b4630-159">In this case, the variable `messagesLock` should also be `Shared`, so that there would be a single lock object used by every instance.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b4630-160">Kod</span><span class="sxs-lookup"><span data-stu-id="b4630-160">Code</span></span>  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a><span data-ttu-id="b4630-161">Opis</span><span class="sxs-lookup"><span data-stu-id="b4630-161">Description</span></span>  
 <span data-ttu-id="b4630-162">W poniższym przykładzie użyto wątków i `SyncLock`.</span><span class="sxs-lookup"><span data-stu-id="b4630-162">The following example uses threads and `SyncLock`.</span></span> <span data-ttu-id="b4630-163">Tak długo, jak `SyncLock` instrukcji, blok instrukcji jest sekcja krytyczna i `balance` nigdy nie jest liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="b4630-163">As long as the `SyncLock` statement is present, the statement block is a critical section and `balance` never becomes a negative number.</span></span> <span data-ttu-id="b4630-164">Możesz przekształcić w komentarz `SyncLock` i `End SyncLock` instrukcje, aby zobaczyć efekt pomijając `SyncLock` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b4630-164">You can comment out the `SyncLock` and `End SyncLock` statements to see the effect of leaving out the `SyncLock` keyword.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b4630-165">Kod</span><span class="sxs-lookup"><span data-stu-id="b4630-165">Code</span></span>  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a><span data-ttu-id="b4630-166">Komentarze</span><span class="sxs-lookup"><span data-stu-id="b4630-166">Comments</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4630-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4630-167">See Also</span></span>  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="b4630-168">Synchronizacja wątku</span><span class="sxs-lookup"><span data-stu-id="b4630-168">Thread Synchronization</span></span>](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)  
 [<span data-ttu-id="b4630-169">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="b4630-169">Threading</span></span>](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)
