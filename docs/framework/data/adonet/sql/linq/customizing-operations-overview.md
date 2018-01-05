---
title: "Dostosowywanie operacji: omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3546296-1443-4b88-aa6e-d41011041ba7
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9776daa28b0a7ffcd3b721f004f5b9a44dd09f48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="customizing-operations-overview"></a><span data-ttu-id="4d0c0-102">Dostosowywanie operacji: omówienie</span><span class="sxs-lookup"><span data-stu-id="4d0c0-102">Customizing Operations: Overview</span></span>
<span data-ttu-id="4d0c0-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczne SQL insert, update i operacji delete na podstawie mapowania.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL for insert, update, and delete operations based on mapping.</span></span> <span data-ttu-id="4d0c0-104">Jednak w praktyce zwykle chcesz dodać własne logiki biznesowej w celu zapewnienia bezpieczeństwa, weryfikacji i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-104">However, in practice you typically want to add your own business logic to provide for security, validation, and so forth.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="4d0c0-105">następujące techniki te operacje dostosowywania.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-105"> techniques for customizing these operations include the following.</span></span>  
  
## <a name="loading-options"></a><span data-ttu-id="4d0c0-106">Trwa ładowanie opcji</span><span class="sxs-lookup"><span data-stu-id="4d0c0-106">Loading Options</span></span>  
 <span data-ttu-id="4d0c0-107">Zapytania można kontrolować, ile danych związanych z urządzenie docelowe głównej są pobierane, gdy połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-107">In your queries, you can control how much data related to your main target is retrieved when you connect to the database.</span></span> <span data-ttu-id="4d0c0-108">Ta funkcja jest zaimplementowana w znacznym stopniu przy użyciu <xref:System.Data.Linq.DataLoadOptions>.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-108">This functionality is implemented largely by using <xref:System.Data.Linq.DataLoadOptions>.</span></span> <span data-ttu-id="4d0c0-109">Aby uzyskać więcej informacji, zobacz [odroczone i ładowania bezpośredniego](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span><span class="sxs-lookup"><span data-stu-id="4d0c0-109">For more information, see [Deferred versus Immediate Loading](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md).</span></span>  
  
## <a name="partial-methods"></a><span data-ttu-id="4d0c0-110">Metody częściowe</span><span class="sxs-lookup"><span data-stu-id="4d0c0-110">Partial Methods</span></span>  
 <span data-ttu-id="4d0c0-111">W jego domyślne mapowanie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] udostępnia metody częściowe ułatwiająca implementację logiki biznesowej.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-111">In its default mapping, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides partial methods to help you implement your business logic.</span></span> <span data-ttu-id="4d0c0-112">Aby uzyskać więcej informacji, zobacz [Dodawanie firm logiki przez przy użyciu metody częściowe](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4d0c0-112">For more information, see [Adding Business Logic By Using Partial Methods](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md).</span></span>  
  
## <a name="stored-procedures-and-user-defined-functions"></a><span data-ttu-id="4d0c0-113">Procedury składowane i funkcje zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="4d0c0-113">Stored Procedures and User-Defined Functions</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="4d0c0-114">obsługuje procedury składowane i funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-114"> supports the use of stored procedures and user-defined functions.</span></span> <span data-ttu-id="4d0c0-115">Procedury składowane są często używane do dostosowania operacji.</span><span class="sxs-lookup"><span data-stu-id="4d0c0-115">Stored procedures are frequently used to customize operations.</span></span> <span data-ttu-id="4d0c0-116">Aby uzyskać więcej informacji, zobacz [procedur składowanych](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4d0c0-116">For more information, see [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d0c0-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d0c0-117">See Also</span></span>  
 [<span data-ttu-id="4d0c0-118">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="4d0c0-118">Customizing Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)
