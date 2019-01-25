---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 947391e0594ffddba8235c519a076d330b73d4d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632637"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="dabf5-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="dabf5-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="dabf5-103">Nie można utworzyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="dabf5-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dabf5-104">Opis</span><span class="sxs-lookup"><span data-stu-id="dabf5-104">Description</span></span>  
 <span data-ttu-id="dabf5-105">Ślad jest generowany, gdy nie może utworzyć transakcji MSDTC.</span><span class="sxs-lookup"><span data-stu-id="dabf5-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="dabf5-106">Może to być spowodowane małą ilością zasobów, miejsca w dzienniku niewystarczające lub inne błędy.</span><span class="sxs-lookup"><span data-stu-id="dabf5-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="dabf5-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="dabf5-107">Troubleshooting</span></span>  
 <span data-ttu-id="dabf5-108">Sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="dabf5-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dabf5-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dabf5-109">See also</span></span>
- [<span data-ttu-id="dabf5-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="dabf5-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="dabf5-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="dabf5-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="dabf5-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="dabf5-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
