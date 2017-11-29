---
title: System.ServiceModel.TxCompletionStatusCompletedForError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ade4722-a6d5-471c-b960-1cfea4ea2aa9
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4bce99f11ba5a18e80c24fc51e65b66de97f9e7d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="14c95-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="14c95-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="14c95-103">Transakcja określona dla określonej operacji została wykonana wskutek wystąpienia nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="14c95-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="14c95-104">Opis</span><span class="sxs-lookup"><span data-stu-id="14c95-104">Description</span></span>  
 <span data-ttu-id="14c95-105">Śledzone, gdy wystąpi błąd podczas próby wykonania bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="14c95-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="14c95-106">Dzieje się to przed odpowiedzi lub błędów są wysyłane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="14c95-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="14c95-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="14c95-107">Troubleshooting</span></span>  
 <span data-ttu-id="14c95-108">Sprawdź, czy w komunikacie śledzonych komunikat o wyjątku oraz dowolne elementy przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="14c95-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14c95-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14c95-109">See Also</span></span>  
 [<span data-ttu-id="14c95-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="14c95-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="14c95-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="14c95-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="14c95-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="14c95-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
