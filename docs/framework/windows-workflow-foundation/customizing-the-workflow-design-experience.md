---
title: Dostosowywanie środowiska projektowania przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 41be55391ae9481f6c2e4feb76443f7fb676b69d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141929"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="e6979-102">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e6979-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="e6979-103">Scenariusze projektowania działań niestandardowych i przeprowadzenia [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] są znacznie uproszczone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="e6979-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="e6979-104">Opracowywanie i wdrażanie jest teraz łatwiejsze i bardziej elastyczne.</span><span class="sxs-lookup"><span data-stu-id="e6979-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="e6979-105">Infrastruktury Key Change polega na tym, że nowy model programowania projektanta działań jest oparty na Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="e6979-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="e6979-106">Dzięki temu można z łatwością definiować projektantów działań i ponownie hostować [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w innych aplikacjach z porównywalną.</span><span class="sxs-lookup"><span data-stu-id="e6979-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="e6979-107">Podczas rehostowania można opracować Edytor wyrażeń niestandardowych do obsługi technologii IntelliSense lub uproszczonej domeny wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e6979-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="e6979-108">Integracja z usługą Windows Communication Foundation (WCF) stała się bardziej bezproblemowe dzięki użyciu usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="e6979-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="e6979-109">Projektanci działań niestandardowych i drzewo elementów modelu mogą służyć do ulepszania środowiska projektowania dla projektantów przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="e6979-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e6979-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e6979-110">In This Section</span></span>

 [<span data-ttu-id="e6979-111">Używanie niestandardowych szablonów i projektantów działań</span><span class="sxs-lookup"><span data-stu-id="e6979-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="e6979-112">Opisuje sposób tworzenia nowych projektantów i szablonów działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e6979-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="e6979-113">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="e6979-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="e6979-114">Opisuje, jak ponownie hostować [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] poza programem Visual Studio oraz jak wyświetlać błędy walidacji.</span><span class="sxs-lookup"><span data-stu-id="e6979-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="e6979-115">Używanie edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e6979-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="e6979-116">Zawiera opis sposobu implementowania niestandardowego edytora wyrażeń do użycia z projektantami przepływu pracy przemieszczonymi poza programem Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e6979-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="e6979-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="e6979-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="e6979-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e6979-118">See also</span></span>

- [<span data-ttu-id="e6979-119">Rozszerzanie programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="e6979-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="e6979-120">Projektant</span><span class="sxs-lookup"><span data-stu-id="e6979-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="e6979-121">Projektanci działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e6979-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="e6979-122">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="e6979-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
