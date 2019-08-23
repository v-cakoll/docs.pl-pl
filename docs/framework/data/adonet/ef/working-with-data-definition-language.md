---
title: Praca z językiem definicji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: c2812e261278af7763bc6b2e1a493b97cb35e3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911636"
---
# <a name="working-with-data-definition-language"></a><span data-ttu-id="0fa92-102">Praca z językiem definicji danych</span><span class="sxs-lookup"><span data-stu-id="0fa92-102">Working with Data Definition Language</span></span>
<span data-ttu-id="0fa92-103">Począwszy od .NET Framework w wersji 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje język definicji danych (DDL).</span><span class="sxs-lookup"><span data-stu-id="0fa92-103">Starting with the .NET Framework version 4, the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] supports data definition language (DDL).</span></span> <span data-ttu-id="0fa92-104">Pozwala to na tworzenie lub usuwanie wystąpienia bazy danych na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).</span><span class="sxs-lookup"><span data-stu-id="0fa92-104">This allows you to create or delete a database instance based on the connection string and the metadata of the storage (SSDL) model.</span></span>  
  
 <span data-ttu-id="0fa92-105">Poniższe metody dotyczące <xref:System.Data.Objects.ObjectContext> używania parametrów połączenia i zawartości SSDL do wykonania następujących czynności: Utwórz lub Usuń bazę danych, sprawdź, czy baza danych istnieje, i Wyświetl wygenerowany skrypt DDL:</span><span class="sxs-lookup"><span data-stu-id="0fa92-105">The following methods on the <xref:System.Data.Objects.ObjectContext> use the connection string and the SSDL content to accomplish the following: create or delete the database, check whether the database exists, and view the generated DDL script:</span></span>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> <span data-ttu-id="0fa92-106">Wykonywanie poleceń języka DDL przyjmuje odpowiednie uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="0fa92-106">Executing the DDL commands assumes sufficient permissions.</span></span>  
  
 <span data-ttu-id="0fa92-107">Wymienione wcześniej metody delegowania większość pracy do podstawowego dostawcy danych ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0fa92-107">The methods previously listed delegate most of the work to the underlying ADO.NET data provider.</span></span> <span data-ttu-id="0fa92-108">Jest on odpowiedzialny za zapewnienie, że Konwencja nazewnictwa używana do generowania obiektów bazy danych jest spójna z konwencjami używanymi do wykonywania zapytań i aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="0fa92-108">It is the provider’s responsibility to ensure that the naming convention used to generate database objects is consistent with conventions used for querying and updates.</span></span>  
  
 <span data-ttu-id="0fa92-109">Poniższy przykład pokazuje, jak wygenerować bazę danych na podstawie istniejącego modelu.</span><span class="sxs-lookup"><span data-stu-id="0fa92-109">The following example shows you how to generate the database based on the existing model.</span></span> <span data-ttu-id="0fa92-110">Dodaje również nowy obiekt Entity do kontekstu obiektu, a następnie zapisuje go w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0fa92-110">It also adds a new entity object to the object context and then saves it to the database.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0fa92-111">Procedury</span><span class="sxs-lookup"><span data-stu-id="0fa92-111">Procedures</span></span>  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a><span data-ttu-id="0fa92-112">Aby zdefiniować bazę danych opartą na istniejącym modelu</span><span class="sxs-lookup"><span data-stu-id="0fa92-112">To define a database based on the existing model</span></span>  
  
1. <span data-ttu-id="0fa92-113">Utwórz aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="0fa92-113">Create a console application.</span></span>  
  
2. <span data-ttu-id="0fa92-114">Dodaj istniejący model do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0fa92-114">Add an existing model to your application.</span></span>  
  
    1. <span data-ttu-id="0fa92-115">Dodaj pusty model o nazwie `SchoolModel`.</span><span class="sxs-lookup"><span data-stu-id="0fa92-115">Add an empty model named `SchoolModel`.</span></span> <span data-ttu-id="0fa92-116">Aby utworzyć pusty model, zobacz [How to: Utwórz nowy temat pliku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) . edmx.</span><span class="sxs-lookup"><span data-stu-id="0fa92-116">To create an empty model, see the [How to: Create a New .edmx File](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) topic.</span></span>  
  
     <span data-ttu-id="0fa92-117">Plik SchoolModel. edmx zostanie dodany do projektu.</span><span class="sxs-lookup"><span data-stu-id="0fa92-117">The SchoolModel.edmx file is added to your project.</span></span>  
  
    1. <span data-ttu-id="0fa92-118">Skopiuj zawartość koncepcyjną, magazynową i mapowanie dla modelu szkoły z tematu [model szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .</span><span class="sxs-lookup"><span data-stu-id="0fa92-118">Copy the conceptual, storage, and mapping content for the School model from the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) topic.</span></span>  
  
    2. <span data-ttu-id="0fa92-119">Otwórz plik SchoolModel. edmx i wklej zawartość w `edmx:Runtime` tagach.</span><span class="sxs-lookup"><span data-stu-id="0fa92-119">Open the SchoolModel.edmx file and paste the content within the `edmx:Runtime` tags.</span></span>  
  
3. <span data-ttu-id="0fa92-120">Dodaj następujący kod do funkcji main.</span><span class="sxs-lookup"><span data-stu-id="0fa92-120">Add the following code to your main function.</span></span> <span data-ttu-id="0fa92-121">Kod inicjuje parametry połączenia z serwerem bazy danych, przegląda Skrypt DDL, tworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="0fa92-121">The code initializes the connection string to your database server, views the DDL script, creates the database, adds a new entity to the context, and saves the changes to the database.</span></span>  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
