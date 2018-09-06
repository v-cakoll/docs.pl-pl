---
title: Działanie promocji właściwości
ms.date: 03/30/2017
ms.assetid: 802196b7-1159-4c05-b41b-d3bfdfcc88d9
ms.openlocfilehash: 6e059a0d344e6c62833feaa890c459c141a49673
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870087"
---
# <a name="property-promotion-activity"></a><span data-ttu-id="796e5-102">Działanie promocji właściwości</span><span class="sxs-lookup"><span data-stu-id="796e5-102">Property Promotion Activity</span></span>
<span data-ttu-id="796e5-103">W tym przykładzie zapewnia rozwiązania end-to-end, która integruje się <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu bezpośrednio do tworzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-103">This sample provides an end-to-end solution that integrates the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature directly into the workflow authoring experience.</span></span> <span data-ttu-id="796e5-104">Kolekcja elementów konfiguracji, działania przepływu pracy i rozszerzeń przepływu pracy, które upraszczają korzystanie z funkcji podwyższania poziomu są dostarczane.</span><span class="sxs-lookup"><span data-stu-id="796e5-104">A collection of configuration elements, workflow activities, and workflow extensions that simplify the use of the Promotion feature are provided.</span></span> <span data-ttu-id="796e5-105">Ponadto przykład zawiera prostego przepływu pracy, który demonstruje sposób skorzystania z tej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="796e5-105">Additionally, the sample contains a simple workflow that demonstrates how to use this collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="796e5-106">Przykłady są udostępniane wyłącznie w celach edukacyjnych.</span><span class="sxs-lookup"><span data-stu-id="796e5-106">Samples are provided for educational purposes only.</span></span> <span data-ttu-id="796e5-107">Nie są przeznaczone dla środowiska produkcyjnego i nie zostały przetestowane w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="796e5-107">They are not intended for a production environment, and have not been tested in a production environment.</span></span> <span data-ttu-id="796e5-108">Firma Microsoft zapewnia pomoc techniczną tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="796e5-108">Microsoft does not provide technical support for these samples.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="796e5-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="796e5-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="796e5-110">Zainicjowana klasa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych</span><span class="sxs-lookup"><span data-stu-id="796e5-110">An initialized <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database</span></span>  
  
-   [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)]  
  
## <a name="sample-projects"></a><span data-ttu-id="796e5-111">Przykładowe projekty</span><span class="sxs-lookup"><span data-stu-id="796e5-111">Sample Projects</span></span>  
  
-   <span data-ttu-id="796e5-112">**PropertyPromotionActivity** projekt zawiera pliki odnoszących się do elementów konfiguracji specyficznej dla podwyższania poziomu, działania przepływu pracy i rozszerzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-112">The **PropertyPromotionActivity** project contains files pertaining to the promotion-specific configuration elements, workflow activities, and workflow extensions.</span></span>  
  
-   <span data-ttu-id="796e5-113">**CounterServiceApplication** projekt zawiera przykładowy przepływ pracy, który używa **SqlWorkflowInstanceStorePromotion** projektu.</span><span class="sxs-lookup"><span data-stu-id="796e5-113">The **CounterServiceApplication** project contains a sample workflow that uses the **SqlWorkflowInstanceStorePromotion** project.</span></span>  
  
-   <span data-ttu-id="796e5-114">Skrypt SQL (PropertyPromotionActivitySQLSample.sql), które muszą być uruchamiane względem <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> bazy danych.</span><span class="sxs-lookup"><span data-stu-id="796e5-114">A SQL script (PropertyPromotionActivitySQLSample.sql) that must be run against the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> database.</span></span>  
  
-   <span data-ttu-id="796e5-115">Plik rozwiązania, który łączy dwie [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projektów (`PropertyPromotionActivity.sln`)</span><span class="sxs-lookup"><span data-stu-id="796e5-115">A solution file that links the two [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] projects (`PropertyPromotionActivity.sln`)</span></span>  
  
## <a name="to-set-up-and-run-the-sample"></a><span data-ttu-id="796e5-116">Aby skonfigurować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="796e5-116">To set up and run the sample</span></span>  
  
1.  <span data-ttu-id="796e5-117">Inicjowanie bazy danych trwałości przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-117">Initialize a workflow persistence database.</span></span>  
  
    1.  <span data-ttu-id="796e5-118">Przejdź do katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity), a następnie uruchom CreateInstanceStore.cmd.</span><span class="sxs-lookup"><span data-stu-id="796e5-118">Navigate to the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity) and run CreateInstanceStore.cmd.</span></span>  
  
    2.  <span data-ttu-id="796e5-119">Jeśli uprawnienia administratora nie są dostępne, należy utworzyć identyfikator logowania programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="796e5-119">If Administrator privileges are not available, create a SQL Server login.</span></span> <span data-ttu-id="796e5-120">SQL Server Management Studio, przejdź do **zabezpieczeń**, **logowania**.</span><span class="sxs-lookup"><span data-stu-id="796e5-120">In SQL Server Management Studio, go to **Security**, **Logins**.</span></span> <span data-ttu-id="796e5-121">Kliknij prawym przyciskiem myszy **logowania** i Utwórz nową nazwę logowania.</span><span class="sxs-lookup"><span data-stu-id="796e5-121">Right-click **Logins** and create a new login.</span></span> <span data-ttu-id="796e5-122">Dodaj użytkownika listy ACL do roli programu SQL, otwierając **baz danych**, **objekt InstanceStore**, **zabezpieczeń**.</span><span class="sxs-lookup"><span data-stu-id="796e5-122">Add your ACL user to the SQL role by opening **Databases**, **InstanceStore**, **Security**.</span></span> <span data-ttu-id="796e5-123">Kliknij prawym przyciskiem myszy **użytkowników** i wybierz **nowego użytkownika**.</span><span class="sxs-lookup"><span data-stu-id="796e5-123">Right-click **Users** and select **New user**.</span></span> <span data-ttu-id="796e5-124">Ustaw **nazwa logowania** użytkownika utworzonego powyżej.</span><span class="sxs-lookup"><span data-stu-id="796e5-124">Set the **Login name** to the user created above.</span></span> <span data-ttu-id="796e5-125">Dodaj użytkownika do członkostwo roli bazy danych System.Activities.DurableInstancing.InstanceStoreUsers (i inne).</span><span class="sxs-lookup"><span data-stu-id="796e5-125">Add the user to the Database role membership System.Activities.DurableInstancing.InstanceStoreUsers (and others).</span></span> <span data-ttu-id="796e5-126">Należy pamiętać, że użytkownik może istnieć już (na przykład użytkownik dbo).</span><span class="sxs-lookup"><span data-stu-id="796e5-126">Note that the user might exist already (for example, user dbo).</span></span>  
  
2.  <span data-ttu-id="796e5-127">Otwórz plik rozwiązania PropertyPromotionActivity.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="796e5-127">Open the PropertyPromotionActivity.sln solution file in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="796e5-128">Jeśli utworzono magazyn wystąpienia w bazie danych innych niż lokalna instalacja programu SQL Server Express, należy zaktualizować parametry połączenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="796e5-128">If you created the instance store in a database other than a local installation of SQL Server Express, then you must update the database connection string.</span></span> <span data-ttu-id="796e5-129">Instrukcja ALTER pliku App.config, w obszarze **CounterServiceApplication** , ustawiając wartość `connectionString` atrybutu na `sqlWorkflowInstanceStorePromotion` węzła, które wskazuje do bazy danych trwałości, który został zainicjowany w kroku 1.</span><span class="sxs-lookup"><span data-stu-id="796e5-129">Alter the App.config file under the **CounterServiceApplication** by setting the value of the `connectionString` attribute on the `sqlWorkflowInstanceStorePromotion` node so that it points to the persistence database that was initialized in step 1.</span></span>  
  
4.  <span data-ttu-id="796e5-130">Skompiluj i uruchom rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="796e5-130">Build and run the solution.</span></span> <span data-ttu-id="796e5-131">Spowoduje to uruchomienie usługi programu WF licznika i automatyczne uruchamianie wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-131">This will start the Counter WF service and automatically start a workflow instance.</span></span>  
  
5.  <span data-ttu-id="796e5-132">Szybko wybrać wszystkie wiersze, w [dbo]. Widok [counterService] w bazie danych trwałości (ten widok został dodany, uruchamiając CreateInstanceStore.cmd w kroku 1).</span><span class="sxs-lookup"><span data-stu-id="796e5-132">Quickly select all the rows in the [dbo].[CounterService] view in your persistence database (this view was added by running CreateInstanceStore.cmd in step 1).</span></span> <span data-ttu-id="796e5-133">Zostanie wyświetlony zestaw podobne do następujących wyników:</span><span class="sxs-lookup"><span data-stu-id="796e5-133">You will see a result set similar to the following:</span></span>  
  
    |<span data-ttu-id="796e5-134">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="796e5-134">InstanceId</span></span>|<span data-ttu-id="796e5-135">CounterValue</span><span class="sxs-lookup"><span data-stu-id="796e5-135">CounterValue</span></span>|<span data-ttu-id="796e5-136">CounterValueLastUpdated</span><span class="sxs-lookup"><span data-stu-id="796e5-136">CounterValueLastUpdated</span></span>|  
    |----------------|------------------|-----------------------------|  
    |<span data-ttu-id="796e5-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span><span class="sxs-lookup"><span data-stu-id="796e5-137">2FA2C302-929E-4C0D-8C25-768A3DA20CE5</span></span>|<span data-ttu-id="796e5-138">12</span><span class="sxs-lookup"><span data-stu-id="796e5-138">12</span></span>|<span data-ttu-id="796e5-139">2010-02-18 22:48:01.740</span><span class="sxs-lookup"><span data-stu-id="796e5-139">2010-02-18 22:48:01.740</span></span>|  
  
     <span data-ttu-id="796e5-140">Jak zachować odświeżyć widok, można zauważyć, że CounterValue i CounterValueLastUpdated zmienić co 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="796e5-140">As you keep refreshing the view, you will notice that CounterValue and CounterValueLastUpdated change every two seconds.</span></span> <span data-ttu-id="796e5-141">Jest to interwał, w którym licznik aktualizuje się samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="796e5-141">This is the interval at which the counter updates itself.</span></span> <span data-ttu-id="796e5-142">CounterValue i właściwości reprezentują promowane CounterValueLastUpdated dla tego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-142">CounterValue and CounterValueLastUpdated represent promoted properties for this workflow.</span></span>  
  
## <a name="to-remove-the-sample"></a><span data-ttu-id="796e5-143">Aby usunąć próbki</span><span class="sxs-lookup"><span data-stu-id="796e5-143">To remove the sample</span></span>  
  
-   <span data-ttu-id="796e5-144">Uruchom RemoveInstanceStore.cmd w katalogu próbki (\WF\Basic\Persistence\PropertyPromotionActivity).</span><span class="sxs-lookup"><span data-stu-id="796e5-144">Run RemoveInstanceStore.cmd in the sample directory (\WF\Basic\Persistence\PropertyPromotionActivity).</span></span>  
  
## <a name="understanding-this-sample"></a><span data-ttu-id="796e5-145">Opis tego przykładu</span><span class="sxs-lookup"><span data-stu-id="796e5-145">Understanding This Sample</span></span>  
 <span data-ttu-id="796e5-146">Przykład zawiera dwa projekty i plik SQL:</span><span class="sxs-lookup"><span data-stu-id="796e5-146">The sample contains two projects and an SQL file:</span></span>  
  
-   <span data-ttu-id="796e5-147">**CounterServiceApplication** to aplikacja konsoli, która udostępnia prostą usługę WF licznika.</span><span class="sxs-lookup"><span data-stu-id="796e5-147">**CounterServiceApplication** is a console application that hosts a simple Counter WF service.</span></span> <span data-ttu-id="796e5-148">Po odebraniu komunikatu jednokierunkowe za pośrednictwem `Start` punktu końcowego, przepływ pracy liczby z zakresu od 0 do 29, zwiększając zmiennej licznika co 2 sekundy.</span><span class="sxs-lookup"><span data-stu-id="796e5-148">Upon receiving a one-way message through the `Start` endpoint, the workflow counts from 0 to 29, incrementing a counter variable every two seconds.</span></span> <span data-ttu-id="796e5-149">Po co zwiększenie licznika przepływ pracy będzie się powtarzać, a podwyższone właściwości są aktualizowane w [dbo]. Widok [counterService].</span><span class="sxs-lookup"><span data-stu-id="796e5-149">After every counter increment, the workflow persists, and the promoted properties are updated in the [dbo].[CounterService] view.</span></span> <span data-ttu-id="796e5-150">Po uruchomieniu aplikacji konsoli hostuje usługę WF i wysyła komunikat do `Start` punktu końcowego, tworząc wystąpienie licznika WF.</span><span class="sxs-lookup"><span data-stu-id="796e5-150">When the console application is run, it hosts the WF service and sends a message to the `Start` endpoint, creating a Counter WF instance.</span></span>  
  
-   <span data-ttu-id="796e5-151">**PropertyPromotionActivity** to biblioteka klasy, która zawiera elementy konfiguracji, działania przepływu pracy i rozszerzenia przepływu pracy, **CounterServiceApplication** używa.</span><span class="sxs-lookup"><span data-stu-id="796e5-151">**PropertyPromotionActivity** is a class library that contains the configuration elements, workflow activities, and workflow extensions that the **CounterServiceApplication** uses.</span></span>  
  
-   <span data-ttu-id="796e5-152">**PropertyPromotionActivitySQLSample.sql** tworzy i dodaje widok [dbo]. [ CounterService] w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="796e5-152">**PropertyPromotionActivitySQLSample.sql** creates and adds the view [dbo].[CounterService] to the database.</span></span>  
  
### <a name="counterserviceapplication"></a><span data-ttu-id="796e5-153">CounterServiceApplication</span><span class="sxs-lookup"><span data-stu-id="796e5-153">CounterServiceApplication</span></span>  
  
#### <a name="using-the-sqlworkflowinstancestorepromotion-configuration-element"></a><span data-ttu-id="796e5-154">Za pomocą SqlWorkflowInstanceStorePromotion elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="796e5-154">Using the SqlWorkflowInstanceStorePromotion Configuration Element</span></span>  
 <span data-ttu-id="796e5-155">`SqlWorkflowInstanceStorePromotion` Dziedziczy po elemencie konfiguracji `SqlWorkflowInstanceStore` element konfiguracji, ale dodaje element dodatkowe czynności konfiguracyjne o nazwie `promotionSets`.</span><span class="sxs-lookup"><span data-stu-id="796e5-155">The `SqlWorkflowInstanceStorePromotion` configuration element inherits from the `SqlWorkflowInstanceStore` configuration element, but adds an additional configuration element called `promotionSets`.</span></span> <span data-ttu-id="796e5-156">`promotionSets` Element umożliwia użytkownikowi określenie właściwości o podwyższonym poziomie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="796e5-156">The `promotionSets` element enables the user to specify promoted properties through configuration.</span></span> <span data-ttu-id="796e5-157">Jest to plik konfiguracyjny, który jest używany przez przykładowy:</span><span class="sxs-lookup"><span data-stu-id="796e5-157">This is the configuration file that is used by the sample:</span></span>  
  
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
  
 <span data-ttu-id="796e5-158">Sprawdź definicję [dbo]. Widok [counterService].</span><span class="sxs-lookup"><span data-stu-id="796e5-158">Examine the definition for the [dbo].[CounterService] view.</span></span>  
  
```sql  
create view [dbo].[CounterService] as  
      select [InstanceId],  
 [Value1] as [CounterValue],  
 [Value2] as [CounterValueLastUpdated]  
      from [System.Activities.DurableInstancing].[InstancePromotedProperties]  
      where [PromotionName] = 'CounterService'  
go  
```  
  
 <span data-ttu-id="796e5-159">Gdy wystąpienie przepływu pracy będzie się powtarzać, zostanie wstawiona do `InstancePromotedProperties` Wyświetl dla każdego `PromotionSet` zdefiniowane w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="796e5-159">When a workflow instance persists, a row is inserted into the `InstancePromotedProperties` view for each `PromotionSet` defined in the configuration.</span></span> <span data-ttu-id="796e5-160">Ten wiersz zawiera wszystkie o podwyższonym poziomie właściwości `PromotionSet` (podwyższony jedną właściwość w kolumnie).</span><span class="sxs-lookup"><span data-stu-id="796e5-160">This row contains all the promoted properties of the `PromotionSet` (one promoted property per column).</span></span> <span data-ttu-id="796e5-161">To `PromotionSet` jest kluczach krotki: `InstanceId, PromotionName`.</span><span class="sxs-lookup"><span data-stu-id="796e5-161">This `PromotionSet` is keyed by the tuple: `InstanceId, PromotionName`.</span></span> <span data-ttu-id="796e5-162">W tym przykładzie mamy jeden `PromotionSet` zdefiniowane w konfiguracji, których atrybut name jest `CounterService`.</span><span class="sxs-lookup"><span data-stu-id="796e5-162">In this sample, we have one `PromotionSet` defined in configuration whose name attribute is `CounterService`.</span></span> <span data-ttu-id="796e5-163">Uwaga jak `PromotionName` wartość kolumny jest równa atrybut name elementu `PromotionSet` elementu.</span><span class="sxs-lookup"><span data-stu-id="796e5-163">Note how the `PromotionName` column value is equal to the name attribute of the `PromotionSet` element.</span></span>  
  
 <span data-ttu-id="796e5-164">Kolejność `promotedValue` elementy mają związek z położenie o podwyższonym poziomie właściwości w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="796e5-164">The order of the `promotedValue` elements correlates with the placement of the promoted properties in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="796e5-165">`Count` jest to pierwszy `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="796e5-165">`Count` is the first `promotedValue` element.</span></span> <span data-ttu-id="796e5-166">W rezultacie jest mapowany na `Value1` kolumny w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="796e5-166">As a result, it is mapped to the `Value1` column in the `InstancePromotedProperties` view.</span></span> <span data-ttu-id="796e5-167">`LastIncrementedAt` jest to druga `promotedValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="796e5-167">`LastIncrementedAt` is the second `promotedValue` element.</span></span> <span data-ttu-id="796e5-168">W rezultacie jest mapowany na `Value2` kolumny w `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="796e5-168">As a result, it is mapped to the `Value2` column in the `InstancePromotedProperties` view.</span></span>  
  
#### <a name="using-the-promotevalue-activity"></a><span data-ttu-id="796e5-169">Przy użyciu działania PromoteValue</span><span class="sxs-lookup"><span data-stu-id="796e5-169">Using the PromoteValue Activity</span></span>  
 <span data-ttu-id="796e5-170">Zapoznaj się z plikiem CounterService.xamlx w Projektancie Windows Workflow Foundation.</span><span class="sxs-lookup"><span data-stu-id="796e5-170">Examine the CounterService.xamlx file in the Windows Workflow Foundation Designer.</span></span> <span data-ttu-id="796e5-171">Zwróć uwagę, że istnieją dwa specjalne działania w definicji WF: `PromoteValue<DateTime>` i `PromoteValue<Int32>`.</span><span class="sxs-lookup"><span data-stu-id="796e5-171">Notice that there are two special activities in the WF definition: `PromoteValue<DateTime>` and `PromoteValue<Int32>`.</span></span>  
  
 <span data-ttu-id="796e5-172">`PromoteValue<Int32>` Działanie ma jego `Name` zdefiniowany jako element członkowski `Count`.</span><span class="sxs-lookup"><span data-stu-id="796e5-172">The `PromoteValue<Int32>` activity has its `Name` member defined as `Count`.</span></span> <span data-ttu-id="796e5-173">To jest zgodny z pierwszym `promotedValue` element w konfiguracji i ma jego `Value` zdefiniowany jako `Counter` zmiennej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-173">This matches with the first `promotedValue` element in the configuration, and has its `Value` defined as the `Counter` workflow variable.</span></span> <span data-ttu-id="796e5-174">Gdy przepływ pracy będzie się powtarzać, `Counter` zmiennej przepływu pracy jest trwały jako właściwości z podwyższonym poziomem do `Value1` kolumny `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="796e5-174">When the workflow persists, the `Counter` workflow variable is persisted as a promoted property into the `Value1` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="796e5-175">`PromoteValue<DateTime>` Działanie ma jego `Name` zdefiniowany jako element członkowski `LastIncrementedAt`.</span><span class="sxs-lookup"><span data-stu-id="796e5-175">The `PromoteValue<DateTime>` activity has its `Name` member defined as `LastIncrementedAt`.</span></span> <span data-ttu-id="796e5-176">Odpowiada to drugi `promotedValue` element w konfiguracji i jego `Value` zdefiniowany jako `TimeLastIncremented` zmiennej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-176">This matches with the second `promotedValue` element in the configuration, and has its `Value` defined as the `TimeLastIncremented` workflow variable.</span></span> <span data-ttu-id="796e5-177">Oznacza to, że gdy przepływ pracy będzie się powtarzać, wartość `TimeLastIncremented` zmiennej przepływu pracy zostaną utrwalone jako właściwości z podwyższonym poziomem do `Value2` kolumny `InstancePromotedProperties` widoku.</span><span class="sxs-lookup"><span data-stu-id="796e5-177">This means that when the workflow persists, the value for the `TimeLastIncremented` workflow variable will be persisted as a promoted property into the `Value2` column of the `InstancePromotedProperties` view.</span></span>  
  
 <span data-ttu-id="796e5-178">Należy pamiętać, że `PromotedValue` działanie ma również logiczna składową o nazwie `ClearExistingPromotedData`.</span><span class="sxs-lookup"><span data-stu-id="796e5-178">Note that the `PromotedValue` activity also has a Boolean member called `ClearExistingPromotedData`.</span></span> <span data-ttu-id="796e5-179">Gdy ten element członkowski jest ustawiona na `true`, czyści wszystkie wartości właściwości z podwyższonym poziomem do tego punktu w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-179">When this member is set to `true`, this clears all the promoted property values up to that point in the workflow.</span></span> <span data-ttu-id="796e5-180">Na przykład jeśli działanie sekwencji jest zdefiniowany jako następująco:</span><span class="sxs-lookup"><span data-stu-id="796e5-180">For example, if a Sequence activity is defined as follows:</span></span>  
  
1.  <span data-ttu-id="796e5-181">PromoteValue {nazwa = "Count", wartość = 3}</span><span class="sxs-lookup"><span data-stu-id="796e5-181">PromoteValue { Name = "Count", Value = 3}</span></span>  
  
2.  <span data-ttu-id="796e5-182">PromoteValue {nazwa = "LastIncrementedAt", wartość = 1-1-2000}</span><span class="sxs-lookup"><span data-stu-id="796e5-182">PromoteValue {Name = "LastIncrementedAt", Value = 1-1-2000 }</span></span>  
  
3.  <span data-ttu-id="796e5-183">Utrwalanie</span><span class="sxs-lookup"><span data-stu-id="796e5-183">Persist</span></span>  
  
4.  <span data-ttu-id="796e5-184">PromoteValue {nazwa = "Count", wartość = 4, ClearExistingPromotedData = true}</span><span class="sxs-lookup"><span data-stu-id="796e5-184">PromoteValue {Name = "Count", Value = 4, ClearExistingPromotedData = true}</span></span>  
  
5.  <span data-ttu-id="796e5-185">Utrwalanie</span><span class="sxs-lookup"><span data-stu-id="796e5-185">Persist</span></span>  
  
 <span data-ttu-id="796e5-186">Na drugiej utrwalanie, wartość o podwyższonym poziomie `Count` będzie równa 4.</span><span class="sxs-lookup"><span data-stu-id="796e5-186">On the second persist, the promoted value for `Count` will be 4.</span></span> <span data-ttu-id="796e5-187">Jednak wartość o podwyższonym poziomie `LastIncrementedAt` będzie `NULL`.</span><span class="sxs-lookup"><span data-stu-id="796e5-187">However, the promoted value for `LastIncrementedAt` will be `NULL`.</span></span> <span data-ttu-id="796e5-188">Jeśli `ClearExistingPromotedData` nie został ustawiony na `true` w kroku 4, po drugim utrwalanie, o podwyższonym poziomie wartość licznika będzie 4.</span><span class="sxs-lookup"><span data-stu-id="796e5-188">If `ClearExistingPromotedData` was not set to `true` for step 4, then after the second persist, the promoted value for Count would be 4.</span></span> <span data-ttu-id="796e5-189">W wyniku wartość o podwyższonym poziomie `LastIncrementedAt` nadal będzie 1-1-2000.</span><span class="sxs-lookup"><span data-stu-id="796e5-189">As a result, the promoted value for `LastIncrementedAt` would still be 1-1-2000.</span></span>  
  
### <a name="propertypromotionactivity"></a><span data-ttu-id="796e5-190">PropertyPromotionActivity</span><span class="sxs-lookup"><span data-stu-id="796e5-190">PropertyPromotionActivity</span></span>  
 <span data-ttu-id="796e5-191">Ta biblioteka klas zawiera następujące klasy publiczne można uproszczenie użytkowania <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> funkcja podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="796e5-191">This class library contains the following public classes to simplify use of the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Promotion feature.</span></span>  
  
#### <a name="promotevalue-class"></a><span data-ttu-id="796e5-192">Klasa PromoteValue</span><span class="sxs-lookup"><span data-stu-id="796e5-192">PromoteValue Class</span></span>  
 <span data-ttu-id="796e5-193">Ta klasa promuje jedną właściwość.</span><span class="sxs-lookup"><span data-stu-id="796e5-193">This class promotes one property.</span></span> <span data-ttu-id="796e5-194">Nazwa właściwości z podwyższonym poziomem powinny odpowiadać nazwa atrybutu `promotedValue` element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="796e5-194">The name of the promoted property should match a name attribute of a `promotedValue` element in the configuration.</span></span> <span data-ttu-id="796e5-195">To działanie może być używane w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-195">This activity can be used in the Workflow Designer.</span></span> <span data-ttu-id="796e5-196">Zobacz CounterServiceApplication, na przykład użycia.</span><span class="sxs-lookup"><span data-stu-id="796e5-196">See the CounterServiceApplication for an example usage.</span></span>  
  
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
  
 <span data-ttu-id="796e5-197">ClearExistingPromotedData (wartość logiczna)</span><span class="sxs-lookup"><span data-stu-id="796e5-197">ClearExistingPromotedData (Bool)</span></span>  
 <span data-ttu-id="796e5-198">Czyści wszystkie wartości, które były promowane przed tym działaniem.</span><span class="sxs-lookup"><span data-stu-id="796e5-198">Clears all values that were promoted before this activity.</span></span>  
  
 <span data-ttu-id="796e5-199">Nazwa (ciąg)</span><span class="sxs-lookup"><span data-stu-id="796e5-199">Name (string)</span></span>  
 <span data-ttu-id="796e5-200">Nazwa która reprezentuje tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="796e5-200">The name that represents this property.</span></span> <span data-ttu-id="796e5-201">Powinien on odpowiadać atrybut name elementu \<promotedValue > element w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="796e5-201">This should match the name attribute of a \<promotedValue> element in the configuration.</span></span>  
  
 <span data-ttu-id="796e5-202">Wartość (InArgument\<T >)</span><span class="sxs-lookup"><span data-stu-id="796e5-202">Value (InArgument\<T>)</span></span>  
 <span data-ttu-id="796e5-203">Zmienna / wartość, że chcesz przechowywać w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="796e5-203">The variable / value that you want to store in the column.</span></span>  
  
#### <a name="promotevalues-class"></a><span data-ttu-id="796e5-204">Klasa PromoteValues</span><span class="sxs-lookup"><span data-stu-id="796e5-204">PromoteValues Class</span></span>  
 <span data-ttu-id="796e5-205">Wspiera wiele właściwości.</span><span class="sxs-lookup"><span data-stu-id="796e5-205">Promotes multiple properties.</span></span> <span data-ttu-id="796e5-206">Nazwy właściwości o podwyższonym poziomie powinny odpowiadać wszystkie atrybuty nazwy w `promotedValue` elementów w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="796e5-206">The names of the promoted properties should match all name attributes in the `promotedValue` elements in the configuration.</span></span> <span data-ttu-id="796e5-207">Użycie jest podobny do `PromoteValue` działań, z wyjątkiem fakt, że wiele właściwości atrybutu może być podwyższony, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="796e5-207">Usage is similar to the `PromoteValue` activity, except for the fact that multiple properties can be promoted at the same time.</span></span> <span data-ttu-id="796e5-208">To działanie nie może być używane w Projektancie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-208">This activity cannot be used in the Workflow Designer.</span></span>  
  
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
  
#### <a name="sqlworkflowinstancestorepromotionbehavior"></a><span data-ttu-id="796e5-209">SqlWorkflowInstanceStorePromotionBehavior</span><span class="sxs-lookup"><span data-stu-id="796e5-209">SqlWorkflowInstanceStorePromotionBehavior</span></span>  
 <span data-ttu-id="796e5-210">Pochodzi od klasy `SqlWorkflowInstanceStoreBehavior`.</span><span class="sxs-lookup"><span data-stu-id="796e5-210">Derives from `SqlWorkflowInstanceStoreBehavior`.</span></span> <span data-ttu-id="796e5-211">Ta klasa pochodna dodaje niestandardowego uczestnika stanów trwałych (również część z tej biblioteki) jako rozszerzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="796e5-211">This derived class adds a custom persistence participant (also a part of this library) as a workflow extension.</span></span> <span data-ttu-id="796e5-212">Implementacja poprzednich dwóch działań przepływu pracy, zależy od tego niestandardowego uczestnika stanów trwałych.</span><span class="sxs-lookup"><span data-stu-id="796e5-212">The implementation of the previous two workflow activities relies on this custom persistence participant.</span></span>  
  
```  
public class SqlWorkflowInstanceStorePromotionBehavior :  
             SqlWorkflowInstanceStoreBehavior, IServiceBehavior  
{  
        public void Promote(string name, IEnumerable<string> promoteAsSqlVariant,  
                            IEnumerable<string> promoteAsBinary)  
  
}  
```  
  
 <span data-ttu-id="796e5-213">Ta biblioteka klas zawiera także `ConfigurationElement` implementację `SqlWorkflowInstanceStorePromotionElement` i niestandardowego uczestnika stanów trwałych używany przez poprzednie działania podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="796e5-213">This class library also contains the `ConfigurationElement` implementation for the `SqlWorkflowInstanceStorePromotionElement` and a custom persistence participant used by the previous promotion activities.</span></span>  
  
### <a name="propertypromotionactivitysqlsample"></a><span data-ttu-id="796e5-214">PropertyPromotionActivitySQLSample</span><span class="sxs-lookup"><span data-stu-id="796e5-214">PropertyPromotionActivitySQLSample</span></span>  
 <span data-ttu-id="796e5-215">Ten plik SQL tworzy `[dbo].[CounterService]` wyświetlanie oprócz `[InstancePromotedProperties]` widoku dla zapytań, wszystkie wystąpienia, które mają zestaw CounterService podwyższania poziomu.</span><span class="sxs-lookup"><span data-stu-id="796e5-215">This SQL file creates a `[dbo].[CounterService]` view in addition to the `[InstancePromotedProperties]` view for querying all instances that have a CounterService Promotion set.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="796e5-216">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="796e5-216">The samples may already be installed on your computer.</span></span> <span data-ttu-id="796e5-217">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne):</span><span class="sxs-lookup"><span data-stu-id="796e5-217">Check for the following (default) directory before continuing:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="796e5-218">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="796e5-218">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="796e5-219">W tym przykładzie znajduje się w następującym katalogu:</span><span class="sxs-lookup"><span data-stu-id="796e5-219">This sample is located in the following directory:</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\PropertyPromotionActivity`  
  
## <a name="see-also"></a><span data-ttu-id="796e5-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="796e5-220">See Also</span></span>  
 [<span data-ttu-id="796e5-221">Przykłady trwałości i hostingu AppFabric</span><span class="sxs-lookup"><span data-stu-id="796e5-221">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
