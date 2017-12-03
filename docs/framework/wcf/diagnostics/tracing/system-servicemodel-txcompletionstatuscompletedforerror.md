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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f6a05f838e37d5cd56a572dc73b032bec2d2abea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxcompletionstatuscompletedforerror"></a><span data-ttu-id="a567a-102">System.ServiceModel.TxCompletionStatusCompletedForError</span><span class="sxs-lookup"><span data-stu-id="a567a-102">System.ServiceModel.TxCompletionStatusCompletedForError</span></span>
<span data-ttu-id="a567a-103">Transakcja określona dla określonej operacji została wykonana wskutek wystąpienia nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a567a-103">The specified transaction for the specified operation was completed due to an unhandled execution exception.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a567a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="a567a-104">Description</span></span>  
 <span data-ttu-id="a567a-105">Śledzone, gdy wystąpi błąd podczas próby wykonania bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="a567a-105">Traced when an error occurs during an attempt to complete the current transaction.</span></span> <span data-ttu-id="a567a-106">Dzieje się to przed odpowiedzi lub błędów są wysyłane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a567a-106">This happens before a reply or fault is sent to the caller.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="a567a-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="a567a-107">Troubleshooting</span></span>  
 <span data-ttu-id="a567a-108">Sprawdź, czy w komunikacie śledzonych komunikat o wyjątku oraz dowolne elementy przydatnych wyników.</span><span class="sxs-lookup"><span data-stu-id="a567a-108">Inspect the traced message for the exception message and any actionable items.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a567a-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a567a-109">See Also</span></span>  
 [<span data-ttu-id="a567a-110">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="a567a-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="a567a-111">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="a567a-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="a567a-112">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="a567a-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
