---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: 968444947714315bae902d3d038129c5b8a04cf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997948"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="9ce0f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="9ce0f-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="9ce0f-103">Nie można utworzyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="9ce0f-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9ce0f-104">Opis</span><span class="sxs-lookup"><span data-stu-id="9ce0f-104">Description</span></span>  
 <span data-ttu-id="9ce0f-105">Ślad jest generowany, gdy nie może utworzyć transakcji MSDTC.</span><span class="sxs-lookup"><span data-stu-id="9ce0f-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="9ce0f-106">Może to być spowodowane małą ilością zasobów, miejsca w dzienniku niewystarczające lub inne błędy.</span><span class="sxs-lookup"><span data-stu-id="9ce0f-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9ce0f-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="9ce0f-107">Troubleshooting</span></span>  
 <span data-ttu-id="9ce0f-108">Sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="9ce0f-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce0f-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ce0f-109">See also</span></span>

- [<span data-ttu-id="9ce0f-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="9ce0f-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="9ce0f-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="9ce0f-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9ce0f-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="9ce0f-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
