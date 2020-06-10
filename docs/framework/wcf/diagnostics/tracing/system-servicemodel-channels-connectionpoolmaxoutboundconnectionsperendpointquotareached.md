---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 742e80a3115e8f8caa728e0d8c460ee8b964ddc9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84588720"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="0a9ec-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="0a9ec-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="0a9ec-103">Usługa protokołu WS-AT nie może zarejestrować się w transakcji przy użyciu podanego kontekstu koordynacji.</span><span class="sxs-lookup"><span data-stu-id="0a9ec-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0a9ec-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0a9ec-104">Description</span></span>  
 <span data-ttu-id="0a9ec-105">Śledzone, gdy usługa MSDTC nie może zarejestrować się w transakcji dla danego protokołu 2PC.</span><span class="sxs-lookup"><span data-stu-id="0a9ec-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="0a9ec-106">Może się tak zdarzyć, ponieważ transakcja już nie istnieje, rejestracja nie jest już dozwolona lub zbyt wiele rejestracji już istnieje.</span><span class="sxs-lookup"><span data-stu-id="0a9ec-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0a9ec-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0a9ec-107">Troubleshooting</span></span>  
 <span data-ttu-id="0a9ec-108">Sprawdź ciąg stanu w komunikacie śledzenia, aby określić, czy istnieje jakikolwiek element możliwy do wykonania.</span><span class="sxs-lookup"><span data-stu-id="0a9ec-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9ec-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a9ec-109">See also</span></span>

- [<span data-ttu-id="0a9ec-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0a9ec-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="0a9ec-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0a9ec-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0a9ec-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0a9ec-112">Administration and Diagnostics</span></span>](../index.md)
