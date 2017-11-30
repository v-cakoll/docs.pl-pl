---
title: "Obsługa transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cceb26e-8d36-4365-8967-58e2e89e0187
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 7c1d438a83f090795a158ade1dfdbb7d2b2df863
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="transaction-support"></a><span data-ttu-id="9dbfa-102">Obsługa transakcji</span><span class="sxs-lookup"><span data-stu-id="9dbfa-102">Transaction Support</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9dbfa-103">obsługuje trzy modele transakcji distinct.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-103"> supports three distinct transaction models.</span></span> <span data-ttu-id="9dbfa-104">Poniższa lista zawiera te modele kolejności wykonać kontroli.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-104">The following lists these models in the order of checks performed.</span></span>  
  
## <a name="explicit-local-transaction"></a><span data-ttu-id="9dbfa-105">Jawne transakcji lokalnej</span><span class="sxs-lookup"><span data-stu-id="9dbfa-105">Explicit Local Transaction</span></span>  
 <span data-ttu-id="9dbfa-106">Gdy <xref:System.Data.Linq.DataContext.SubmitChanges%2A> jest wywoływana, jeśli <xref:System.Data.Linq.DataContext.Transaction%2A> ma ustawioną wartość właściwości (`IDbTransaction`) transakcji, <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wywołanie jest wykonywany w kontekście tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-106">When <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called, if the <xref:System.Data.Linq.DataContext.Transaction%2A> property is set to a (`IDbTransaction`) transaction, the <xref:System.Data.Linq.DataContext.SubmitChanges%2A> call is executed in the context of the same transaction.</span></span>  
  
 <span data-ttu-id="9dbfa-107">Odpowiada Twojej zatwierdzania lub wycofywania transakcji po pomyślnym wykonaniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-107">It is your responsibility to commit or rollback the transaction after successful execution of the transaction.</span></span> <span data-ttu-id="9dbfa-108">Połączenie odpowiadające transakcji musi być zgodna połączenia używany do tworzenia <xref:System.Data.Linq.DataContext>.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-108">The connection corresponding to the transaction must match the connection used for constructing the <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="9dbfa-109">Jeśli jest używany przez inne połączenie, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-109">An exception is thrown if a different connection is used.</span></span>  
  
## <a name="explicit-distributable-transaction"></a><span data-ttu-id="9dbfa-110">Jawne dystrybucyjnego transakcji</span><span class="sxs-lookup"><span data-stu-id="9dbfa-110">Explicit Distributable Transaction</span></span>  
 <span data-ttu-id="9dbfa-111">Możesz wywołać [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsów API (w tym między innymi <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) w zakresie aktywnego <xref:System.Transactions.Transaction>.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-111">You can call [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] APIs (including but not limited to <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) in the scope of an active <xref:System.Transactions.Transaction>.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9dbfa-112">wykrywa, że wywołanie znajduje się w zakresie transakcji i nie tworzy nową transakcję.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-112"> detects that the call is in the scope of a transaction and does not create a new transaction.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="9dbfa-113">unika się również w takim przypadku zamknięcie połączenia.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-113"> also avoids closing the connection in this case.</span></span> <span data-ttu-id="9dbfa-114">Można wykonywać zapytania i <xref:System.Data.Linq.DataContext.SubmitChanges%2A> wykonaniami w ramach takich transakcji.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-114">You can perform query and <xref:System.Data.Linq.DataContext.SubmitChanges%2A> executions in the context of such a transaction.</span></span>  
  
## <a name="implicit-transaction"></a><span data-ttu-id="9dbfa-115">Niejawne transakcji</span><span class="sxs-lookup"><span data-stu-id="9dbfa-115">Implicit Transaction</span></span>  
 <span data-ttu-id="9dbfa-116">Podczas wywoływania <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sprawdza, czy połączenie jest w zakresie <xref:System.Transactions.Transaction> lub, jeśli `Transaction` właściwości (`IDbTransaction`) ma ustawioną wartość użytkownik rozpoczął transakcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-116">When you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] checks to see whether the call is in the scope of a <xref:System.Transactions.Transaction> or if the `Transaction` property (`IDbTransaction`) is set to a user-started local transaction.</span></span> <span data-ttu-id="9dbfa-117">W przypadku odnalezienia ani transakcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] uruchamia transakcji lokalnej (`IDbTransaction`) i używa go do wykonania polecenia SQL wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-117">If it finds neither transaction, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] starts a local transaction (`IDbTransaction`) and uses it to execute the generated SQL commands.</span></span> <span data-ttu-id="9dbfa-118">Gdy wszystkie polecenia SQL została pomyślnie ukończona, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zatwierdza transakcji lokalnej i zwraca.</span><span class="sxs-lookup"><span data-stu-id="9dbfa-118">When all SQL commands have been successfully completed, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] commits the local transaction and returns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbfa-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9dbfa-119">See Also</span></span>  
 [<span data-ttu-id="9dbfa-120">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="9dbfa-120">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [<span data-ttu-id="9dbfa-121">Porady: nawiasów przesyłania danych za pomocą transakcji</span><span class="sxs-lookup"><span data-stu-id="9dbfa-121">How to: Bracket Data Submissions by Using Transactions</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-bracket-data-submissions-by-using-transactions.md)
