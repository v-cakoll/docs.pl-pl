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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: aa12b26723c3c97e45f75ae951a7496025fde5a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="b05e5-102">Dostosowywanie wstawiania, aktualizowania i usuwania operacji</span><span class="sxs-lookup"><span data-stu-id="b05e5-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="b05e5-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczne SQL do wdrożenia insert, odczytu, aktualizacji i usuwania operacji.</span><span class="sxs-lookup"><span data-stu-id="b05e5-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="b05e5-104">W praktyce jednak zwykle dostosować aplikację, w zależności od potrzeb biznesowych.</span><span class="sxs-lookup"><span data-stu-id="b05e5-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b05e5-105">Jeśli używasz [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], można użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Aby dostosować wstawiania, aktualizowania i usuwania działań.</span><span class="sxs-lookup"><span data-stu-id="b05e5-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="b05e5-106">Tematy w tej części opisano techniki który [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia dostosowywanie insert, odczytu, aktualizacji i operacji usuwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b05e5-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b05e5-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="b05e5-107">In This Section</span></span>  
 [<span data-ttu-id="b05e5-108">Dostosowywanie operacji: Omówienie</span><span class="sxs-lookup"><span data-stu-id="b05e5-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="b05e5-109">Zawiera opis różnych technik [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia dostosowywanie insert, odczytu, aktualizacji i operacji usuwania.</span><span class="sxs-lookup"><span data-stu-id="b05e5-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="b05e5-110">Operacje wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="b05e5-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="b05e5-111">W tym artykule opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślne procesów do manipulowania danymi bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b05e5-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="b05e5-112">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="b05e5-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="b05e5-113">Zawiera opis roli deweloperów w wymagania, które nie są wymuszane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b05e5-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="b05e5-114">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="b05e5-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="b05e5-115">Informacje dotyczące używania metod częściowych do przesłonięcia metody wygenerowana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="b05e5-115">Describes how to use partial methods to override autogenerated methods.</span></span>
