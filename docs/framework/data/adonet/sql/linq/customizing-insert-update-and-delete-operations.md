---
title: Dostosowywanie wstawiania, aktualizowania i usuwania operacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e48ac307087d5b90567c720d0c215ac0d52ccb6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="6b177-102">Dostosowywanie wstawiania, aktualizowania i usuwania operacji</span><span class="sxs-lookup"><span data-stu-id="6b177-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="6b177-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczne SQL do wdrożenia insert, odczytu, aktualizacji i usuwania operacji.</span><span class="sxs-lookup"><span data-stu-id="6b177-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="6b177-104">W praktyce jednak zwykle dostosować aplikację, w zależności od potrzeb biznesowych.</span><span class="sxs-lookup"><span data-stu-id="6b177-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b177-105">Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Aby dostosować wstawiania, aktualizowania i usuwania działań.</span><span class="sxs-lookup"><span data-stu-id="6b177-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="6b177-106">Tematy w tej części opisano techniki który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia dostosowywanie insert, odczytu, aktualizacji i operacji usuwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b177-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6b177-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6b177-107">In This Section</span></span>  
 [<span data-ttu-id="6b177-108">Dostosowywanie operacji: omówienie</span><span class="sxs-lookup"><span data-stu-id="6b177-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="6b177-109">Zawiera opis różnych technik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia dostosowywanie insert, odczytu, aktualizacji i operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="6b177-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="6b177-110">Wstawiania, aktualizowania i usuwania działań</span><span class="sxs-lookup"><span data-stu-id="6b177-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="6b177-111">W tym artykule opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne procesów do manipulowania danymi bazy danych.</span><span class="sxs-lookup"><span data-stu-id="6b177-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="6b177-112">Obowiązki dewelopera w Zastępowanie domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="6b177-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="6b177-113">Zawiera opis roli deweloperów w wymagania, które nie są wymuszane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6b177-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="6b177-114">Dodawanie logiki biznesowej przy użyciu metody częściowe</span><span class="sxs-lookup"><span data-stu-id="6b177-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="6b177-115">Informacje dotyczące używania metod częściowych do przesłonięcia metody wygenerowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="6b177-115">Describes how to use partial methods to override autogenerated methods.</span></span>
