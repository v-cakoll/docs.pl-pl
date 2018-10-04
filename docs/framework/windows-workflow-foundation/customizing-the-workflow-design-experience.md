---
title: Dostosowywanie środowiska projektowania przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: ed4ccb45e4470eb03cec856e865d4b50220816e3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777542"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="02868-102">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02868-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="02868-103">Scenariusze dotyczące projektowania niestandardowych działań i rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] zostały znacznie uproszczone w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02868-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="02868-104">Programowania i wdrażania są teraz łatwiejsze i bardziej elastyczne.</span><span class="sxs-lookup"><span data-stu-id="02868-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="02868-105">Zmian infrastrukturalnych klucza jest, że nowy model programowania projektanta działań bazuje na Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="02868-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="02868-106">Daje to możliwość definiowania Projektanci działań w sposób deklaratywny i rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w innych aplikacjach przy użyciu porównawczej łatwe.</span><span class="sxs-lookup"><span data-stu-id="02868-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="02868-107">Kiedy ponowny hosting, edytora wyrażeń niestandardowych mogą być tworzone do obsługi technologii IntelliSense lub domeny uproszczone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="02868-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="02868-108">Integracja za pomocą programu Windows Communication Foundation (WCF) stał się aby usprawnić przy użyciu usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02868-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="02868-109">Projektanci działań niestandardowych i drzewo elementów modelu może służyć do zwiększenia projektowania czasu środowiska w projektantach rehostowanym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="02868-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="02868-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="02868-110">In This Section</span></span>

 [<span data-ttu-id="02868-111">Używanie niestandardowych szablonów i projektantów działań</span><span class="sxs-lookup"><span data-stu-id="02868-111">Using Custom Activity Designers and Templates</span></span>](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="02868-112">W tym artykule opisano sposób tworzenia nowego niestandardowi Projektanci działań i szablony.</span><span class="sxs-lookup"><span data-stu-id="02868-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="02868-113">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="02868-113">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)

 <span data-ttu-id="02868-114">Opisuje sposób ponownego hostowania [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] poza programem Visual Studio i sposób wyświetlania błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="02868-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="02868-115">Używanie edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="02868-115">Using a Custom Expression Editor</span></span>](../../../docs/framework/windows-workflow-foundation/using-a-custom-expression-editor.md)

 <span data-ttu-id="02868-116">Opisuje sposób implementacji edytora wyrażeń niestandardowych do korzystania z przepływu pracy projektanci rehostowanym poza programem Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="02868-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="02868-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="02868-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="02868-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02868-118">See Also</span></span>

- [<span data-ttu-id="02868-119">Rozszerzanie programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="02868-119">Extending Windows Workflow Foundation</span></span>](../../../docs/framework/windows-workflow-foundation/extend.md)
- [<span data-ttu-id="02868-120">Projektant</span><span class="sxs-lookup"><span data-stu-id="02868-120">Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer.md)
- [<span data-ttu-id="02868-121">Projektanci działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="02868-121">Custom Activity Designers</span></span>](../../../docs/framework/windows-workflow-foundation/samples/custom-activity-designers.md)
- [<span data-ttu-id="02868-122">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="02868-122">Designer ReHosting</span></span>](../../../docs/framework/windows-workflow-foundation/samples/designer-rehosting.md)