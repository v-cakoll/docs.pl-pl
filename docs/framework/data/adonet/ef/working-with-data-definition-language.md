---
title: Praca z językiem definicji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 75a214ad1099bf48dcb2c2d3b36bf07dc0524f8d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313245"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="1e649-102">Praca z językiem definicji danych</span><span class="sxs-lookup"><span data-stu-id="1e649-102">Working with Data Definition Language</span></span>
<span data-ttu-id="1e649-103">Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w wersji 4 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje języka definicji danych (DDL).</span><span class="sxs-lookup"><span data-stu-id="1e649-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="1e649-104">Dzięki temu można utworzyć lub usunąć wystąpienie bazy danych na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="1e649-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="1e649-105">Następujące metody w <xref:System.Data.Objects.ObjectContext> za pomocą parametrów połączenia i zawartości SSDL wykonywać następujące czynności: Tworzenie lub usuwanie bazy danych, sprawdź, czy baza danych istnieje i wyświetlić wygenerowany skrypt języka DDL:</span><span class="sxs-lookup"><span data-stu-id="1e649-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="1e649-106">Wykonywanie polecenia języka DDL zakłada wystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="1e649-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="1e649-107">Metody wymienione wcześniej delegować większość pracy do podstawowego dostawcy danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="1e649-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="1e649-108">Jest odpowiedzialny za dostawcy upewnij się, że Konwencja nazewnictwa służącego do generowania obiektów bazy danych zgodne z konwencjami, używane do tworzenia zapytań i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="1e649-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="1e649-109">Poniższy przykład pokazuje, jak wygenerować bazy danych na podstawie istniejącego modelu.</span><span class="sxs-lookup"><span data-stu-id="1e649-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="1e649-110">On również dodaje nowy obiekt jednostki do kontekstu obiektów i zapisuje je w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="1e649-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="1e649-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="1e649-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="1e649-112">Aby zdefiniować bazę danych na podstawie istniejącego modelu</span><span class="sxs-lookup"><span data-stu-id="1e649-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="1e649-113">Utwórz aplikację konsoli.</span><span class="sxs-lookup"><span data-stu-id="1e649-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="1e649-114">Dodawanie istniejącego modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1e649-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="1e649-115">Dodaj pusty modelu o nazwie `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="1e649-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="1e649-116">Aby utworzyć pusty model, zobacz [jak: Tworzenie nowego edmx pliku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) tematu.</span><span class="sxs-lookup"><span data-stu-id="1e649-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="1e649-117">Plik SchoolModel.edmx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="1e649-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="1e649-118">Skopiuj pojęciach, magazynu i mapowanie zawartości przez model do szkoły [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) tematu.</span><span class="sxs-lookup"><span data-stu-id="1e649-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2.  <span data-ttu-id="1e649-119">Otwórz plik SchoolModel.edmx i Wklej zawartość w ramach `edmx:Runtime` tagów.</span><span class="sxs-lookup"><span data-stu-id="1e649-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="1e649-120">Dodaj następujący kod do funkcji main.</span><span class="sxs-lookup"><span data-stu-id="1e649-120">Add the following code to your main function.</span></span> <span data-ttu-id="1e649-121">Ten kod inicjalizuje parametry połączenia z serwerem bazy danych, widoki, skrypt DDL tworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="1e649-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
