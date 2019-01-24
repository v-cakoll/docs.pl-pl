---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed
ms.date: 03/30/2017
ms.assetid: 96474056-0418-41e4-8c75-bbc0a853eaba
ms.openlocfilehash: 5c8592ac34375445964b3dbcbbd4800c47e53850
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515053"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfailed"></a><span data-ttu-id="b2206-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span><span class="sxs-lookup"><span data-stu-id="b2206-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFailed</span></span>
<span data-ttu-id="b2206-103">Usługa protokołu WS-AT nie może wysłać komunikatu rejestracji do koordynatora</span><span class="sxs-lookup"><span data-stu-id="b2206-103">The WS-AT protocol service failed to send a Register message to its coordinator</span></span>  
  
## <a name="description"></a><span data-ttu-id="b2206-104">Opis</span><span class="sxs-lookup"><span data-stu-id="b2206-104">Description</span></span>  
 <span data-ttu-id="b2206-105">Śledzone, jeśli lokalny Menedżer transakcji nie można zarejestrować w usłudze jego przełożonego Menedżer transakcji z powodu braku możliwości, aby wysłać wiadomość.</span><span class="sxs-lookup"><span data-stu-id="b2206-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to the inability to send a message.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b2206-106">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="b2206-106">Troubleshooting</span></span>  
 <span data-ttu-id="b2206-107">Sprawdź komunikat śledzenia, dla wyjątku, co powoduje błąd wysyłania wiadomości</span><span class="sxs-lookup"><span data-stu-id="b2206-107">Inspect the trace message for the exception causing the message send failure</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2206-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2206-108">See also</span></span>
- [<span data-ttu-id="b2206-109">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="b2206-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="b2206-110">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="b2206-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b2206-111">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="b2206-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
