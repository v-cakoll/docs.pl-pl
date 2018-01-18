---
title: "Porady: przesyłanie zmian w bazie danych"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bf1f9c7982cf9f328fe060266762658ab9693c2e
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-submit-changes-to-the-database"></a><span data-ttu-id="97ecf-102">Porady: przesyłanie zmian w bazie danych</span><span class="sxs-lookup"><span data-stu-id="97ecf-102">How to: Submit Changes to the Database</span></span>
<span data-ttu-id="97ecf-103">Niezależnie od tego, ile zmiany wprowadzane do obiektów zmiany są wprowadzane tylko replik w pamięci.</span><span class="sxs-lookup"><span data-stu-id="97ecf-103">Regardless of how many changes you make to your objects, changes are made only to in-memory replicas.</span></span> <span data-ttu-id="97ecf-104">Zostały wprowadzone żadne zmiany do danych rzeczywistych w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="97ecf-104">You have made no changes to the actual data in the database.</span></span> <span data-ttu-id="97ecf-105">Zmiany nie są przesyłane do serwera, dopóki nie zostanie jawnie wywołać <xref:System.Data.Linq.DataContext.SubmitChanges%2A> na <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="97ecf-105">Your changes are not transmitted to the server until you explicitly call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> on the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="97ecf-106">Po wprowadzeniu tego wywołania <xref:System.Data.Linq.DataContext> próbuje tłumaczenie zmiany na równoważne polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="97ecf-106">When you make this call, the <xref:System.Data.Linq.DataContext> tries to translate your changes into equivalent SQL commands.</span></span> <span data-ttu-id="97ecf-107">Można używać niestandardowej logiki do przesłonięcia te akcje, ale kolejność przesyłanie jest zorkiestrowana przez usługę <xref:System.Data.Linq.DataContext> znany jako *zmienić procesora*.</span><span class="sxs-lookup"><span data-stu-id="97ecf-107">You can use your own custom logic to override these actions, but the order of submission is orchestrated by a service of the <xref:System.Data.Linq.DataContext> known as the *change processor*.</span></span> <span data-ttu-id="97ecf-108">Kolejność zdarzeń wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="97ecf-108">The sequence of events is as follows:</span></span>  
  
1.  <span data-ttu-id="97ecf-109">Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza, czy zestaw znanymi obiektami, aby określić, czy nowe wystąpienia zostały dołączone do nich.</span><span class="sxs-lookup"><span data-stu-id="97ecf-109">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examines the set of known objects to determine whether new instances have been attached to them.</span></span> <span data-ttu-id="97ecf-110">Jeśli są dostępne, te nowe wystąpienia są dodawane do zestawu obiektów śledzonych.</span><span class="sxs-lookup"><span data-stu-id="97ecf-110">If they have, these new instances are added to the set of tracked objects.</span></span>  
  
2.  <span data-ttu-id="97ecf-111">Wszystkie obiekty, które mają oczekujące zmiany są uporządkowane w sekwencji obiektów na podstawie zależności między nimi.</span><span class="sxs-lookup"><span data-stu-id="97ecf-111">All objects that have pending changes are ordered into a sequence of objects based on the dependencies between them.</span></span> <span data-ttu-id="97ecf-112">Obiekty, której zmiany są zależne od innych obiektów są ustawione w kolejności po ich zależności.</span><span class="sxs-lookup"><span data-stu-id="97ecf-112">Objects whose changes depend on other objects are sequenced after their dependencies.</span></span>  
  
3.  <span data-ttu-id="97ecf-113">Bezpośrednio przed rzeczywiste zmiany są przesyłane, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uruchamia transakcja hermetyzują serię poszczególnych poleceń.</span><span class="sxs-lookup"><span data-stu-id="97ecf-113">Immediately before any actual changes are transmitted, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a transaction to encapsulate the series of individual commands.</span></span>  
  
4.  <span data-ttu-id="97ecf-114">Zmiany do obiektów są tłumaczone kolejno polecenia SQL i wysłane do serwera.</span><span class="sxs-lookup"><span data-stu-id="97ecf-114">The changes to the objects are translated one by one to SQL commands and sent to the server.</span></span>  
  
 <span data-ttu-id="97ecf-115">W tym momencie procesu przesyłania zatrzymać spowodować błędy wykryte przez bazę danych i zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="97ecf-115">At this point, any errors detected by the database cause the submission process to stop, and an exception is raised.</span></span> <span data-ttu-id="97ecf-116">Wszystkie zmiany do bazy danych są wycofane tak, jakby nie przesłanych kiedykolwiek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="97ecf-116">All changes to the database are rolled back as if no submissions ever occurred.</span></span> <span data-ttu-id="97ecf-117"><xref:System.Data.Linq.DataContext> Nadal ma pełne rejestrowanie wszystkich wprowadzonych zmian.</span><span class="sxs-lookup"><span data-stu-id="97ecf-117">The <xref:System.Data.Linq.DataContext> still has a full recording of all changes.</span></span> <span data-ttu-id="97ecf-118">W związku z tym można spróbować rozwiązać problem i wywołanie <xref:System.Data.Linq.DataContext.SubmitChanges%2A> ponownie, jak w następującym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="97ecf-118">You can therefore try to correct the problem and call <xref:System.Data.Linq.DataContext.SubmitChanges%2A> again, as in the code example that follows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97ecf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="97ecf-119">Example</span></span>  
 <span data-ttu-id="97ecf-120">Gdy transakcji wokół przesyłania zakończyło się powodzeniem, <xref:System.Data.Linq.DataContext> akceptuje zmian do obiektów przez ignorowanie informacji śledzenia zmian.</span><span class="sxs-lookup"><span data-stu-id="97ecf-120">When the transaction around the submission is completed successfully, the <xref:System.Data.Linq.DataContext> accepts the changes to the objects by ignoring the change-tracking information.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="97ecf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="97ecf-121">See Also</span></span>  
 [<span data-ttu-id="97ecf-122">Instrukcje: Wykrywanie i rozwiązywanie powodujących konflikt przesłań</span><span class="sxs-lookup"><span data-stu-id="97ecf-122">How to: Detect and Resolve Conflicting Submissions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [<span data-ttu-id="97ecf-123">Instrukcje: Zarządzanie konfliktami zmian</span><span class="sxs-lookup"><span data-stu-id="97ecf-123">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="97ecf-124">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="97ecf-124">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="97ecf-125">Tworzenie i przesyłanie zmian danych</span><span class="sxs-lookup"><span data-stu-id="97ecf-125">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
