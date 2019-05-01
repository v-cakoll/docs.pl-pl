---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.date: 03/30/2017
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
ms.openlocfilehash: 591e1a1dcb6746d79ff5eceba7e74e890f327354
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779499"
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="f7d43-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="f7d43-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="f7d43-103">Określonej transakcji dla określonej operacji zostało zakończone z powodu nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f7d43-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f7d43-104">Opis</span><span class="sxs-lookup"><span data-stu-id="f7d43-104">Description</span></span>  
 <span data-ttu-id="f7d43-105">Śledzone, gdy wystąpi błąd podczas próby wykonania bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="f7d43-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="f7d43-106">To ma miejsce przed odpowiedzi lub błędów jest wysyłany do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f7d43-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="f7d43-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="f7d43-107">Troubleshooting</span></span>  
 <span data-ttu-id="f7d43-108">Sprawdź, czy komunikat śledzenia dla komunikat o wyjątku oraz wszystkich elementów informacje z możliwością działania.</span><span class="sxs-lookup"><span data-stu-id="f7d43-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d43-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7d43-109">See also</span></span>

- [<span data-ttu-id="f7d43-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f7d43-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="f7d43-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f7d43-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f7d43-112">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="f7d43-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
