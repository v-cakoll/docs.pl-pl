---
title: Przykład LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 5f39db9e-0e62-42c9-8c98-bb8b54cec98c
ms.openlocfilehash: 83dc8433459f64860baaca2e8309fbc85e2bb3a2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515371"
---
# <a name="linq-to-sql-sample"></a><span data-ttu-id="8179c-102">Przykład LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8179c-102">LINQ to SQL Sample</span></span>
<span data-ttu-id="8179c-103">W tym przykładzie pokazano, jak utworzyć działanie używać programu LINQ do jednostek zapytania SQL z tabel bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8179c-103">This sample demonstrates how to create an activity to use LINQ to SQL query entities from tables in SQL Server databases.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8179c-104">Przykłady WCF może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8179c-104">The WCF samples may already be installed on your machine.</span></span> <span data-ttu-id="8179c-105">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8179c-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardspace`  
>   
>  <span data-ttu-id="8179c-106">Jeśli ten katalog nie istnieje, kliknij link pobierania próbki, w górnej części tej strony.</span><span class="sxs-lookup"><span data-stu-id="8179c-106">If this directory does not exist, click the download sample link at the top of this page.</span></span> <span data-ttu-id="8179c-107">Należy pamiętać, że ten link pobiera i instaluje wszystkie [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, i [!INCLUDE[infocard](../../../../includes/infocard-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="8179c-107">Note that this link downloads and installs all of the [!INCLUDE[wf1](../../../../includes/wf1-md.md)], WCF, and [!INCLUDE[infocard](../../../../includes/infocard-md.md)] samples.</span></span> <span data-ttu-id="8179c-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8179c-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\Samples\WCFWFCardSpace\WF\Scenario\ActivityLibrary\Linq\LinqToSql`  
  
## <a name="activity-details-for-findinsqltable"></a><span data-ttu-id="8179c-109">Szczegóły działań dla FindInSqlTable</span><span class="sxs-lookup"><span data-stu-id="8179c-109">Activity details for FindInSqlTable</span></span>  
 <span data-ttu-id="8179c-110">To działanie umożliwia użytkownikom wykonywanie zapytań dotyczących jednostek z tabel w bazie danych za pomocą LINQ to SQL.</span><span class="sxs-lookup"><span data-stu-id="8179c-110">This activity allows users to query entities from tables in a database using LINQ to SQL.</span></span> <span data-ttu-id="8179c-111">Użytkownicy, działania mogą także podać predykat LINQ w postaci wyrażenia lambda do filtrowania wyników.</span><span class="sxs-lookup"><span data-stu-id="8179c-111">Users of the activity can also provide a LINQ predicate in the form of a lambda expression to filter the results.</span></span> <span data-ttu-id="8179c-112">Jeśli nie podano żadnych predykat, zwracany jest całą tabelę.</span><span class="sxs-lookup"><span data-stu-id="8179c-112">If no predicate is provided, the entire table is returned.</span></span> <span data-ttu-id="8179c-113">W poniższej tabeli przedstawiono właściwości i zwrócenie wartości dla działania.</span><span class="sxs-lookup"><span data-stu-id="8179c-113">The following table details the property and return values for the activity.</span></span>  
  
|<span data-ttu-id="8179c-114">Właściwości lub wartości zwracanej</span><span class="sxs-lookup"><span data-stu-id="8179c-114">Property or Return Value</span></span>|<span data-ttu-id="8179c-115">Opis</span><span class="sxs-lookup"><span data-stu-id="8179c-115">Description</span></span>|  
|------------------------------|-----------------|  
|<span data-ttu-id="8179c-116">`Collection` Właściwość</span><span class="sxs-lookup"><span data-stu-id="8179c-116">`Collection` property</span></span>|<span data-ttu-id="8179c-117">Wymagana właściwość, która określa, kolekcji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="8179c-117">A required property that specifies the source collection.</span></span>|  
|<span data-ttu-id="8179c-118">`Predicate` Właściwość</span><span class="sxs-lookup"><span data-stu-id="8179c-118">`Predicate` property</span></span>|<span data-ttu-id="8179c-119">Wymagana właściwość, która określa filtr dla kolekcji w postaci wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="8179c-119">A required property that specifies the filter for the collection in the form of a lambda expression.</span></span>|  
|<span data-ttu-id="8179c-120">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8179c-120">Return Value</span></span>|<span data-ttu-id="8179c-121">Kolekcja filtrowane.</span><span class="sxs-lookup"><span data-stu-id="8179c-121">The filtered collection.</span></span>|  
  
## <a name="code-sample-that-uses-the-custom-activity"></a><span data-ttu-id="8179c-122">Przykładowy kod, który używa działania niestandardowe</span><span class="sxs-lookup"><span data-stu-id="8179c-122">Code Sample that uses the Custom Activity</span></span>  
 <span data-ttu-id="8179c-123">Poniższy przykład kodu wykorzystuje `FindInSqlTable` niestandardowe działanie, aby znaleźć wszystkie wiersze w tabeli programu SQL Server o nazwie `Employee` gdzie `Role` kolumny jest równa `SDE`.</span><span class="sxs-lookup"><span data-stu-id="8179c-123">The following code example uses the `FindInSqlTable` custom activity to find all rows in a SQL Server table named `Employee` where the `Role` column is equal to `SDE`.</span></span>  
  
```csharp  
new FindInSqlTable<Employee>   
{  
    ConnectionString = @"Data Source=.\SQLExpress;Initial Catalog=LinqToSqlSample;Integrated Security=True",                          
    Predicate = new LambdaValue<Func<Employee, bool>>(c => new Func<Employee, bool>(emp => emp.Role.Equals("SDE"))),  
    Result = new OutArgument<IList<Employee>>(employees)  
},  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="8179c-124">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="8179c-124">To use this sample</span></span>  
  
1.  <span data-ttu-id="8179c-125">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="8179c-125">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="8179c-126">Przejdź do folderu, który zawiera ten przykład.</span><span class="sxs-lookup"><span data-stu-id="8179c-126">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="8179c-127">Uruchom plik Setup.cmd pliku polecenia.</span><span class="sxs-lookup"><span data-stu-id="8179c-127">Run the Setup.cmd command file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8179c-128">Plik Setup.cmd skrypt próbuje zainstalować przykładową bazę danych na komputerze lokalnym programu SQL Server Express.</span><span class="sxs-lookup"><span data-stu-id="8179c-128">The Setup.cmd script attempts to install the sample database in your local machine SQL Server Express.</span></span> <span data-ttu-id="8179c-129">Jeśli chcesz zainstalować go w inne wystąpienie programu SQL server, należy edytować plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8179c-129">If you want to install it in other SQL server instance, edit Setup.cmd.</span></span>  
  
     <span data-ttu-id="8179c-130">Skrypt plik Setup.cmd wykonuje następujące akcje.:</span><span class="sxs-lookup"><span data-stu-id="8179c-130">The Setup.cmd script does the following actions.:</span></span>  
  
    -   <span data-ttu-id="8179c-131">Tworzy bazę danych o nazwie LinqToSqlSample.</span><span class="sxs-lookup"><span data-stu-id="8179c-131">Creates a database called LinqToSqlSample.</span></span>  
  
    -   <span data-ttu-id="8179c-132">Tworzy tabelę ról.</span><span class="sxs-lookup"><span data-stu-id="8179c-132">Creates a Roles table.</span></span>  
  
    -   <span data-ttu-id="8179c-133">Tworzy tabelę Pracownicy.</span><span class="sxs-lookup"><span data-stu-id="8179c-133">Creates an Employees table.</span></span>  
  
    -   <span data-ttu-id="8179c-134">Wstawia 3 rekordy w tabeli ról.</span><span class="sxs-lookup"><span data-stu-id="8179c-134">Inserts 3 records into the Roles table.</span></span>  
  
    -   <span data-ttu-id="8179c-135">Wstawia 12 rekordów do tabel pracownikami.</span><span class="sxs-lookup"><span data-stu-id="8179c-135">Inserts 12 records into the Employees table.</span></span>  
  
4.  <span data-ttu-id="8179c-136">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik rozwiązania LinqToSQL.sln.</span><span class="sxs-lookup"><span data-stu-id="8179c-136">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the LinqToSQL.sln solution file.</span></span>  
  
5.  <span data-ttu-id="8179c-137">Aby skompilować rozwiązanie, naciśnij klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="8179c-137">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="8179c-138">Aby uruchomić rozwiązanie, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="8179c-138">To run the solution, press F5.</span></span>  
  
#### <a name="to-uninstall-the-linqtosql-sample-database"></a><span data-ttu-id="8179c-139">Aby odinstalować LinqToSql przykładowej bazy danych</span><span class="sxs-lookup"><span data-stu-id="8179c-139">To uninstall the LinqToSql sample database</span></span>  
  
1.  <span data-ttu-id="8179c-140">Otwórz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="8179c-140">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="8179c-141">Przejdź do folderu, który zawiera ten przykład.</span><span class="sxs-lookup"><span data-stu-id="8179c-141">Navigate to the folder that contains this sample.</span></span>  
  
3.  <span data-ttu-id="8179c-142">Uruchom plik polecenia Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="8179c-142">Run the Cleanup.cmd command file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8179c-143">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8179c-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8179c-144">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="8179c-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8179c-145">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="8179c-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8179c-146">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="8179c-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\Liiinq\LinqToSql`  
  
## <a name="see-also"></a><span data-ttu-id="8179c-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8179c-147">See Also</span></span>  
 [<span data-ttu-id="8179c-148">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="8179c-148">LINQ to SQL</span></span>](https://go.microsoft.com/fwlink/?LinkId=150376)  
 [<span data-ttu-id="8179c-149">Wprowadzenie (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="8179c-149">Getting Started (LINQ to SQL)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150377)
