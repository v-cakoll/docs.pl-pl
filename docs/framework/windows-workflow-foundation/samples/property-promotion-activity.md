---
title: Właściwości działania podwyższania poziomu
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 46e74c8c479e545778db92e15de3cb8798dafa11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-promotion-activity"></a><span data-ttu-id="7b260-102">Właściwości działania podwyższania poziomu</span><span class="sxs-lookup"><span data-stu-id="7b260-102">Property Promotion Activity</span></span>
<span data-ttu-id="7b260-103">W tym przykładzie przedstawiono rozwiązanie end-to-end, która integruje się <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu bezpośrednio do tworzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="7b260-104">Podano w kolekcji elementów konfiguracji, działań przepływu pracy i rozszerzeń przepływu pracy, które ułatwiają korzystanie z funkcji podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="7b260-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="7b260-105">Ponadto próbka zawiera proste przepływu pracy, który pokazuje, jak użyć tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7b260-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b260-106">Przykłady są udostępniane tylko na potrzeby edukacyjne.</span><span class="sxs-lookup"><span data-stu-id="7b260-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="7b260-107">Nie są przeznaczone dla środowiska produkcyjnego i nie zostały przetestowane w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="7b260-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="7b260-108">Firma Microsoft nie zapewnia pomoc techniczną dla tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="7b260-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b260-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7b260-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="7b260-110">Zainicjowana klasa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych</span><span class="sxs-lookup"><span data-stu-id="7b260-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="7b260-111">Przykładowych projektach</span><span class="sxs-lookup"><span data-stu-id="7b260-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="7b260-112">**PropertyPromotionActivity** projekt zawiera pliki należące do elementów konfiguracji dotyczące podwyższania poziomu, działań przepływu pracy i rozszerzeń przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="7b260-113">**CounterServiceApplication** projekt zawiera przykładowego przepływu pracy, który używa **SqlWorkflowInstanceStorePromotion** projektu.</span><span class="sxs-lookup"><span data-stu-id="7b260-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="7b260-114">Skrypt SQL (PropertyPromotionActivitySQLSample.sql), które muszą być uruchamiane przed <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7b260-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="7b260-115">Plik rozwiązania, które łączy dwa [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projektów (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="7b260-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="7b260-116">Aby skonfigurować i uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="7b260-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="7b260-117">Zainicjuj bazę danych trwałości przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="7b260-118">Przejdź do katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity), a następnie uruchom CreateInstanceStore.cmd.</span><span class="sxs-lookup"><span data-stu-id="7b260-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="7b260-119">Jeśli uprawnienia administratora nie są dostępne, Utwórz dane logowania programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7b260-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="7b260-120">SQL Server Management Studio, przejdź do **zabezpieczeń**, **logowania**.</span><span class="sxs-lookup"><span data-stu-id="7b260-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="7b260-121">Kliknij prawym przyciskiem myszy **logowania** i Utwórz nowe dane logowania.</span><span class="sxs-lookup"><span data-stu-id="7b260-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="7b260-122">Dodaj listę kontroli dostępu użytkownika do roli SQL, otwierając **baz danych**, **InstanceStore**, **zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="7b260-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="7b260-123">Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="7b260-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="7b260-124">Ustaw **nazwa logowania** użytkownikowi utworzone powyżej.</span><span class="sxs-lookup"><span data-stu-id="7b260-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="7b260-125">Dodaj użytkownika do członkostwo roli bazy danych System.Activities.DurableInstancing.InstanceStoreUsers (i inne).</span><span class="sxs-lookup"><span data-stu-id="7b260-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="7b260-126">Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownika dbo).</span><span class="sxs-lookup"><span data-stu-id="7b260-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="7b260-127">Otwórz plik rozwiązania PropertyPromotionActivity.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7b260-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="7b260-128">Jeśli w bazie danych innych niż lokalnej instalacji programu SQL Server Express został utworzony w magazynie wystąpień, należy zaktualizować parametry połączenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7b260-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="7b260-129">Zmiany w pliku App.config **CounterServiceApplication** przez ustawienie wartości `connectionString` atrybutu `sqlWorkflowInstanceStorePromotion` węzła tak, aby wskazywało do bazy danych trwałości, który został zainicjowany w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="7b260-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="7b260-130">Tworzenie i uruchamianie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="7b260-130">Build and run the solution.</span></span> <span data-ttu-id="7b260-131">Spowoduje uruchomienie usługi WF licznik i automatyczne uruchamianie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="7b260-132">Szybko zaznaczyć wszystkie wiersze w [dbo]. Widok [counterService] w bazie danych trwałości (w tym widoku został dodany przez uruchomienie CreateInstanceStore.cmd w kroku 1).</span><span class="sxs-lookup"><span data-stu-id="7b260-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="7b260-133">Zostanie wyświetlony zestaw podobne do następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="7b260-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="7b260-134">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="7b260-134">InstanceId</span></span>|<span data-ttu-id="7b260-135">Równowartości</span><span class="sxs-lookup"><span data-stu-id="7b260-135">CounterValue</span></span>|<span data-ttu-id="7b260-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="7b260-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="7b260-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="7b260-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="7b260-138">12</span><span class="sxs-lookup"><span data-stu-id="7b260-138">12</span></span>|<span data-ttu-id="7b260-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="7b260-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="7b260-140">Jak należy odświeżyć widok, można zauważyć, że równowartości i CounterValueLastUpdated zmienić co dwie sekundy.</span><span class="sxs-lookup"><span data-stu-id="7b260-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="7b260-141">Jest to interwał, w którym licznik aktualizuje się samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="7b260-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="7b260-142">Równowartości i CounterValueLastUpdated reprezentują awansowanej właściwości dla tego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="7b260-143">Aby usunąć próbki</span><span class="sxs-lookup"><span data-stu-id="7b260-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="7b260-144">Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity).</span><span class="sxs-lookup"><span data-stu-id="7b260-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="7b260-145">Opis tego przykładu</span><span class="sxs-lookup"><span data-stu-id="7b260-145">Understanding This Sample</span></span>  
 <span data-ttu-id="7b260-146">Próbka zawiera dwa projekty i pliku SQL:</span><span class="sxs-lookup"><span data-stu-id="7b260-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="7b260-147">**CounterServiceApplication** jest aplikacja konsolowa, która obsługuje prosty usługę WF licznika.</span><span class="sxs-lookup"><span data-stu-id="7b260-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="7b260-148">Po otrzymaniu komunikat jednokierunkowy za pośrednictwem `Start` punktu końcowego, przepływu pracy liczby z zakresu od 0 do 29 wartości zmiennej licznika co dwie sekundy.</span><span class="sxs-lookup"><span data-stu-id="7b260-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="7b260-149">Po każdym przyrost liczników przepływ pracy będzie się powtarzać, a awansowanej właściwości są aktualizowane w [dbo]. Widok [counterService].</span><span class="sxs-lookup"><span data-stu-id="7b260-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="7b260-150">Po uruchomieniu aplikacji konsoli, obsługuje usługę WF i wysyła komunikat do `Start` punktu końcowego, tworzenie wystąpienia licznika WF.</span><span class="sxs-lookup"><span data-stu-id="7b260-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="7b260-151">**PropertyPromotionActivity** Biblioteka klasy, która zawiera elementy konfiguracji, działań przepływu pracy i przepływ pracy rozszerzenia który **CounterServiceApplication** używa.</span><span class="sxs-lookup"><span data-stu-id="7b260-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="7b260-152">**PropertyPromotionActivitySQLSample.sql** tworzy i dodaje widoku [dbo]. [ CounterService] w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="7b260-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="7b260-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="7b260-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="7b260-154">Za pomocą SqlWorkflowInstanceStorePromotion elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7b260-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="7b260-155">`SqlWorkflowInstanceStorePromotion` Dziedziczy po elemencie konfiguracji `SqlWorkflowInstanceStore` element konfiguracji, ale dodaje element dodatkowe czynności konfiguracyjne o nazwie `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="7b260-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="7b260-156">`promotionSets` Element umożliwia użytkownikowi określenie awansowanej właściwości konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b260-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="7b260-157">To jest plik konfiguracji, który jest używany przez próbki:</span><span class="sxs-lookup"><span data-stu-id="7b260-157">This is the configuration file that is used by the sample:</span></span>  
  
```xml  
<sqlWorkflowInstanceStorePromotion connectionString ="Data Source=.;Initial Catalog=SqlWorkflowInstanceStoreTest;Integrated Security=True;">  
  <promotionSets>  
    <promotionSet name="CounterService">  
      <promotedValue propertyName="Count"/>  
      <promotedValue propertyName="LastIncrementedAt"/>  
    </promotionSet>  
  </promotionSets>  
</sqlWorkflowInstanceStorePromotion>  
```  
  
 <span data-ttu-id="7b260-158">Sprawdź, czy definicja [dbo]. Widok [counterService].</span><span class="sxs-lookup"><span data-stu-id="7b260-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="7b260-159">Po wystąpienia przepływu pracy będzie się powtarzać, wiersza są wstawiane do `InstancePromotedProperties` wyświetlić dla każdego `PromotionSet` zdefiniowanych w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b260-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="7b260-160">Ten wiersz zawiera wszystkie awansowanej właściwości `PromotionSet` (jeden poziom jest podwyższany właściwości dla kolumny).</span><span class="sxs-lookup"><span data-stu-id="7b260-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="7b260-161">To `PromotionSet` jest klucze w postaci spójnej kolekcji: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="7b260-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="7b260-162">W tym przykładzie mamy jedną `PromotionSet` zdefiniowanych w konfiguracji, których atrybut name jest `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="7b260-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="7b260-163">Uwaga jak `PromotionName` wartość kolumny jest taki sam atrybut name elementu `PromotionSet` elementu.</span><span class="sxs-lookup"><span data-stu-id="7b260-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="7b260-164">Kolejność `promotedValue` elementy są powiązane z umieszczania awansowanej właściwości w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="7b260-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="7b260-165">`Count` jest to pierwszy `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="7b260-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="7b260-166">W związku z tym jest zamapowany na `Value1` kolumny w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="7b260-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="7b260-167">`LastIncrementedAt` jest to druga `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="7b260-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="7b260-168">W związku z tym jest zamapowany na `Value2` kolumny w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="7b260-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="7b260-169">Za pomocą działania PromoteValue</span><span class="sxs-lookup"><span data-stu-id="7b260-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="7b260-170">Zapoznaj się z plikiem CounterService.xamlx w Projektancie Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="7b260-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="7b260-171">Zwróć uwagę, że istnieją dwa specjalne działania w definicji WF: `PromoteValue<DateTime>` i `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="7b260-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="7b260-172">`PromoteValue<Int32>` Działanie ma jego `Name` zdefiniowany jako element członkowski `Count`.</span><span class="sxs-lookup"><span data-stu-id="7b260-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="7b260-173">To jest zgodny z pierwszym `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `Counter` zmiennej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="7b260-174">Gdy przepływ pracy będzie się powtarzać, `Counter` zmiennej przepływu pracy jest utrwalony jako awansowanej właściwości do `Value1` kolumny `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="7b260-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="7b260-175">`PromoteValue<DateTime>` Działanie ma jego `Name` zdefiniowany jako element członkowski `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="7b260-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="7b260-176">To jest zgodny z drugą `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `TimeLastIncremented` zmiennej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="7b260-177">Oznacza to, że gdy przepływ pracy będzie się powtarzać, wartość `TimeLastIncremented` zostaną utrwalone zmiennej przepływu pracy jako awansowanej właściwości do `Value2` kolumny `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="7b260-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="7b260-178">Należy pamiętać, że `PromotedValue` działanie ma również element członkowski logiczną o nazwie `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="7b260-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="7b260-179">Jeśli ten element członkowski ma wartość `true`, czyści wszystkie wartości awansowanej właściwości do tego punktu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="7b260-180">Na przykład jeśli nie zdefiniowano działania Sequence jako następująco:</span><span class="sxs-lookup"><span data-stu-id="7b260-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="7b260-181">PromoteValue {nazwa = "Count", wartość = 3}</span><span class="sxs-lookup"><span data-stu-id="7b260-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="7b260-182">PromoteValue {nazwa = "LastIncrementedAt", wartość = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="7b260-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="7b260-183">Utrwalanie</span><span class="sxs-lookup"><span data-stu-id="7b260-183">Persist</span></span>  
  
4.  <span data-ttu-id="7b260-184">PromoteValue {nazwa = "Count", wartość = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="7b260-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="7b260-185">Utrwalanie</span><span class="sxs-lookup"><span data-stu-id="7b260-185">Persist</span></span>  
  
 <span data-ttu-id="7b260-186">Na drugim utrwalania, awansowana wartość `Count` będzie 4.</span><span class="sxs-lookup"><span data-stu-id="7b260-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="7b260-187">Jednak wartość awansowana `LastIncrementedAt` będzie `NULL`.</span><span class="sxs-lookup"><span data-stu-id="7b260-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="7b260-188">Jeśli `ClearExistingPromotedData` nie został ustawiony na `true` w kroku 4, następnie po drugim będzie nadal występować, awansowana wartość liczba będzie równa 4.</span><span class="sxs-lookup"><span data-stu-id="7b260-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="7b260-189">W wyniku wartość awansowana `LastIncrementedAt` nadal będzie 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="7b260-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="7b260-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="7b260-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="7b260-191">Ta biblioteka klasy zawiera następujące klasy publicznej ułatwiających korzystanie z <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="7b260-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="7b260-192">Klasa PromoteValue</span><span class="sxs-lookup"><span data-stu-id="7b260-192">PromoteValue Class</span></span>  
 <span data-ttu-id="7b260-193">Ta klasa zamienia jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="7b260-193">This class promotes one property.</span></span> <span data-ttu-id="7b260-194">Nazwa awansowanej właściwości powinny odpowiadać atrybut nazwy `promotedValue` element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b260-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="7b260-195">To działanie może być używane w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="7b260-196">Zobacz CounterServiceApplication, na przykład użycia.</span><span class="sxs-lookup"><span data-stu-id="7b260-196">See the CounterServiceApplication for an example usage.</span></span>  
  
```csharp  
public class PromoteValue<T> : CodeActivity  
{  
    public PromoteValue()  
    {  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public string Name { get; set; }  
    public InArgument<T> Value { get; set; }  
}  
```  
  
 <span data-ttu-id="7b260-197">ClearExistingPromotedData (wartość logiczna)</span><span class="sxs-lookup"><span data-stu-id="7b260-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="7b260-198">Czyści wszystkie wartości, które zostały awansowane przed tego działania.</span><span class="sxs-lookup"><span data-stu-id="7b260-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="7b260-199">Nazwa (ciąg)</span><span class="sxs-lookup"><span data-stu-id="7b260-199">Name (string)</span></span>  
 <span data-ttu-id="7b260-200">Nazwa, która reprezentuje tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b260-200">The name that represents this property.</span></span> <span data-ttu-id="7b260-201">Atrybut name elementu powinna odpowiadać \<promotedValue > element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b260-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="7b260-202">Wartość (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="7b260-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="7b260-203">Zmienna-wartość chcesz przechowywać w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="7b260-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="7b260-204">Klasa PromoteValues</span><span class="sxs-lookup"><span data-stu-id="7b260-204">PromoteValues Class</span></span>  
 <span data-ttu-id="7b260-205">Zamienia wiele właściwości.</span><span class="sxs-lookup"><span data-stu-id="7b260-205">Promotes multiple properties.</span></span> <span data-ttu-id="7b260-206">Nazwy awansowanej właściwości powinny być zgodne wszystkie atrybuty nazwy w `promotedValue` elementów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7b260-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="7b260-207">Użycie jest podobny do `PromoteValue` działania, z wyjątkiem fakt, że można podwyższyć wiele właściwości w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="7b260-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="7b260-208">Nie można użyć tego działania w Projektancie przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
```  
public class PromoteValues : CodeActivity  
{  
    public PromoteValues()  
    {  
        this.ValuesToPromote = new Dictionary<string, InArgument>();  
    }  
  
    public bool ClearExistingPromotedData { get; set; }  
    public IDictionary<string, InArgument> ValuesToPromote { get; set; }  
}  
```  
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="7b260-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="7b260-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="7b260-210">Pochodną `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="7b260-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="7b260-211">Ta klasa pochodna dodaje uczestnika trwałości niestandardowe (również jest częścią tej biblioteki) jako rozszerzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7b260-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="7b260-212">Wykonanie poprzednich dwóch działań przepływu pracy zależy od tego uczestnika trwałości niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="7b260-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="7b260-213">Biblioteka ta klasa zawiera także `ConfigurationElement` implementację `SqlWorkflowInstanceStorePromotionElement` i uczestnika trwałości niestandardowy używany przez poprzednie działania podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="7b260-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="7b260-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="7b260-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="7b260-215">Ten plik SQL tworzy `[dbo].[CounterService]` wyświetlić oprócz `[InstancePromotedProperties]` widoku do wykonywania zapytań wszystkich wystąpień, które mają zestaw CounterService podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="7b260-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7b260-216">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="7b260-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7b260-217">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="7b260-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7b260-218">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="7b260-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7b260-219">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="7b260-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="7b260-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b260-220">See Also</span></span>  
 [<span data-ttu-id="7b260-221">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="7b260-221">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
