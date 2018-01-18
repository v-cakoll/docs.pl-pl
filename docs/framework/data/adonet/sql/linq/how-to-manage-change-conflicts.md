---
title: "Porady: Zarządzanie konfliktów zmian"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd292c51-a3d1-4c6f-8d8e-04323c36054e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: caacb4c3b877ce6bf7ba11001f602a76ad7f9734
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-manage-change-conflicts"></a><span data-ttu-id="ec35c-102">Porady: Zarządzanie konfliktów zmian</span><span class="sxs-lookup"><span data-stu-id="ec35c-102">How to: Manage Change Conflicts</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ec35c-103">zawiera kolekcję interfejsów API, aby ułatwić odnajdywanie, oceny i rozwiązywanie konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ec35c-103"> provides a collection of APIs to help you discover, evaluate, and resolve concurrency conflicts.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec35c-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ec35c-104">In This Section</span></span>  
 [<span data-ttu-id="ec35c-105">Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań</span><span class="sxs-lookup"><span data-stu-id="ec35c-105">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 <span data-ttu-id="ec35c-106">Opisuje sposób wykrywania i rozwiązywania konfliktów współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ec35c-106">Describes how to detect and resolve concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="ec35c-107">Instrukcje: Określanie, kiedy są zgłaszane wyjątki współbieżności</span><span class="sxs-lookup"><span data-stu-id="ec35c-107">How to: Specify When Concurrency Exceptions are Thrown</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-when-concurrency-exceptions-are-thrown.md)  
 <span data-ttu-id="ec35c-108">Opisuje sposób określić, kiedy użytkownik powinien mieć świadomość konfliktom współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ec35c-108">Describes how to specify when you should be informed of concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="ec35c-109">Instrukcje: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktów współbieżności</span><span class="sxs-lookup"><span data-stu-id="ec35c-109">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)  
 <span data-ttu-id="ec35c-110">Opisuje sposób atrybutu elementy członkowskie, aby określić, czy są one sprawdzane pod kątem konfliktom współbieżności.</span><span class="sxs-lookup"><span data-stu-id="ec35c-110">Describes how to attribute members to specify whether they are checked for concurrency conflicts.</span></span>  
  
 [<span data-ttu-id="ec35c-111">Instrukcje: Pobieranie informacji o konflikcie jednostki</span><span class="sxs-lookup"><span data-stu-id="ec35c-111">How to: Retrieve Entity Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-entity-conflict-information.md)  
 <span data-ttu-id="ec35c-112">Opisuje sposób zebrać informacje o konfliktach jednostki.</span><span class="sxs-lookup"><span data-stu-id="ec35c-112">Describes how to gather information about entity conflicts.</span></span>  
  
 [<span data-ttu-id="ec35c-113">Instrukcje: Pobieranie informacji o konflikcie elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="ec35c-113">How to: Retrieve Member Conflict Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-retrieve-member-conflict-information.md)  
 <span data-ttu-id="ec35c-114">Opisuje sposób zebrać informacje dotyczące wystąpił konflikt elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="ec35c-114">Describes how to gather information about member conflicts.</span></span>  
  
 [<span data-ttu-id="ec35c-115">Instrukcje: Rozwiązywanie konfliktów, zachowując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="ec35c-115">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 <span data-ttu-id="ec35c-116">Opisuje sposób zastępowania bieżących wartości z wartościami bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ec35c-116">Describes how to overwrite current values with database values.</span></span>  
  
 [<span data-ttu-id="ec35c-117">Instrukcje: Rozwiązywanie konfliktów, zastępując wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="ec35c-117">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 <span data-ttu-id="ec35c-118">Opisuje sposób zachować bieżące wartości przez zastąpienie wartości bazy danych.</span><span class="sxs-lookup"><span data-stu-id="ec35c-118">Describes how to keep current values by overwriting database values.</span></span>  
  
 [<span data-ttu-id="ec35c-119">Instrukcje: Rozwiązywanie konfliktów, scalając wartości bazy danych</span><span class="sxs-lookup"><span data-stu-id="ec35c-119">How to: Resolve Conflicts by Merging with Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-merging-with-database-values.md)  
 <span data-ttu-id="ec35c-120">Opisuje sposób rozwiązania konfliktu przez scalenie bazy danych i bieżące wartości.</span><span class="sxs-lookup"><span data-stu-id="ec35c-120">Describes how to resolve a conflict by merging database and current values.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec35c-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ec35c-121">Related Sections</span></span>  
 [<span data-ttu-id="ec35c-122">Optymistyczna współbieżność: Omówienie</span><span class="sxs-lookup"><span data-stu-id="ec35c-122">Optimistic Concurrency: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)  
 <span data-ttu-id="ec35c-123">Opisano terminy, które dotyczą optymistycznej współbieżności w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ec35c-123">Explains the terms that apply to optimistic concurrency in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>
