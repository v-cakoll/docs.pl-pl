---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 93c96d94aaeddeb7e7b04ea80645b8de95b0343e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666797"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="0eb87-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="0eb87-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="0eb87-103">Usługa protokołu WS-AT nie można zarejestrować transakcji za pomocą dostępnego kontekstu koordynacji.</span><span class="sxs-lookup"><span data-stu-id="0eb87-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0eb87-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0eb87-104">Description</span></span>  
 <span data-ttu-id="0eb87-105">Śledzone po nie można zarejestrować transakcji protokołu 2pc danej usługi MSDTC.</span><span class="sxs-lookup"><span data-stu-id="0eb87-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="0eb87-106">Można to zrobić, ponieważ transakcja nie istnieje, rejestrowanie nie jest już dozwolona lub zbyt wiele rejestracji znajdują się już.</span><span class="sxs-lookup"><span data-stu-id="0eb87-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0eb87-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0eb87-107">Troubleshooting</span></span>  
 <span data-ttu-id="0eb87-108">Sprawdź, czy ciąg stanu w ramach komunikat śledzenia do ustalenia, czy istnieje dowolny element informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="0eb87-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb87-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0eb87-109">See also</span></span>

- [<span data-ttu-id="0eb87-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0eb87-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0eb87-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0eb87-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0eb87-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0eb87-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
