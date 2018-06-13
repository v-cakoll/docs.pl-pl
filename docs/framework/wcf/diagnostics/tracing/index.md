---
title: Śledzenie
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 6f427425b1bbf19ecd8b30fb1498634a7a3d5fa9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33809319"
---
# <a name="tracing"></a><span data-ttu-id="597a0-102">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="597a0-102">Tracing</span></span>
<span data-ttu-id="597a0-103">Windows Communication Foundation (WCF) zapewnia instrumentacji aplikacji i danych diagnostycznych błędów monitorowania i analizy.</span><span class="sxs-lookup"><span data-stu-id="597a0-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="597a0-104">Śledzenie można użyć zamiast debugera zrozumienie zachowania aplikacji lub przyczynę błędów.</span><span class="sxs-lookup"><span data-stu-id="597a0-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="597a0-105">Między składnikami, aby zapewnić środowisko end-to-end można również dostosować błędów i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="597a0-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="597a0-106">Usługi WCF generuje następujące dane śledzenia diagnostycznego:</span><span class="sxs-lookup"><span data-stu-id="597a0-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="597a0-107">Ślady punktów kontrolnych procesu dotyczące wszystkich składników aplikacji, takie jak wywołania operacji kodu: wyjątki, ostrzeżenia i inne istotne przetwarzanie zdarzeń."</span><span class="sxs-lookup"><span data-stu-id="597a0-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="597a0-108">Zdarzenia błędu systemu Windows działa funkcja śledzenia.</span><span class="sxs-lookup"><span data-stu-id="597a0-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="597a0-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="597a0-109">In This Section</span></span>  
 [<span data-ttu-id="597a0-110">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="597a0-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="597a0-111">W tym temacie opisano, jak skonfigurować śledzenie na różnych poziomach do własnych potrzeb określone.</span><span class="sxs-lookup"><span data-stu-id="597a0-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="597a0-112">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="597a0-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="597a0-113">W tej sekcji opisano, jak można użyć działania śledzenia i Propagacja dla korelacji end-to-end ułatwiających debugowania.</span><span class="sxs-lookup"><span data-stu-id="597a0-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="597a0-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="597a0-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="597a0-115">W tej sekcji opisano, jak umożliwia śledzenie debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="597a0-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="597a0-116">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="597a0-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="597a0-117">W tym temacie opisano, jak możesz chronić poufne informacje z widoczne, a także przydatne porady, korzystając z hostem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="597a0-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="597a0-118">Informacje o śladach</span><span class="sxs-lookup"><span data-stu-id="597a0-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="597a0-119">W tym temacie wymieniono wszystkie ślady generowane przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="597a0-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597a0-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="597a0-120">See Also</span></span>  
 [<span data-ttu-id="597a0-121">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="597a0-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
