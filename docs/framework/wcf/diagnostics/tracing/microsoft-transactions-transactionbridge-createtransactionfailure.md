---
title: Microsoft.Transactions.TransactionBridge.CreateTransactionFailure
ms.date: 03/30/2017
ms.assetid: c3468e23-49a9-4a84-972d-a79a658851b3
ms.openlocfilehash: f35cc0c12f2ac42c2b26536186c21feef193ae5d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594403"
---
# <a name="microsofttransactionstransactionbridgecreatetransactionfailure"></a><span data-ttu-id="359c8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="359c8-102">Microsoft.Transactions.TransactionBridge.CreateTransactionFailure</span></span>
<span data-ttu-id="359c8-103">Nie można utworzyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="359c8-103">A transaction could not be created.</span></span>  
  
## <a name="description"></a><span data-ttu-id="359c8-104">Opis</span><span class="sxs-lookup"><span data-stu-id="359c8-104">Description</span></span>  
 <span data-ttu-id="359c8-105">Ten ślad jest generowany, gdy usługa MSDTC nie może utworzyć transakcji.</span><span class="sxs-lookup"><span data-stu-id="359c8-105">This trace is generated when MSDTC is unable to create a transaction.</span></span> <span data-ttu-id="359c8-106">Może to być spowodowane małą ilością zasobów, niewystarczającą ilością miejsca w dzienniku lub innymi błędami.</span><span class="sxs-lookup"><span data-stu-id="359c8-106">This can be due to low resources, insufficient log space, or other errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="359c8-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="359c8-107">Troubleshooting</span></span>  
 <span data-ttu-id="359c8-108">Sprawdź ciąg stanu w komunikacie śledzenia, aby określić, czy istnieje jakikolwiek element możliwy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="359c8-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="359c8-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="359c8-109">See also</span></span>

- [<span data-ttu-id="359c8-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="359c8-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="359c8-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="359c8-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="359c8-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="359c8-112">Administration and Diagnostics</span></span>](../index.md)
