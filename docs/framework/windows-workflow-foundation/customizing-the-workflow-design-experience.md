---
title: Dostosowywanie środowiska projektowania przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 27be398d874747b65ae051224070d3f40f1fbbb0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715137"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="11695-102">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="11695-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="11695-103">Scenariusze projektowania działań niestandardowych i rehostowania Projektant przepływu pracy systemu Windows są znacznie uproszczone w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="11695-103">The scenarios for designing custom activities and for rehosting the Windows Workflow Designer have been greatly simplified in .NET Framework 4.</span></span> <span data-ttu-id="11695-104">Opracowywanie i wdrażanie jest teraz łatwiejsze i bardziej elastyczne.</span><span class="sxs-lookup"><span data-stu-id="11695-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="11695-105">Infrastruktury Key Change polega na tym, że nowy model programowania projektanta działań jest oparty na Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="11695-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="11695-106">Dzięki temu można z łatwością definiować projektantów działań i ponownie hostować Projektant przepływu pracy w innych aplikacjach z porównywalną.</span><span class="sxs-lookup"><span data-stu-id="11695-106">This gives you the ability to define activity designers declaratively and to rehost the Workflow Designer in other applications with comparative easy.</span></span> <span data-ttu-id="11695-107">Podczas rehostowania można opracować Edytor wyrażeń niestandardowych do obsługi technologii IntelliSense lub uproszczonej domeny wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="11695-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="11695-108">Integracja z usługą Windows Communication Foundation (WCF) stała się bardziej bezproblemowe dzięki użyciu usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="11695-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="11695-109">Projektanci działań niestandardowych i drzewo elementów modelu mogą służyć do ulepszania środowiska projektowania dla projektantów przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="11695-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="11695-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="11695-110">In This Section</span></span>

 [<span data-ttu-id="11695-111">Używanie niestandardowych szablonów i projektantów działań</span><span class="sxs-lookup"><span data-stu-id="11695-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="11695-112">Opisuje sposób tworzenia nowych projektantów i szablonów działań niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="11695-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="11695-113">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="11695-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="11695-114">Opisuje sposób ponownego hostowania systemu Windows Projektant przepływu pracy poza programem Visual Studio oraz sposób wyświetlania błędów walidacji.</span><span class="sxs-lookup"><span data-stu-id="11695-114">Describes how to re-host the Windows Workflow Designer outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="11695-115">Używanie edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="11695-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="11695-116">Zawiera opis sposobu implementowania niestandardowego edytora wyrażeń do użycia z projektantami przepływu pracy przemieszczonymi poza programem Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="11695-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="11695-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="11695-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="11695-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11695-118">See also</span></span>

- [<span data-ttu-id="11695-119">Rozszerzanie programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="11695-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="11695-120">Projektant</span><span class="sxs-lookup"><span data-stu-id="11695-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="11695-121">Projektanci działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="11695-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="11695-122">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="11695-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)
