---
title: Manipulowanie danymi w elemencie DataTable
ms.date: 03/30/2017
ms.assetid: 5cb86d48-a987-4af4-80e0-8cc2c8373d62
ms.openlocfilehash: a09edc6ce3098ab135d8c27ba0f6ad56cceed159
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521311"
---
# <a name="manipulating-data-in-a-datatable"></a><span data-ttu-id="b1539-102">Manipulowanie danymi w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-102">Manipulating Data in a DataTable</span></span>
<span data-ttu-id="b1539-103">Po utworzeniu <xref:System.Data.DataTable> w <xref:System.Data.DataSet>, można wykonać tego samego działania, które jak w przypadku tabeli w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="b1539-103">After creating a <xref:System.Data.DataTable> in a <xref:System.Data.DataSet>, you can perform the same activities that you would when using a table in a database.</span></span> <span data-ttu-id="b1539-104">Możesz dodawać, wyświetlać, edytowania i usuwania danych w tabeli; można monitorować, błędów i zdarzeń; i można wyszukiwać dane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1539-104">You can add, view, edit, and delete data in the table; you can monitor errors and events; and you can query the data in the table.</span></span> <span data-ttu-id="b1539-105">Podczas modyfikowania danych w **DataTable**, możesz również sprawdzić czy zmiany są dokładne i określenia, czy programowo zaakceptować lub odrzucić zmiany.</span><span class="sxs-lookup"><span data-stu-id="b1539-105">When modifying data in a **DataTable**, you can also verify whether the changes are accurate, and determine whether to programmatically accept or reject the changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1539-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b1539-106">In This Section</span></span>  
 [<span data-ttu-id="b1539-107">Dodawanie danych do elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-107">Adding Data to a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-data-to-a-datatable.md)  
 <span data-ttu-id="b1539-108">Wyjaśnia, jak utworzyć nowe wiersze i dodać je do tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1539-108">Explains how to create new rows and add them to a table.</span></span>  
  
 [<span data-ttu-id="b1539-109">Wyświetlanie danych w elemencie DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-109">Viewing Data in a DataTable</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/viewing-data-in-a-datatable.md)  
 <span data-ttu-id="b1539-110">Opisuje sposób uzyskiwać dostęp do danych w wierszu, łącznie z pierwotnym i bieżącym wersji danych.</span><span class="sxs-lookup"><span data-stu-id="b1539-110">Describes how to access the data in a row, including original and current versions of the data.</span></span>  
  
 [<span data-ttu-id="b1539-111">Metoda Load</span><span class="sxs-lookup"><span data-stu-id="b1539-111">The Load Method</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/the-load-method.md)  
 <span data-ttu-id="b1539-112">W tym artykule opisano korzystanie z **obciążenia** metodę, aby wypełnić **DataTable** wierszy.</span><span class="sxs-lookup"><span data-stu-id="b1539-112">Describes the use of the **Load** method to fill a **DataTable** with rows.</span></span>  
  
 [<span data-ttu-id="b1539-113">Edycje elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-113">DataTable Edits</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-edits.md)  
 <span data-ttu-id="b1539-114">Wyjaśnia, jak modyfikowanie danych w wierszu, w tym zawieszanie zmian w wierszu, aż proponowanych zmian zostaną zweryfikowane i zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="b1539-114">Explains how to modify the data in a row, including suspending the changes to a row until the proposed changes are verified and accepted.</span></span>  
  
 [<span data-ttu-id="b1539-115">Stany wiersza i wersje wiersza</span><span class="sxs-lookup"><span data-stu-id="b1539-115">Row States and Row Versions</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)  
 <span data-ttu-id="b1539-116">Zawiera informacje dotyczące różnych stanów wiersza.</span><span class="sxs-lookup"><span data-stu-id="b1539-116">Provides information about the different states of a row.</span></span>  
  
 [<span data-ttu-id="b1539-117">Usuwanie elementu DataRow</span><span class="sxs-lookup"><span data-stu-id="b1539-117">DataRow Deletion</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datarow-deletion.md)  
 <span data-ttu-id="b1539-118">Opisuje sposób usuwania wiersza z tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1539-118">Describes how to remove a row from a table.</span></span>  
  
 [<span data-ttu-id="b1539-119">Informacje o błędzie wiersza</span><span class="sxs-lookup"><span data-stu-id="b1539-119">Row Error Information</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)  
 <span data-ttu-id="b1539-120">Wyjaśnia, jak i Wstaw informacje o błędzie na wiersz, aby ułatwić rozwiązywanie problemów z danymi w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1539-120">Explains how to insert error information per row, to help resolve problems with the data within an application.</span></span>  
  
 [<span data-ttu-id="b1539-121">Metody AcceptChanges i RejectChanges</span><span class="sxs-lookup"><span data-stu-id="b1539-121">AcceptChanges and RejectChanges</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/acceptchanges-and-rejectchanges.md)  
 <span data-ttu-id="b1539-122">Wyjaśnia, jak o zaakceptowanie lub odrzucenie zmiany wprowadzone do wiersza.</span><span class="sxs-lookup"><span data-stu-id="b1539-122">Explains how to accept or reject the changes made to a row.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1539-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1539-123">See Also</span></span>  
 [<span data-ttu-id="b1539-124">Elementy DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-124">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [<span data-ttu-id="b1539-125">Obsługa zdarzeń elementu DataTable</span><span class="sxs-lookup"><span data-stu-id="b1539-125">Handling DataTable Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)  
 [<span data-ttu-id="b1539-126">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b1539-126">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
