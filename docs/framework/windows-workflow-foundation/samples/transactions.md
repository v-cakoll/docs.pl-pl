---
title: Transactions2
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51212219-a39e-448e-bff3-10064ff5de64
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53389822f635151d15c2ae205c5a421a331c063b
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="transactions"></a><span data-ttu-id="51229-102">Transakcje</span><span class="sxs-lookup"><span data-stu-id="51229-102">Transactions</span></span>
<span data-ttu-id="51229-103">Ta sekcja zawiera przykłady ilustrujące transakcji przepływu pracy w systemie Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="51229-103">This section contains samples that demonstrate workflow transactions in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51229-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="51229-104">In This Section</span></span>  
 [<span data-ttu-id="51229-105">Podstawowy element TransactionScope</span><span class="sxs-lookup"><span data-stu-id="51229-105">Basic TransactionScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md)  
 <span data-ttu-id="51229-106">Składa się z czterech scenariusze, które przedstawiają sposób zagnieździć <xref:System.Activities.Statements.TransactionScope> wystąpień.</span><span class="sxs-lookup"><span data-stu-id="51229-106">Consists of four scenarios that show how to nest <xref:System.Activities.Statements.TransactionScope> instances.</span></span>  
  
 [<span data-ttu-id="51229-107">Używanie elementu TransactedReceiveScope</span><span class="sxs-lookup"><span data-stu-id="51229-107">Use of TransactedReceiveScope</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/use-of-transactedreceivescope.md)  
 <span data-ttu-id="51229-108">Przedstawia sposób uruchomienia przepływu transakcji od klienta do serwera przy użyciu <xref:System.Activities.Statements.TransactionScope> można utworzyć nowej transakcji na komputerze klienckim i <xref:System.ServiceModel.Activities.TransactedReceiveScope> do odbierania wiadomości z przesłanej transakcji i zakres okres istnienia transakcji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="51229-108">Demonstrates how to flow a transaction from a client to a server using <xref:System.Activities.Statements.TransactionScope> to create a new transaction on the client and a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive a message with a flowed transaction and scope the lifetime of the transaction on the server.</span></span>  
  
 [<span data-ttu-id="51229-109">Zagnieżdżanie elementu TransactionScope w usłudze</span><span class="sxs-lookup"><span data-stu-id="51229-109">Nesting of TransactionScope within a service</span></span>](../../../../docs/framework/windows-workflow-foundation/samples/nesting-of-transactionscope-within-a-service.md)  
 <span data-ttu-id="51229-110">Składa się z dwóch scenariuszy, które przedstawiają sposób obsługi <xref:System.Activities.Statements.TransactionScope> wystąpienia działania w ramach usługi.</span><span class="sxs-lookup"><span data-stu-id="51229-110">Consists of two scenarios that show how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span>
