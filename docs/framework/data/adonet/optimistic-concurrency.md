---
title: Optymistyczna współbieżność
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: a8cca707f8fa82e97e988fcbe015b55e35b93499
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794683"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="e11db-102">Optymistyczna współbieżność</span><span class="sxs-lookup"><span data-stu-id="e11db-102">Optimistic Concurrency</span></span>
<span data-ttu-id="e11db-103">W środowisku wielodostępnym istnieją dwa modele aktualizowania danych w bazie danych: optymistyczne współbieżność i pesymistyczne współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="e11db-104"><xref:System.Data.DataSet> Obiekt został zaprojektowany, aby zachęcić do korzystania z optymistycznej współbieżności dla długotrwałych działań, takich jak dane dotyczące komunikacji zdalnej i manipulowania danymi.</span><span class="sxs-lookup"><span data-stu-id="e11db-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="e11db-105">Współbieżność pesymistyczna polega na zablokowaniu wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w taki sposób, który ma wpływ na bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e11db-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="e11db-106">W modelu pesymistycznym, gdy użytkownik wykonuje akcję, która powoduje stosowanie blokady, inni użytkownicy nie mogą wykonać akcji, które mogłyby spowodować konflikt z blokadą do momentu jego zwolnienia przez właściciela.</span><span class="sxs-lookup"><span data-stu-id="e11db-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="e11db-107">Ten model jest używany głównie w środowiskach, w których istnieje intensywna rywalizacja o dane, dzięki czemu koszt ochrony danych z blokadami jest niższy niż koszt wycofywania transakcji w przypadku wystąpienia konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="e11db-108">W związku z tym w modelu współbieżności pesymistycznej użytkownik, który aktualizuje wiersz, ustanawia blokadę.</span><span class="sxs-lookup"><span data-stu-id="e11db-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="e11db-109">Do momentu zakończenia aktualizacji przez użytkownika i zwolnienia blokady nikt inny nie będzie mógł zmienić tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="e11db-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="e11db-110">Z tego powodu Współbieżność pesymistyczna jest najlepszym zaimplementowana, gdy czasy blokowania będą krótkie, jak programowe przetwarzanie rekordów.</span><span class="sxs-lookup"><span data-stu-id="e11db-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="e11db-111">Współbieżność pesymistyczna nie jest skalowalna, gdy użytkownicy pracują z danymi i powodują, że rekordy są blokowane przez stosunkowo długi czas.</span><span class="sxs-lookup"><span data-stu-id="e11db-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e11db-112">Jeśli musisz zaktualizować wiele wierszy w tej samej operacji, tworzenie transakcji jest bardziej skalowalne, niż przy użyciu pesymistycznego blokowania.</span><span class="sxs-lookup"><span data-stu-id="e11db-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="e11db-113">Z kolei użytkownicy korzystający z optymistycznej współbieżności nie blokują wiersza podczas odczytu.</span><span class="sxs-lookup"><span data-stu-id="e11db-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="e11db-114">Gdy użytkownik chce zaktualizować wiersz, aplikacja musi określić, czy inny użytkownik zmienił wiersz od czasu odczytu.</span><span class="sxs-lookup"><span data-stu-id="e11db-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="e11db-115">Współbieżność optymistyczna jest zwykle używana w środowiskach z niską rywalizacją dla danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="e11db-116">Optymistyczna współbieżność zwiększa wydajność, ponieważ nie jest wymagane blokowanie rekordów, a blokowanie rekordów wymaga dodatkowych zasobów serwera.</span><span class="sxs-lookup"><span data-stu-id="e11db-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="e11db-117">Ponadto w celu utrzymania blokad rekordów wymagane jest trwałe połączenie z serwerem bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="e11db-118">Ponieważ nie jest to przypadek optymistyczny model współbieżności, połączenia z serwerem są bezpłatne, aby zapewnić większą liczbę klientów w krótszym czasie.</span><span class="sxs-lookup"><span data-stu-id="e11db-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="e11db-119">W modelu współbieżności optymistycznej uważa się, że wystąpiło naruszenie, jeśli po odebraniu przez użytkownika wartości z bazy danych inny użytkownik zmodyfikuje wartość przed próbą zmodyfikowania jej przez pierwszego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e11db-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="e11db-120">Jak serwer rozpoznaje naruszenie współbieżności najlepiej ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e11db-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="e11db-121">W poniższych tabelach przedstawiono przykład optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="e11db-122">O godzinie 1:00, Użytkownik1 odczytuje wiersz z bazy danych o następujących wartościach:</span><span class="sxs-lookup"><span data-stu-id="e11db-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="e11db-123">**CustID nazwisko imię**</span><span class="sxs-lookup"><span data-stu-id="e11db-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="e11db-124">101 Kowalski Roberta</span><span class="sxs-lookup"><span data-stu-id="e11db-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="e11db-125">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="e11db-125">Column name</span></span>|<span data-ttu-id="e11db-126">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-126">Original value</span></span>|<span data-ttu-id="e11db-127">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-127">Current value</span></span>|<span data-ttu-id="e11db-128">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e11db-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="e11db-129">CustID</span><span class="sxs-lookup"><span data-stu-id="e11db-129">CustID</span></span>|<span data-ttu-id="e11db-130">101</span><span class="sxs-lookup"><span data-stu-id="e11db-130">101</span></span>|<span data-ttu-id="e11db-131">101</span><span class="sxs-lookup"><span data-stu-id="e11db-131">101</span></span>|<span data-ttu-id="e11db-132">101</span><span class="sxs-lookup"><span data-stu-id="e11db-132">101</span></span>|  
|<span data-ttu-id="e11db-133">LastName</span><span class="sxs-lookup"><span data-stu-id="e11db-133">LastName</span></span>|<span data-ttu-id="e11db-134">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-134">Smith</span></span>|<span data-ttu-id="e11db-135">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-135">Smith</span></span>|<span data-ttu-id="e11db-136">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-136">Smith</span></span>|  
|<span data-ttu-id="e11db-137">FirstName</span><span class="sxs-lookup"><span data-stu-id="e11db-137">FirstName</span></span>|<span data-ttu-id="e11db-138">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-138">Bob</span></span>|<span data-ttu-id="e11db-139">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-139">Bob</span></span>|<span data-ttu-id="e11db-140">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-140">Bob</span></span>|  
  
 <span data-ttu-id="e11db-141">O godzinie 1:01, 13:00 odczytuje ten sam wiersz.</span><span class="sxs-lookup"><span data-stu-id="e11db-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="e11db-142">O godzinie 1:03 – 13:00 zmiany **FirstName** od "Roberta" do "Robert" i aktualizuje bazę danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="e11db-143">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="e11db-143">Column name</span></span>|<span data-ttu-id="e11db-144">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-144">Original value</span></span>|<span data-ttu-id="e11db-145">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-145">Current value</span></span>|<span data-ttu-id="e11db-146">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e11db-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="e11db-147">CustID</span><span class="sxs-lookup"><span data-stu-id="e11db-147">CustID</span></span>|<span data-ttu-id="e11db-148">101</span><span class="sxs-lookup"><span data-stu-id="e11db-148">101</span></span>|<span data-ttu-id="e11db-149">101</span><span class="sxs-lookup"><span data-stu-id="e11db-149">101</span></span>|<span data-ttu-id="e11db-150">101</span><span class="sxs-lookup"><span data-stu-id="e11db-150">101</span></span>|  
|<span data-ttu-id="e11db-151">LastName</span><span class="sxs-lookup"><span data-stu-id="e11db-151">LastName</span></span>|<span data-ttu-id="e11db-152">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-152">Smith</span></span>|<span data-ttu-id="e11db-153">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-153">Smith</span></span>|<span data-ttu-id="e11db-154">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-154">Smith</span></span>|  
|<span data-ttu-id="e11db-155">FirstName</span><span class="sxs-lookup"><span data-stu-id="e11db-155">FirstName</span></span>|<span data-ttu-id="e11db-156">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-156">Bob</span></span>|<span data-ttu-id="e11db-157">Robert</span><span class="sxs-lookup"><span data-stu-id="e11db-157">Robert</span></span>|<span data-ttu-id="e11db-158">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-158">Bob</span></span>|  
  
 <span data-ttu-id="e11db-159">Aktualizacja powiedzie się, ponieważ wartości w bazie danych w czasie aktualizacji pasują do oryginalnych wartości, które mają wartość od.</span><span class="sxs-lookup"><span data-stu-id="e11db-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="e11db-160">O godzinie 1:05, Użytkownik1 zmieni imię "Roberta" na "Kuba" i spróbuje zaktualizować wiersz.</span><span class="sxs-lookup"><span data-stu-id="e11db-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="e11db-161">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="e11db-161">Column name</span></span>|<span data-ttu-id="e11db-162">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-162">Original value</span></span>|<span data-ttu-id="e11db-163">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="e11db-163">Current value</span></span>|<span data-ttu-id="e11db-164">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="e11db-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="e11db-165">CustID</span><span class="sxs-lookup"><span data-stu-id="e11db-165">CustID</span></span>|<span data-ttu-id="e11db-166">101</span><span class="sxs-lookup"><span data-stu-id="e11db-166">101</span></span>|<span data-ttu-id="e11db-167">101</span><span class="sxs-lookup"><span data-stu-id="e11db-167">101</span></span>|<span data-ttu-id="e11db-168">101</span><span class="sxs-lookup"><span data-stu-id="e11db-168">101</span></span>|  
|<span data-ttu-id="e11db-169">LastName</span><span class="sxs-lookup"><span data-stu-id="e11db-169">LastName</span></span>|<span data-ttu-id="e11db-170">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-170">Smith</span></span>|<span data-ttu-id="e11db-171">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-171">Smith</span></span>|<span data-ttu-id="e11db-172">Nazwisk</span><span class="sxs-lookup"><span data-stu-id="e11db-172">Smith</span></span>|  
|<span data-ttu-id="e11db-173">FirstName</span><span class="sxs-lookup"><span data-stu-id="e11db-173">FirstName</span></span>|<span data-ttu-id="e11db-174">Bob</span><span class="sxs-lookup"><span data-stu-id="e11db-174">Bob</span></span>|<span data-ttu-id="e11db-175">Tomasz</span><span class="sxs-lookup"><span data-stu-id="e11db-175">James</span></span>|<span data-ttu-id="e11db-176">Robert</span><span class="sxs-lookup"><span data-stu-id="e11db-176">Robert</span></span>|  
  
 <span data-ttu-id="e11db-177">W tym momencie Użytkownik1 napotyka optymistyczne naruszenie współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest już zgodna z oryginalną wartością oczekiwaną przez Użytkownik1 ("Robert").</span><span class="sxs-lookup"><span data-stu-id="e11db-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="e11db-178">Naruszenie współbieżności pozwala stwierdzić, że aktualizacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="e11db-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="e11db-179">Należy teraz podjąć decyzję, czy zastąpić zmiany wprowadzone przez użytkownika, wprowadzając zmiany podane przez Użytkownik1, lub aby anulować zmiany przez Użytkownik1.</span><span class="sxs-lookup"><span data-stu-id="e11db-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="e11db-180">Testowanie dla optymistycznych naruszeń współbieżności</span><span class="sxs-lookup"><span data-stu-id="e11db-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="e11db-181">Istnieje kilka technik testowania dla optymistycznego naruszenia współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="e11db-182">Jeden z nich obejmuje dołączenie kolumny timestamp do tabeli.</span><span class="sxs-lookup"><span data-stu-id="e11db-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="e11db-183">Bazy danych często zapewniają funkcję sygnatur czasowych, która może służyć do identyfikowania daty i godziny ostatniej aktualizacji rekordu.</span><span class="sxs-lookup"><span data-stu-id="e11db-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="e11db-184">Korzystając z tej techniki, w definicji tabeli jest dołączona kolumna sygnatur czasowych.</span><span class="sxs-lookup"><span data-stu-id="e11db-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="e11db-185">Za każdym razem, gdy rekord zostanie zaktualizowany, sygnatura czasowa jest aktualizowana w celu odzwierciedlenia bieżącej daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="e11db-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="e11db-186">W teście dla optymistycznych naruszeń współbieżności kolumna sygnatury czasowej jest zwracana z dowolnego zapytania o zawartość tabeli.</span><span class="sxs-lookup"><span data-stu-id="e11db-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="e11db-187">Po próbie aktualizacji wartość sygnatury czasowej w bazie danych jest porównywana z oryginalną wartością sygnatury czasowej zawartej w zmodyfikowanym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e11db-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="e11db-188">Jeśli są one zgodne, aktualizacja jest wykonywana, a kolumna sygnatury czasowej zostaje zaktualizowana o bieżący czas, aby odzwierciedlić aktualizację.</span><span class="sxs-lookup"><span data-stu-id="e11db-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="e11db-189">Jeśli nie są zgodne, nastąpiło jednooptymistyczne naruszenie współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="e11db-190">Inna technika testowania dla optymistycznego naruszenia współbieżności polega na sprawdzeniu, czy wszystkie oryginalne wartości kolumn w wierszu nadal pasują do nazw znalezionych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="e11db-191">Rozważmy na przykład następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="e11db-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="e11db-192">Aby sprawdzić optymistyczne naruszenie współbieżności podczas aktualizowania wiersza w tabeli **Tabela1**, należy wydać następującą instrukcję AKTUALIZUJĄCĄ:</span><span class="sxs-lookup"><span data-stu-id="e11db-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="e11db-193">Tak długo, jak oryginalne wartości pasują do wartości w bazie danych, jest przeprowadzana aktualizacja.</span><span class="sxs-lookup"><span data-stu-id="e11db-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="e11db-194">Jeśli wartość została zmodyfikowana, aktualizacja nie zmodyfikuje wiersza, ponieważ klauzula WHERE nie znajdzie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="e11db-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="e11db-195">Należy zauważyć, że zaleca się zawsze zwrócenie unikatowej wartości klucza podstawowego do zapytania.</span><span class="sxs-lookup"><span data-stu-id="e11db-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="e11db-196">W przeciwnym razie Poprzednia instrukcja UPDATE może zaktualizować więcej niż jeden wiersz, co może nie być Twoim zamiarem.</span><span class="sxs-lookup"><span data-stu-id="e11db-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="e11db-197">Jeśli kolumna w źródle danych dopuszcza wartości null, może być konieczne przeciągnięcie klauzuli WHERE, aby sprawdzić pasujące odwołanie o wartości null w lokalnej tabeli i w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="e11db-198">Na przykład następująca instrukcja UPDATE sprawdza, czy odwołanie o wartości null w wierszu lokalnym nadal pasuje do odwołania o wartości null w źródle danych lub czy wartość w wierszu lokalnym nadal pasuje do wartości w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="e11db-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="e11db-199">Można również zastosować mniej restrykcyjne kryteria przy użyciu optymistycznego modelu współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="e11db-200">Na przykład użycie tylko kolumn klucza podstawowego w klauzuli WHERE powoduje zastąpienie danych bez względu na to, czy inne kolumny zostały zaktualizowane od czasu ostatniego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e11db-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="e11db-201">Można również zastosować klauzulę WHERE tylko do określonych kolumn, co spowoduje zastąpienie danych, chyba że określone pola zostały zaktualizowane od czasu ostatniego zapytania.</span><span class="sxs-lookup"><span data-stu-id="e11db-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="e11db-202">Zdarzenie DataAdapter. RowUpdated</span><span class="sxs-lookup"><span data-stu-id="e11db-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="e11db-203">Zdarzenie<xref:System.Data.Common.DataAdapter> **RowUpdated** obiektu może być używane w połączeniu z opisanymi wcześniej technikami w celu dostarczenia powiadomienia do aplikacji optymistyczne naruszenia współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="e11db-204">**RowUpdated** występuje po każdej próbie zaktualizowania **zmodyfikowanego** wiersza z **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e11db-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="e11db-205">Dzięki temu można dodać specjalny kod obsługi, w tym przetwarzanie w przypadku wystąpienia wyjątku, dodanie niestandardowych informacji o błędzie, dodanie logiki ponawiania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="e11db-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="e11db-206">Obiekt zwraca Właściwość RecordsAffected zawierającą liczbę wierszy, na które miało wpływ określone polecenie Update dla zmodyfikowanego wiersza w tabeli. <xref:System.Data.Common.RowUpdatedEventArgs></span><span class="sxs-lookup"><span data-stu-id="e11db-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="e11db-207">Ustawiając polecenie Update do testowania optymistycznej współbieżności, właściwość **RecordsAffected** będzie w efekcie zwracać wartość 0 w przypadku wystąpienia naruszenia optymistycznej współbieżności, ponieważ żadne rekordy nie zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="e11db-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="e11db-208">W takim przypadku zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e11db-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="e11db-209">Zdarzenie **RowUpdated** umożliwia obsługę tego wystąpienia i uniknięcie wyjątku przez ustawienie odpowiedniej wartości **RowUpdatedEventArgs. status** , takiej jak **UpdateStatus. SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="e11db-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="e11db-210">Aby uzyskać więcej informacji o zdarzeniu **RowUpdated** , zobacz [Obsługa zdarzeń DataAdapter](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="e11db-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="e11db-211">Opcjonalnie można ustawić **Właściwość DataAdapter. ContinueUpdateOnError** na **wartość true**, przed wywołaniem funkcji **Update**, a następnie odpowiedzieć na informacje o błędzie przechowywane we właściwości **RowError** określonego wiersza po zakończeniu **aktualizacji** .</span><span class="sxs-lookup"><span data-stu-id="e11db-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="e11db-212">Aby uzyskać więcej informacji, zobacz [wiersz informacje o błędzie](./dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="e11db-212">For more information, see [Row Error Information](./dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="e11db-213">Przykład optymistycznej współbieżności</span><span class="sxs-lookup"><span data-stu-id="e11db-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="e11db-214">Poniżej przedstawiono prosty przykład, który ustawia element **UpdateCommand** elementu **DataAdapter** do testowania optymistycznej współbieżności, a następnie używa zdarzenia **RowUpdated** do testowania optymistycznych naruszeń współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="e11db-215">Po napotkaniu optymistycznego naruszenia współbieżności aplikacja ustawia **RowError** wiersza, dla którego aktualizacja została wystawiona, aby odzwierciedlał optymistyczne naruszenie współbieżności.</span><span class="sxs-lookup"><span data-stu-id="e11db-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="e11db-216">Należy zauważyć, że wartości parametrów przesyłane do klauzuli WHERE polecenia UPDATE są mapowane na **oryginalne** wartości odpowiednich kolumn.</span><span class="sxs-lookup"><span data-stu-id="e11db-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e11db-217">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e11db-217">See also</span></span>

- [<span data-ttu-id="e11db-218">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e11db-218">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="e11db-219">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="e11db-219">Updating Data Sources with DataAdapters</span></span>](updating-data-sources-with-dataadapters.md)
- [<span data-ttu-id="e11db-220">Informacje o błędzie wiersza</span><span class="sxs-lookup"><span data-stu-id="e11db-220">Row Error Information</span></span>](./dataset-datatable-dataview/row-error-information.md)
- [<span data-ttu-id="e11db-221">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="e11db-221">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="e11db-222">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="e11db-222">ADO.NET Overview</span></span>](ado-net-overview.md)
