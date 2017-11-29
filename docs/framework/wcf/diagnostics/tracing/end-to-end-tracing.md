---
title: "Kompleksowe śledzenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b4cdbc12f57c733d8e8ba3753ce5a2f29ab28ffd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="62e41-102">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="62e41-102">End-to-End Tracing</span></span>
<span data-ttu-id="62e41-103">Kompleksowe śledzenie (e2e) umożliwia deweloperom wykonaj wykonywanie kodu w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastrukturę do badania, dlaczego ścieżka kodu nie powiodło się lub w celu zapewnienia szczegółowego śledzenia wydajności planowania i analiza wydajności.</span><span class="sxs-lookup"><span data-stu-id="62e41-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="62e41-104">udostępnia trzy mechanizmy korelacji, aby pomóc w zdiagnozowaniu przyczyny błędu: działań, przesyłania i propagacji.</span><span class="sxs-lookup"><span data-stu-id="62e41-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="62e41-105">Zobacz [scenariusze śledzenia End-To-End](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) listę scenariuszy śledzenia end-to-end oraz ich odpowiednich działania i śledzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="62e41-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="62e41-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="62e41-106">In This Section</span></span>  
 <span data-ttu-id="62e41-107">[Działanie](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): opisuje działania śledzenia w [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] śledzenie modelu.</span><span class="sxs-lookup"><span data-stu-id="62e41-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="62e41-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): Opisuje transferu [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] śledzenie modelu i przy użyciu transferu do skorelowania działań w ramach punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="62e41-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="62e41-109">[Propagacja](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): opisuje działania propagacją [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] śledzenie modelu i przy użyciu propagacji służące do skorelowania działań w obrębie punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="62e41-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="62e41-110">Podsumowanie typu śledzenia</span><span class="sxs-lookup"><span data-stu-id="62e41-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="62e41-111">Zawiera podsumowanie działań wszystkie typy śledzenia</span><span class="sxs-lookup"><span data-stu-id="62e41-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e41-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e41-112">See Also</span></span>  
 [<span data-ttu-id="62e41-113">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="62e41-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="62e41-114">Przy użyciu przeglądarki śledzenia usługi do wyświetlania skorelowanych danych śledzenia i rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="62e41-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="62e41-115">Scenariusze śledzenia end-To-End</span><span class="sxs-lookup"><span data-stu-id="62e41-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="62e41-116">Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="62e41-116">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
