---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 4f51777ae690178b83d353f72e63a6f2958b1592
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674586"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="81fa2-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="81fa2-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="81fa2-103">Usługa protokołu WS-AT nie można zarejestrować transakcji za pomocą dostępnego kontekstu koordynacji.</span><span class="sxs-lookup"><span data-stu-id="81fa2-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="81fa2-104">Opis</span><span class="sxs-lookup"><span data-stu-id="81fa2-104">Description</span></span>  
 <span data-ttu-id="81fa2-105">Śledzone po nie można zarejestrować transakcji protokołu 2pc danej usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="81fa2-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="81fa2-106">Można to zrobić, ponieważ transakcja nie istnieje, rejestrowanie nie jest już dozwolona lub zbyt wiele rejestracji znajdują się już.</span><span class="sxs-lookup"><span data-stu-id="81fa2-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="81fa2-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="81fa2-107">Troubleshooting</span></span>  
 <span data-ttu-id="81fa2-108">Sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="81fa2-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81fa2-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81fa2-109">See also</span></span>
- [<span data-ttu-id="81fa2-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="81fa2-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="81fa2-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="81fa2-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="81fa2-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="81fa2-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
