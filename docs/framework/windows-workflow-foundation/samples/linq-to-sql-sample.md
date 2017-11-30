---
title: "LINQ do SQL próbki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c05520dccdbf0677569d7fc64f55795e0ddb79b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="a089d-102">LINQ do SQL próbki</span><span class="sxs-lookup"><span data-stu-id="a089d-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="a089d-103">Ten przykład przedstawia sposób tworzenia działania, aby używać LINQ do jednostek zapytania SQL z tabel w bazach danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a089d-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a089d-104">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a089d-104">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] samples may already be installed on your machine.</span></span> <span data-ttu-id="a089d-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a089d-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="a089d-106">Jeśli ten katalog nie istnieje, kliknij łącze próbki pobierania w górnej części strony.</span><span class="sxs-lookup"><span data-stu-id="a089d-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="a089d-107">Należy pamiętać, że to łącze pobiera i instaluje wszystkie [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], i [!INCLUDE[infocard](../../../../includes/infocard-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a089d-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="a089d-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a089d-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="a089d-109">Szczegóły działania FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="a089d-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="a089d-110">To działanie umożliwia użytkownikom do jednostek zapytania z tabel w bazie danych przy użyciu składnika LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="a089d-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="a089d-111">Użytkownicy działania można też podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="a089d-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="a089d-112">Jeśli predykat nie zostanie podany, jest zwracana całą tabelę.</span><span class="sxs-lookup"><span data-stu-id="a089d-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="a089d-113">W poniższej tabeli przedstawiono wartości właściwości i przywrócenie działania.</span><span class="sxs-lookup"><span data-stu-id="a089d-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="a089d-114">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="a089d-114">Property or Return Value</span></span>|<span data-ttu-id="a089d-115">Opis</span><span class="sxs-lookup"><span data-stu-id="a089d-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="a089d-116">`Collection`Właściwość</span><span class="sxs-lookup"><span data-stu-id="a089d-116">`Collection` property</span></span>|<span data-ttu-id="a089d-117">Wymaganą właściwość, która określa kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="a089d-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="a089d-118">`Predicate`Właściwość</span><span class="sxs-lookup"><span data-stu-id="a089d-118">`Predicate` property</span></span>|<span data-ttu-id="a089d-119">Wymaganą właściwość, która określa filtr do kolekcji w postaci wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a089d-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="a089d-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a089d-120">Return Value</span></span>|<span data-ttu-id="a089d-121">Filtrowane kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a089d-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="a089d-122">Przykładem kodu, który używa działania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="a089d-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="a089d-123">Poniższy przykład kodu wykorzystuje `FindInSqlTable` działania niestandardowego można znaleźć wszystkie wiersze w tabeli programu SQL Server o nazwie `Employee` gdzie `Role` kolumny jest równa `SDE`.</span><span class="sxs-lookup"><span data-stu-id="a089d-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a089d-124">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="a089d-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="a089d-125">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="a089d-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="a089d-126">Przejdź do folderu, który zawiera ten przykład.</span><span class="sxs-lookup"><span data-stu-id="a089d-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="a089d-127">Uruchom plik polecenia Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a089d-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a089d-128">Skrypt Setup.cmd próbuje zainstalować przykładową bazę danych w komputerze lokalnym programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="a089d-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="a089d-129">Jeśli użytkownik chce go zainstalować w inne wystąpienie programu SQL server, należy edytować Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a089d-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="a089d-130">Skrypt Setup.cmd wykonuje następujące akcje.:</span><span class="sxs-lookup"><span data-stu-id="a089d-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="a089d-131">Tworzy bazę danych o nazwie LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="a089d-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="a089d-132">Tworzy tabelę ról.</span><span class="sxs-lookup"><span data-stu-id="a089d-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="a089d-133">Tworzy tabelę pracowników.</span><span class="sxs-lookup"><span data-stu-id="a089d-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="a089d-134">Wstawia 3 rekordy do tabeli ról.</span><span class="sxs-lookup"><span data-stu-id="a089d-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="a089d-135">Wstawia 12 rekordów do tabeli pracowników.</span><span class="sxs-lookup"><span data-stu-id="a089d-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="a089d-136">Przy użyciu [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="a089d-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="a089d-137">Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a089d-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="a089d-138">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="a089d-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="a089d-139">Aby odinstalować LinqToSql przykładowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="a089d-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="a089d-140">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="a089d-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="a089d-141">Przejdź do folderu, który zawiera ten przykład.</span><span class="sxs-lookup"><span data-stu-id="a089d-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="a089d-142">Uruchom plik polecenia Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="a089d-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a089d-143">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a089d-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a089d-144">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="a089d-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a089d-145">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="a089d-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a089d-146">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a089d-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="a089d-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a089d-147">See Also</span></span>  
 [<span data-ttu-id="a089d-148">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="a089d-148">LINQ to SQL</span></span>](http://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="a089d-149">Wprowadzenie (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="a089d-149">Getting Started (LINQ to SQL)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150377)
