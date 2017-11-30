---
title: "Śledzenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0a291e3ca277bc58f69b8016c523b383b3cece8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="tracing"></a><span data-ttu-id="5f2b2-102">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="5f2b2-102">Tracing</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="5f2b2-103">udostępnia instrumentacji aplikacji i danych diagnostycznych dla błędów monitorowania i analizy.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-103"> provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="5f2b2-104">Śledzenie można użyć zamiast debugera zrozumienie zachowania aplikacji lub przyczynę błędów.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="5f2b2-105">Między składnikami, aby zapewnić środowisko end-to-end można również dostosować błędów i przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="5f2b2-106">Wyświetla następujące dane śledzenia diagnostycznego:</span><span class="sxs-lookup"><span data-stu-id="5f2b2-106"> outputs the following data for diagnostic tracing:</span></span>  
  
-   <span data-ttu-id="5f2b2-107">Ślady punktów kontrolnych procesu dotyczące wszystkich składników aplikacji, takie jak wywołania operacji kodu: wyjątki, ostrzeżenia i inne istotne przetwarzanie zdarzeń."</span><span class="sxs-lookup"><span data-stu-id="5f2b2-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
-   <span data-ttu-id="5f2b2-108">Zdarzenia błędu systemu Windows działa funkcja śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f2b2-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5f2b2-109">In This Section</span></span>  
 [<span data-ttu-id="5f2b2-110">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="5f2b2-110">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
 <span data-ttu-id="5f2b2-111">W tym temacie opisano, jak skonfigurować śledzenie na różnych poziomach do własnych potrzeb określone.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="5f2b2-112">Śledzenia end-to-End</span><span class="sxs-lookup"><span data-stu-id="5f2b2-112">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)  
  
 <span data-ttu-id="5f2b2-113">W tej sekcji opisano, jak można użyć działania śledzenia i Propagacja dla korelacji end-to-end ułatwiających debugowania.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="5f2b2-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="5f2b2-114">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="5f2b2-115">W tej sekcji opisano, jak umożliwia śledzenie debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="5f2b2-116">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="5f2b2-116">Security Concerns and Useful Tips for Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="5f2b2-117">W tym temacie opisano, jak możesz chronić poufne informacje z widoczne, a także przydatne porady, korzystając z hostem sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5f2b2-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="5f2b2-118">Informacje o śladach</span><span class="sxs-lookup"><span data-stu-id="5f2b2-118">Traces Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/traces-reference.md)  
  
 <span data-ttu-id="5f2b2-119">W tym temacie wymieniono wszystkie ślady generowane przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5f2b2-119">This topic lists all the traces generated by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f2b2-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f2b2-120">See Also</span></span>  
 [<span data-ttu-id="5f2b2-121">Narzędzie podglądu śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="5f2b2-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
