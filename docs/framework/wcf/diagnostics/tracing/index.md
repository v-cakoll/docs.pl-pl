---
title: Śledzenie
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 2379b290494e72b65db5ddc6a7bc5df376d4373f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093400"
---
# <a name="tracing"></a><span data-ttu-id="f1a74-102">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="f1a74-102">Tracing</span></span>
<span data-ttu-id="f1a74-103">Windows Communication Foundation (WCF) udostępnia instrumentacji aplikacji i danych diagnostycznych dla błędów monitorowania i analizy.</span><span class="sxs-lookup"><span data-stu-id="f1a74-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="f1a74-104">Aby dowiedzieć się, jak aplikacja zachowuje się lub dlaczego błędów, można użyć śledzenia zamiast debugera.</span><span class="sxs-lookup"><span data-stu-id="f1a74-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="f1a74-105">Między składnikami w celu udostępnienia środowiska end-to-end, można skorelować błędów i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f1a74-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="f1a74-106">Usługi WCF wyświetla następujące dane śledzenia diagnostycznego:</span><span class="sxs-lookup"><span data-stu-id="f1a74-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="f1a74-107">Śledzenie procesu punktów kontrolnych, dotyczące wszystkich składników aplikacji, takich jak wywołania operacji kodu: wyjątki, ostrzeżenia i inne zdarzenia przetwarzania."</span><span class="sxs-lookup"><span data-stu-id="f1a74-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="f1a74-108">Zdarzenia błędu Windows działa funkcja śledzenia.</span><span class="sxs-lookup"><span data-stu-id="f1a74-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1a74-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f1a74-109">In This Section</span></span>  
 [<span data-ttu-id="f1a74-110">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="f1a74-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="f1a74-111">W tym temacie opisano, jak skonfigurować śledzenie, na różnych poziomach w zależności od określonych wymagań.</span><span class="sxs-lookup"><span data-stu-id="f1a74-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="f1a74-112">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="f1a74-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="f1a74-113">W tej sekcji opisano, jak można użyć śledzenie działań i Propagacja dla korelacji end-to-end, ułatwiające debugowanie.</span><span class="sxs-lookup"><span data-stu-id="f1a74-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="f1a74-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="f1a74-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="f1a74-115">W tej sekcji opisano, jak można użyć z funkcji śledzenia podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f1a74-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="f1a74-116">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="f1a74-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="f1a74-117">W tym temacie opisano, jak możesz chronić poufne informacje przed przypadkowym, a także przydatne porady, korzystając z hostem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f1a74-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="f1a74-118">Informacje o śladach</span><span class="sxs-lookup"><span data-stu-id="f1a74-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="f1a74-119">Ten temat zawiera listę wszystkich danych śledzenia generowane przez architekturę WCF.</span><span class="sxs-lookup"><span data-stu-id="f1a74-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a74-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1a74-120">See also</span></span>

- [<span data-ttu-id="f1a74-121">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f1a74-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
