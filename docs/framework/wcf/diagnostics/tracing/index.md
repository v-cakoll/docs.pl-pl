---
title: Śledzenie
ms.date: 03/30/2017
ms.assetid: 2649eae2-dbf8-421c-9cfb-cfa9e01de87f
ms.openlocfilehash: 569a97dc21a434cd711ad4c735f828df588f3af7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578984"
---
# <a name="tracing"></a><span data-ttu-id="efeac-102">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="efeac-102">Tracing</span></span>
<span data-ttu-id="efeac-103">Windows Communication Foundation (WCF) udostępnia instrumentację aplikacji i dane diagnostyczne na potrzeby monitorowania i analizy błędów.</span><span class="sxs-lookup"><span data-stu-id="efeac-103">Windows Communication Foundation (WCF) provides application instrumentation and diagnostic data for fault monitoring and analysis.</span></span> <span data-ttu-id="efeac-104">Możesz użyć śledzenia zamiast debugera, aby zrozumieć, jak działa aplikacja, lub przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="efeac-104">You can use tracing instead of a debugger to understand how an application is behaving, or why it faults.</span></span> <span data-ttu-id="efeac-105">Możesz również skorelować błędy i przetwarzanie między składnikami, aby zapewnić kompleksowe środowisko pracy.</span><span class="sxs-lookup"><span data-stu-id="efeac-105">You can also correlate faults and processing across components to provide an end-to-end experience.</span></span>  
  
 <span data-ttu-id="efeac-106">Usługa WCF wyprowadza następujące dane do śledzenia diagnostycznego:</span><span class="sxs-lookup"><span data-stu-id="efeac-106">WCF outputs the following data for diagnostic tracing:</span></span>  
  
- <span data-ttu-id="efeac-107">Ślady dla punktów kontrolnych procesu we wszystkich składnikach aplikacji, takich jak wywołania operacji, wyjątki kodu, ostrzeżenia i inne istotne zdarzenia przetwarzania ".</span><span class="sxs-lookup"><span data-stu-id="efeac-107">Traces for process milestones across all components of the applications, such as operation calls, code exceptions, warnings and other significant processing events."</span></span>  
  
- <span data-ttu-id="efeac-108">Zdarzenia błędów systemu Windows, gdy funkcja śledzenia działa nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="efeac-108">Windows error events when the tracing feature malfunctions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efeac-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="efeac-109">In This Section</span></span>  
 [<span data-ttu-id="efeac-110">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="efeac-110">Configuring Tracing</span></span>](configuring-tracing.md)  
  
 <span data-ttu-id="efeac-111">W tym temacie opisano, jak można skonfigurować śledzenie na różnych poziomach zgodnie z konkretną potrzebami.</span><span class="sxs-lookup"><span data-stu-id="efeac-111">This topic describes how you can configure tracing at different levels to suit your specific need.</span></span>  
  
 [<span data-ttu-id="efeac-112">Kompleksowe śledzenie</span><span class="sxs-lookup"><span data-stu-id="efeac-112">End-to-End Tracing</span></span>](end-to-end-tracing.md)  
  
 <span data-ttu-id="efeac-113">W tej sekcji opisano, jak można użyć funkcji Śledzenie aktywności i Propagacja na potrzeby kompleksowej korelacji, aby pomóc w debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="efeac-113">This section describes how you can use Activity Tracing and Propagation for end-to-end correlation to assist debugging.</span></span>  
  
 [<span data-ttu-id="efeac-114">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="efeac-114">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)  
  
 <span data-ttu-id="efeac-115">W tej sekcji opisano, jak można użyć śledzenia do debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="efeac-115">This section describes how you can use tracing to debug your application.</span></span>  
  
 [<span data-ttu-id="efeac-116">Problemy dotyczące zabezpieczeń i przydatne porady na temat śledzenia</span><span class="sxs-lookup"><span data-stu-id="efeac-116">Security Concerns and Useful Tips for Tracing</span></span>](security-concerns-and-useful-tips-for-tracing.md)  
  
 <span data-ttu-id="efeac-117">W tym temacie opisano, jak można chronić poufne informacje przed ujawnieniem, a także przydatne porady dotyczące korzystania z programu WebHost.</span><span class="sxs-lookup"><span data-stu-id="efeac-117">This topic describes how you can protect sensitive information from being exposed, as well as useful tips when using WebHost.</span></span>  
  
 [<span data-ttu-id="efeac-118">Informacje o śladach</span><span class="sxs-lookup"><span data-stu-id="efeac-118">Traces Reference</span></span>](traces-reference.md)  
  
 <span data-ttu-id="efeac-119">W tym temacie wymieniono wszystkie ślady wygenerowane przez program WCF.</span><span class="sxs-lookup"><span data-stu-id="efeac-119">This topic lists all the traces generated by WCF.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efeac-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efeac-120">See also</span></span>

- [<span data-ttu-id="efeac-121">Narzędzie do przeglądania danych śledzenia usług (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="efeac-121">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
