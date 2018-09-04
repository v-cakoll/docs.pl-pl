---
title: Optymistyczna współbieżność
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: 641a1cc0fd0ec53872ee3312e7da06923b82ddd7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507608"
---
# <a name="optimistic-concurrency"></a><span data-ttu-id="d7334-102">Optymistyczna współbieżność</span><span class="sxs-lookup"><span data-stu-id="d7334-102">Optimistic Concurrency</span></span>
<span data-ttu-id="d7334-103">W środowisku wielodostępnym, istnieją dwa modele aktualizacji danych w bazie danych: optymistycznej współbieżności i pesymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-103">In a multiuser environment, there are two models for updating data in a database: optimistic concurrency and pessimistic concurrency.</span></span> <span data-ttu-id="d7334-104"><xref:System.Data.DataSet> Obiektu jest przeznaczona do zachęcać do stosowania funkcji optymistycznej współbieżności dla długotrwałych działań, takich jak dane usług zdalnych i wchodzenie w interakcje z danymi.</span><span class="sxs-lookup"><span data-stu-id="d7334-104">The <xref:System.Data.DataSet> object is designed to encourage the use of optimistic concurrency for long-running activities, such as remoting data and interacting with data.</span></span>  
  
 <span data-ttu-id="d7334-105">Współbieżność pesymistyczna polega na blokowanie wierszy w źródle danych, aby uniemożliwić innym użytkownikom modyfikowanie danych w sposób, który ma wpływ na bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7334-105">Pessimistic concurrency involves locking rows at the data source to prevent other users from modifying data in a way that affects the current user.</span></span> <span data-ttu-id="d7334-106">Pesymistyczne modelu gdy użytkownik wykona akcję, która powoduje, że blokady do zastosowania, inni użytkownicy nie można wykonać akcje, które spowodowałoby to konflikt z blokadą do momentu właściciel blokady zwalnia go.</span><span class="sxs-lookup"><span data-stu-id="d7334-106">In a pessimistic model, when a user performs an action that causes a lock to be applied, other users cannot perform actions that would conflict with the lock until the lock owner releases it.</span></span> <span data-ttu-id="d7334-107">Ten model jest używany głównie w środowiskach, w której jest mocno rywalizacji o danych, tak, aby koszty ochrony danych przy użyciu blokady jest mniejsza niż koszt wycofywanie transakcji, jeśli występują konflikty współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-107">This model is primarily used in environments where there is heavy contention for data, so that the cost of protecting data with locks is less than the cost of rolling back transactions if concurrency conflicts occur.</span></span>  
  
 <span data-ttu-id="d7334-108">W związku z tym w modelu pesymistycznej współbieżności, użytkownik, który aktualizuje wiersz ustanawia blokadę.</span><span class="sxs-lookup"><span data-stu-id="d7334-108">Therefore, in a pessimistic concurrency model, a user who updates a row establishes a lock.</span></span> <span data-ttu-id="d7334-109">Dopóki użytkownik nie ma Zakończono aktualizację i ogólnie blokady, nikt inny nie można zmienić tego wiersza.</span><span class="sxs-lookup"><span data-stu-id="d7334-109">Until the user has finished the update and released the lock, no one else can change that row.</span></span> <span data-ttu-id="d7334-110">Współbieżność pesymistyczna z tego powodu najlepiej jest implementowane, gdy czasy blokady będą krótki, tak jak programowe przetwarzania rekordów.</span><span class="sxs-lookup"><span data-stu-id="d7334-110">For this reason, pessimistic concurrency is best implemented when lock times will be short, as in programmatic processing of records.</span></span> <span data-ttu-id="d7334-111">Współbieżność pesymistyczna nie jest to skalowalne rozwiązanie, gdy użytkownicy są wchodzenie w interakcje z danymi i powodują, że rekordy zostanie zablokowane przez stosunkowo dużej ilości okresy.</span><span class="sxs-lookup"><span data-stu-id="d7334-111">Pessimistic concurrency is not a scalable option when users are interacting with data and causing records to be locked for relatively large periods of time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7334-112">Jeśli trzeba zaktualizować wiele wierszy w tej samej operacji, następnie utworzenie transakcji jest bardziej skalowalna opcji niż przy użyciu pesymistycznego blokowania.</span><span class="sxs-lookup"><span data-stu-id="d7334-112">If you need to update multiple rows in the same operation, then creating a transaction is a more scalable option than using pessimistic locking.</span></span>  
  
 <span data-ttu-id="d7334-113">Z drugiej strony Użytkownicy, którzy używaj optymistycznej współbieżności nie Blokuj wiersz podczas jej odczytywania.</span><span class="sxs-lookup"><span data-stu-id="d7334-113">By contrast, users who use optimistic concurrency do not lock a row when reading it.</span></span> <span data-ttu-id="d7334-114">Gdy użytkownik chce, aby zaktualizować wiersza, aplikacji należy określić, czy inny użytkownik zmienił wiersza, ponieważ została ona odczytana.</span><span class="sxs-lookup"><span data-stu-id="d7334-114">When a user wants to update a row, the application must determine whether another user has changed the row since it was read.</span></span> <span data-ttu-id="d7334-115">Optymistyczna współbieżność jest zazwyczaj używane w środowiskach z niskim rywalizacji o zasoby danych.</span><span class="sxs-lookup"><span data-stu-id="d7334-115">Optimistic concurrency is generally used in environments with a low contention for data.</span></span> <span data-ttu-id="d7334-116">Optymistyczna współbieżność zwiększa wydajność, ponieważ wymagana jest nie blokowania rekordów i blokowanie rekordów wymaga dodatkowych zasobów serwera.</span><span class="sxs-lookup"><span data-stu-id="d7334-116">Optimistic concurrency improves performance because no locking of records is required, and locking of records requires additional server resources.</span></span> <span data-ttu-id="d7334-117">Ponadto w celu utrzymania blokady rekordu, trwałe połączenie z serwerem bazy danych jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d7334-117">Also, in order to maintain record locks, a persistent connection to the database server is required.</span></span> <span data-ttu-id="d7334-118">Ponieważ nie jest w przypadku modelu optymistycznej współbieżności, połączenia z serwerem są bezpłatne do obsługi większej liczby klientów w krótszym czasie.</span><span class="sxs-lookup"><span data-stu-id="d7334-118">Because this is not the case in an optimistic concurrency model, connections to the server are free to serve a larger number of clients in less time.</span></span>  
  
 <span data-ttu-id="d7334-119">W modelu optymistycznej współbieżności naruszenie uznaje się miała miejsce, jeśli po użytkownik otrzymuje wartość z bazy danych, inny użytkownik modyfikuje wartość, zanim pierwszy użytkownik próbował go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="d7334-119">In an optimistic concurrency model, a violation is considered to have occurred if, after a user receives a value from the database, another user modifies the value before the first user has attempted to modify it.</span></span> <span data-ttu-id="d7334-120">Jak serwer rozpoznaje Naruszenie współbieżności najlepiej jest wyświetlany przy pierwszym opisujące w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d7334-120">How the server resolves a concurrency violation is best shown by first describing the following example.</span></span>  
  
 <span data-ttu-id="d7334-121">Poniższe tabele postępuj zgodnie z przykładem optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-121">The following tables follow an example of optimistic concurrency.</span></span>  
  
 <span data-ttu-id="d7334-122">O 1:00 Użytkownik1 odczytuje wiersz z bazy danych z następującymi wartościami:</span><span class="sxs-lookup"><span data-stu-id="d7334-122">At 1:00 p.m., User1 reads a row from the database with the following values:</span></span>  
  
 <span data-ttu-id="d7334-123">**CustID nazwisko imię**</span><span class="sxs-lookup"><span data-stu-id="d7334-123">**CustID     LastName     FirstName**</span></span>  
  
 <span data-ttu-id="d7334-124">101 Bob Smith</span><span class="sxs-lookup"><span data-stu-id="d7334-124">101          Smith             Bob</span></span>  
  
|<span data-ttu-id="d7334-125">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="d7334-125">Column name</span></span>|<span data-ttu-id="d7334-126">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-126">Original value</span></span>|<span data-ttu-id="d7334-127">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-127">Current value</span></span>|<span data-ttu-id="d7334-128">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="d7334-128">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d7334-129">CustID</span><span class="sxs-lookup"><span data-stu-id="d7334-129">CustID</span></span>|<span data-ttu-id="d7334-130">101</span><span class="sxs-lookup"><span data-stu-id="d7334-130">101</span></span>|<span data-ttu-id="d7334-131">101</span><span class="sxs-lookup"><span data-stu-id="d7334-131">101</span></span>|<span data-ttu-id="d7334-132">101</span><span class="sxs-lookup"><span data-stu-id="d7334-132">101</span></span>|  
|<span data-ttu-id="d7334-133">Nazwisko</span><span class="sxs-lookup"><span data-stu-id="d7334-133">LastName</span></span>|<span data-ttu-id="d7334-134">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-134">Smith</span></span>|<span data-ttu-id="d7334-135">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-135">Smith</span></span>|<span data-ttu-id="d7334-136">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-136">Smith</span></span>|  
|<span data-ttu-id="d7334-137">Imię</span><span class="sxs-lookup"><span data-stu-id="d7334-137">FirstName</span></span>|<span data-ttu-id="d7334-138">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-138">Bob</span></span>|<span data-ttu-id="d7334-139">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-139">Bob</span></span>|<span data-ttu-id="d7334-140">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-140">Bob</span></span>|  
  
 <span data-ttu-id="d7334-141">1 o godzinie: 01 Użytkownik2 odczytuje w tym samym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d7334-141">At 1:01 p.m., User2 reads the same row.</span></span>  
  
 <span data-ttu-id="d7334-142">1 o godzinie: 03, zmienia się Użytkownik2 **FirstName** z "Bob" do "Robert" i aktualizuje bazę danych.</span><span class="sxs-lookup"><span data-stu-id="d7334-142">At 1:03 p.m., User2 changes **FirstName** from "Bob" to "Robert" and updates the database.</span></span>  
  
|<span data-ttu-id="d7334-143">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="d7334-143">Column name</span></span>|<span data-ttu-id="d7334-144">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-144">Original value</span></span>|<span data-ttu-id="d7334-145">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-145">Current value</span></span>|<span data-ttu-id="d7334-146">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="d7334-146">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d7334-147">CustID</span><span class="sxs-lookup"><span data-stu-id="d7334-147">CustID</span></span>|<span data-ttu-id="d7334-148">101</span><span class="sxs-lookup"><span data-stu-id="d7334-148">101</span></span>|<span data-ttu-id="d7334-149">101</span><span class="sxs-lookup"><span data-stu-id="d7334-149">101</span></span>|<span data-ttu-id="d7334-150">101</span><span class="sxs-lookup"><span data-stu-id="d7334-150">101</span></span>|  
|<span data-ttu-id="d7334-151">Nazwisko</span><span class="sxs-lookup"><span data-stu-id="d7334-151">LastName</span></span>|<span data-ttu-id="d7334-152">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-152">Smith</span></span>|<span data-ttu-id="d7334-153">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-153">Smith</span></span>|<span data-ttu-id="d7334-154">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-154">Smith</span></span>|  
|<span data-ttu-id="d7334-155">Imię</span><span class="sxs-lookup"><span data-stu-id="d7334-155">FirstName</span></span>|<span data-ttu-id="d7334-156">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-156">Bob</span></span>|<span data-ttu-id="d7334-157">Robert</span><span class="sxs-lookup"><span data-stu-id="d7334-157">Robert</span></span>|<span data-ttu-id="d7334-158">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-158">Bob</span></span>|  
  
 <span data-ttu-id="d7334-159">Aktualizacja zakończy się pomyślnie, ponieważ oryginalne wartości, które ma Użytkownik2 pasuje do wartości w bazie danych w czasie aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="d7334-159">The update succeeds because the values in the database at the time of update match the original values that User2 has.</span></span>  
  
 <span data-ttu-id="d7334-160">1 o godzinie: 05 Użytkownik1 zmiany "Bob" imię "James" i podejmuje próbę zaktualizowania wiersza w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d7334-160">At 1:05 p.m., User1 changes "Bob"'s first name to "James" and tries to update the row.</span></span>  
  
|<span data-ttu-id="d7334-161">Nazwa kolumny</span><span class="sxs-lookup"><span data-stu-id="d7334-161">Column name</span></span>|<span data-ttu-id="d7334-162">Oryginalna wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-162">Original value</span></span>|<span data-ttu-id="d7334-163">Bieżąca wartość</span><span class="sxs-lookup"><span data-stu-id="d7334-163">Current value</span></span>|<span data-ttu-id="d7334-164">Wartość w bazie danych</span><span class="sxs-lookup"><span data-stu-id="d7334-164">Value in database</span></span>|  
|-----------------|--------------------|-------------------|-----------------------|  
|<span data-ttu-id="d7334-165">CustID</span><span class="sxs-lookup"><span data-stu-id="d7334-165">CustID</span></span>|<span data-ttu-id="d7334-166">101</span><span class="sxs-lookup"><span data-stu-id="d7334-166">101</span></span>|<span data-ttu-id="d7334-167">101</span><span class="sxs-lookup"><span data-stu-id="d7334-167">101</span></span>|<span data-ttu-id="d7334-168">101</span><span class="sxs-lookup"><span data-stu-id="d7334-168">101</span></span>|  
|<span data-ttu-id="d7334-169">Nazwisko</span><span class="sxs-lookup"><span data-stu-id="d7334-169">LastName</span></span>|<span data-ttu-id="d7334-170">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-170">Smith</span></span>|<span data-ttu-id="d7334-171">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-171">Smith</span></span>|<span data-ttu-id="d7334-172">Nowak</span><span class="sxs-lookup"><span data-stu-id="d7334-172">Smith</span></span>|  
|<span data-ttu-id="d7334-173">Imię</span><span class="sxs-lookup"><span data-stu-id="d7334-173">FirstName</span></span>|<span data-ttu-id="d7334-174">Bob</span><span class="sxs-lookup"><span data-stu-id="d7334-174">Bob</span></span>|<span data-ttu-id="d7334-175">James</span><span class="sxs-lookup"><span data-stu-id="d7334-175">James</span></span>|<span data-ttu-id="d7334-176">Robert</span><span class="sxs-lookup"><span data-stu-id="d7334-176">Robert</span></span>|  
  
 <span data-ttu-id="d7334-177">W tym momencie użytkownik User1 napotyka naruszenie optymistycznej współbieżności, ponieważ wartość w bazie danych ("Robert") nie jest zgodna z oryginalnej wartości, że użytkownik User1 oczekiwała ("Bob").</span><span class="sxs-lookup"><span data-stu-id="d7334-177">At this point, User1 encounters an optimistic concurrency violation because the value in the database ("Robert") no longer matches the original value that User1 was expecting ("Bob").</span></span> <span data-ttu-id="d7334-178">Naruszenie współbieżności po prostu informuje o tym, że aktualizacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="d7334-178">The concurrency violation simply lets you know that the update failed.</span></span> <span data-ttu-id="d7334-179">Teraz decyzja należy zastąpić zmiany dostarczonych przez Użytkownik2 ze zmianami, dostarczone przez użytkownika Użytkownik1 lub Anuluj zmiany przy użyciu konta użytkownik1.</span><span class="sxs-lookup"><span data-stu-id="d7334-179">The decision now needs to be made whether to overwrite the changes supplied by User2 with the changes supplied by User1, or to cancel the changes by User1.</span></span>  
  
## <a name="testing-for-optimistic-concurrency-violations"></a><span data-ttu-id="d7334-180">Testowanie pod kątem naruszeń optymistycznej współbieżności</span><span class="sxs-lookup"><span data-stu-id="d7334-180">Testing for Optimistic Concurrency Violations</span></span>  
 <span data-ttu-id="d7334-181">Istnieje kilka technik testowania dla naruszenia optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-181">There are several techniques for testing for an optimistic concurrency violation.</span></span> <span data-ttu-id="d7334-182">Jeden polega na tym kolumnę sygnatur czasowych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d7334-182">One involves including a timestamp column in the table.</span></span> <span data-ttu-id="d7334-183">Bazy danych zwykle zapewniają funkcje sygnatury czasowej, który może służyć do identyfikowania Data i godzina, kiedy rekord był ostatnio aktualizowany.</span><span class="sxs-lookup"><span data-stu-id="d7334-183">Databases commonly provide timestamp functionality that can be used to identify the date and time when the record was last updated.</span></span> <span data-ttu-id="d7334-184">Ta technika kolumnę sygnatur czasowych znajduje się w definicji tabeli.</span><span class="sxs-lookup"><span data-stu-id="d7334-184">Using this technique, a timestamp column is included in the table definition.</span></span> <span data-ttu-id="d7334-185">Zawsze wtedy, gdy rekord zostanie zaktualizowany, sygnatura czasowa jest aktualizowana w celu odzwierciedlenia bieżącej daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="d7334-185">Whenever the record is updated, the timestamp is updated to reflect the current date and time.</span></span> <span data-ttu-id="d7334-186">W teście naruszeń optymistycznej współbieżności kolumnę sygnatur czasowych, jest zwracany za pomocą dowolnego zapytania zawartość tabeli.</span><span class="sxs-lookup"><span data-stu-id="d7334-186">In a test for optimistic concurrency violations, the timestamp column is returned with any query of the contents of the table.</span></span> <span data-ttu-id="d7334-187">Próba aktualizacji wartości sygnatur czasowych w bazie danych jest porównywany oryginalna wartość sygnatury czasowej znajdujących się w wierszu zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="d7334-187">When an update is attempted, the timestamp value in the database is compared to the original timestamp value contained in the modified row.</span></span> <span data-ttu-id="d7334-188">Jeśli są zgodne, wykonywania aktualizacji, a kolumny sygnatur czasowych zostanie zaktualizowany bieżący czas w celu uwzględnienia aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="d7334-188">If they match, the update is performed and the timestamp column is updated with the current time to reflect the update.</span></span> <span data-ttu-id="d7334-189">Jeśli nie są zgodne, wystąpiło naruszenie optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-189">If they do not match, an optimistic concurrency violation has occurred.</span></span>  
  
 <span data-ttu-id="d7334-190">Inna technika testowanie pod kątem naruszenie optymistycznej współbieżności jest Sprawdź, czy wszystkie oryginalne wartości kolumn w wierszu nadal odpowiadają tych dostępnych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="d7334-190">Another technique for testing for an optimistic concurrency violation is to verify that all the original column values in a row still match those found in the database.</span></span> <span data-ttu-id="d7334-191">Na przykład należy wziąć pod uwagę następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="d7334-191">For example, consider the following query:</span></span>  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 <span data-ttu-id="d7334-192">Do testowania naruszenie optymistycznej współbieżności podczas aktualizowania wiersza w **Tabela1**, czy wystawiać następującą instrukcję aktualizacji:</span><span class="sxs-lookup"><span data-stu-id="d7334-192">To test for an optimistic concurrency violation when updating a row in **Table1**, you would issue the following UPDATE statement:</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 <span data-ttu-id="d7334-193">Tak długo, jak oryginalne wartości odpowiadają wartościom w bazie danych, aktualizacja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="d7334-193">As long as the original values match the values in the database, the update is performed.</span></span> <span data-ttu-id="d7334-194">W przypadku modyfikowania wartość aktualizacji nie będą modyfikować wiersza, ponieważ klauzula WHERE nie znajdzie dopasowania.</span><span class="sxs-lookup"><span data-stu-id="d7334-194">If a value has been modified, the update will not modify the row because the WHERE clause will not find a match.</span></span>  
  
 <span data-ttu-id="d7334-195">Należy pamiętać, że zalecane jest zawsze zwracać unikatowe wartości klucza podstawowego w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="d7334-195">Note that it is recommended to always return a unique primary key value in your query.</span></span> <span data-ttu-id="d7334-196">W przeciwnym razie poprzednich instrukcji UPDATE może być aktualizowana więcej niż jeden wiersz, który może nie być zgodne z zamiarami użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d7334-196">Otherwise, the preceding UPDATE statement may update more than one row, which might not be your intent.</span></span>  
  
 <span data-ttu-id="d7334-197">Kolumny w źródle danych dopuszcza wartości null, może być konieczne rozszerzenie usługi klauzuli WHERE, aby wyszukać pasujące odwołanie o wartości null w Twojej lokalnej tabeli, a w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d7334-197">If a column at your data source allows nulls, you may need to extend your WHERE clause to check for a matching null reference in your local table and at the data source.</span></span> <span data-ttu-id="d7334-198">Na przykład następującą instrukcję aktualizacji sprawdza, czy odwołanie o wartości null w wierszu lokalne nadal odpowiada odwołanie o wartości null w źródle danych, lub że wartość w lokalnych wierszu nadal odpowiada wartości w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="d7334-198">For example, the following UPDATE statement verifies that a null reference in the local row still matches a null reference at the data source, or that the value in the local row still matches the value at the data source.</span></span>  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 <span data-ttu-id="d7334-199">Można również zastosować mniej restrykcyjne uprawnienia kryteria, korzystając z modelu optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-199">You may also choose to apply less restrictive criteria when using an optimistic concurrency model.</span></span> <span data-ttu-id="d7334-200">Na przykład za pomocą tylko kolumny klucza podstawowego w klauzuli WHERE powoduje, że dane zostaną zastąpione, niezależnie od tego, czy inne kolumny zostały zaktualizowane od czasu ostatniego zapytania.</span><span class="sxs-lookup"><span data-stu-id="d7334-200">For example, using only the primary key columns in the WHERE clause causes the data to be overwritten regardless of whether the other columns have been updated since the last query.</span></span> <span data-ttu-id="d7334-201">Klauzula WHERE można również zastosować tylko do określonych kolumn skutkuje danych zostaną zastąpione, chyba że niektóre pola zostały zaktualizowane od czasu ostatniego wykonano.</span><span class="sxs-lookup"><span data-stu-id="d7334-201">You can also apply a WHERE clause only to specific columns, resulting in data being overwritten unless particular fields have been updated since they were last queried.</span></span>  
  
### <a name="the-dataadapterrowupdated-event"></a><span data-ttu-id="d7334-202">Zdarzenie DataAdapter.RowUpdated</span><span class="sxs-lookup"><span data-stu-id="d7334-202">The DataAdapter.RowUpdated Event</span></span>  
 <span data-ttu-id="d7334-203">**RowUpdated** zdarzenia <xref:System.Data.Common.DataAdapter> obiekt może być używany w połączeniu z technik opisanych wcześniej, aby powiadomienie do aplikacji naruszeń optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-203">The **RowUpdated** event of the <xref:System.Data.Common.DataAdapter> object can be used in conjunction with the techniques described earlier, to provide notification to your application of optimistic concurrency violations.</span></span> <span data-ttu-id="d7334-204">**RowUpdated** występuje po każdej próby zaktualizowania **zmodyfikowane** wiersz z tabeli **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="d7334-204">**RowUpdated** occurs after each attempt to update a **Modified** row from a **DataSet**.</span></span> <span data-ttu-id="d7334-205">Dzięki temu można dodać kodu specjalnej obsługi, w tym przetwarzanie, gdy wystąpi wyjątek, dodawania niestandardowej informacji o błędzie, dodanie logiki ponawiania prób i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="d7334-205">This enables you to add special handling code, including processing when an exception occurs, adding custom error information, adding retry logic, and so on.</span></span> <span data-ttu-id="d7334-206"><xref:System.Data.Common.RowUpdatedEventArgs> Zwraca obiekt **RecordsAffected** Właściwość zawierająca liczby wierszy na polecenie określonej aktualizacji dla zmodyfikowanych wierszy w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d7334-206">The <xref:System.Data.Common.RowUpdatedEventArgs> object returns a **RecordsAffected** property containing the number of rows affected by a particular update command for a modified row in a table.</span></span> <span data-ttu-id="d7334-207">Ustawiając polecenia update do testowania optymistycznej współbieżności **RecordsAffected** właściwości co w efekcie zwróci wartość 0, jeśli nastąpiło naruszenie zasad optymistycznej współbieżności, ponieważ żadne rekordy nie zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="d7334-207">By setting the update command to test for optimistic concurrency, the **RecordsAffected** property will, as a result, return a value of 0 when an optimistic concurrency violation has occurred, because no records were updated.</span></span> <span data-ttu-id="d7334-208">Jeśli jest to możliwe, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d7334-208">If this is the case, an exception is thrown.</span></span> <span data-ttu-id="d7334-209">**RowUpdated** zdarzenie pozwala na obsługę tego wystąpienia i uniknąć wyjątek, ustawiając odpowiednią **RowUpdatedEventArgs.Status** wartości, takich jak  **UpdateStatus.SkipCurrentRow**.</span><span class="sxs-lookup"><span data-stu-id="d7334-209">The **RowUpdated** event enables you to handle this occurrence and avoid the exception by setting an appropriate **RowUpdatedEventArgs.Status** value, such as **UpdateStatus.SkipCurrentRow**.</span></span> <span data-ttu-id="d7334-210">Aby uzyskać więcej informacji na temat **RowUpdated** zdarzeń, zobacz [Obsługa zdarzeń elementu DataAdapter](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="d7334-210">For more information about the **RowUpdated** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
 <span data-ttu-id="d7334-211">Opcjonalnie możesz ustawić **DataAdapter.ContinueUpdateOnError** do **true**, przed wywołaniem **aktualizacji**i reagować na informacje o błędzie, przechowywane w **RowError** właściwości określonego wiersza, kiedy **aktualizacji** zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d7334-211">Optionally, you can set **DataAdapter.ContinueUpdateOnError** to **true**, before calling **Update**, and respond to the error information stored in the **RowError** property of a particular row when the **Update** is completed.</span></span> <span data-ttu-id="d7334-212">Aby uzyskać więcej informacji, zobacz [informacje o błędzie wiersza](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span><span class="sxs-lookup"><span data-stu-id="d7334-212">For more information, see [Row Error Information](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md).</span></span>  
  
## <a name="optimistic-concurrency-example"></a><span data-ttu-id="d7334-213">Przykład optymistycznej współbieżności</span><span class="sxs-lookup"><span data-stu-id="d7334-213">Optimistic Concurrency Example</span></span>  
 <span data-ttu-id="d7334-214">Poniżej przedstawiono prosty przykład, który ustawia **elementu UpdateCommand** z **DataAdapter** do testowania optymistycznej współbieżności, a następnie używa **RowUpdated** zdarzeń do testowania naruszenia optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-214">The following is a simple example that sets the **UpdateCommand** of a **DataAdapter** to test for optimistic concurrency, and then uses the **RowUpdated** event to test for optimistic concurrency violations.</span></span> <span data-ttu-id="d7334-215">W przypadku naruszenia optymistycznej współbieżności, aplikacja ustawia **RowError** wiersza, który aktualizacji został wystawiony dla, aby odzwierciedlić naruszenie optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="d7334-215">When an optimistic concurrency violation is encountered, the application sets the **RowError** of the row that the update was issued for to reflect an optimistic concurrency violation.</span></span>  
  
 <span data-ttu-id="d7334-216">Należy zauważyć, że wartości parametrów przekazanych do klauzuli WHERE polecenia UPDATE są mapowane na **oryginalnego** wartościami odpowiednimi kolumnami.</span><span class="sxs-lookup"><span data-stu-id="d7334-216">Note that the parameter values passed to the WHERE clause of the UPDATE command are mapped to the **Original** values of their respective columns.</span></span>  
  
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
Dim parameter As SqlParameter = dataSet.UpdateCommand.Parameters.Add( _  
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
  
## <a name="see-also"></a><span data-ttu-id="d7334-217">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7334-217">See Also</span></span>  
 [<span data-ttu-id="d7334-218">Pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d7334-218">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="d7334-219">Aktualizowanie źródeł danych za pomocą elementów DataAdapters</span><span class="sxs-lookup"><span data-stu-id="d7334-219">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 [<span data-ttu-id="d7334-220">Informacje o błędzie wiersza</span><span class="sxs-lookup"><span data-stu-id="d7334-220">Row Error Information</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 [<span data-ttu-id="d7334-221">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="d7334-221">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="d7334-222">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="d7334-222">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
