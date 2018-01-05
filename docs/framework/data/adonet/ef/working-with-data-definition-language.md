---
title: "Praca z języka definicji danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 85c603d20e8b2e1936ac33773ad0b53a5a958e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="370f1-102">Praca z języka definicji danych</span><span class="sxs-lookup"><span data-stu-id="370f1-102">Working with Data Definition Language</span></span>
<span data-ttu-id="370f1-103">Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w wersji 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje języka definicji danych (DDL).</span><span class="sxs-lookup"><span data-stu-id="370f1-103">Starting with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="370f1-104">Umożliwia to tworzenie lub usuwanie wystąpienia bazy danych, na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="370f1-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="370f1-105">Następujących metod na <xref:System.Data.Objects.ObjectContext> Użyj parametrów połączenia i zawartość pliku SSDL, aby wykonać następujące czynności: Utwórz lub Usuń bazę danych, sprawdź, czy baza danych istnieje i wyświetlić wygenerowany skrypt DDL:</span><span class="sxs-lookup"><span data-stu-id="370f1-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  <span data-ttu-id="370f1-106">Wykonywanie polecenia języka DDL zakłada wystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="370f1-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="370f1-107">Metody wcześniej wymienione delegować większość pracy do podstawowego dostawcy danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="370f1-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="370f1-108">Jest dostawcy odpowiedzialność za upewnij się, że konwencji nazewnictwa służący do generowania obiektów bazy danych jest zgodne z konwencjami używane do wykonywania zapytań i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="370f1-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="370f1-109">Poniższy przykład przedstawia sposób generowania bazy danych na podstawie istniejącego modelu.</span><span class="sxs-lookup"><span data-stu-id="370f1-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="370f1-110">On również dodaje nowy obiekt jednostki do kontekstu obiektów i jest zapisywany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="370f1-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="370f1-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="370f1-111">Procedures</span></span>  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="370f1-112">Aby określić bazę danych na podstawie istniejącego modelu</span><span class="sxs-lookup"><span data-stu-id="370f1-112">To define a database based on the existing model</span></span>  
  
1.  <span data-ttu-id="370f1-113">Tworzenie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="370f1-113">Create a console application.</span></span>  
  
2.  <span data-ttu-id="370f1-114">Dodawanie istniejącego modelu do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="370f1-114">Add an existing model to your application.</span></span>  
  
    1.  <span data-ttu-id="370f1-115">Dodaj pusty model o nazwie `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="370f1-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="370f1-116">Aby utworzyć pusty model, zobacz [porady: Tworzenie nowego edmx pliku](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2) tematu.</span><span class="sxs-lookup"><span data-stu-id="370f1-116">To create an empty model, see the [How to: Create a New .edmx File](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2) topic.</span></span>  
  
     <span data-ttu-id="370f1-117">Plik SchoolModel.edmx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="370f1-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1.  <span data-ttu-id="370f1-118">Kopiowanie pojęciach, magazynu i mapowanie zawartości dla modelu służbowe [modelu służbowe](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) tematu.</span><span class="sxs-lookup"><span data-stu-id="370f1-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) topic.</span></span>  
  
    2.  <span data-ttu-id="370f1-119">Otwórz plik SchoolModel.edmx i Wklej zawartość w `edmx:Runtime` tagów.</span><span class="sxs-lookup"><span data-stu-id="370f1-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3.  <span data-ttu-id="370f1-120">Dodaj następujący kod do funkcji main.</span><span class="sxs-lookup"><span data-stu-id="370f1-120">Add the following code to your main function.</span></span> <span data-ttu-id="370f1-121">Kod inicjuje parametry połączenia z serwerem bazy danych, widoki skryptu DDL utworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="370f1-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
