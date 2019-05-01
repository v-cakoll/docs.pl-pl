---
title: Dostosowywanie środowiska projektowania przepływu pracy
ms.date: 03/30/2017
helpviewer_keywords:
- extending [WF], Workflow Designer
ms.assetid: 98135077-0f5d-4d16-9337-01094e843537
ms.openlocfilehash: 2d6ef24d00baa4df6dfc8e0af69c1d489b79a41f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945993"
---
# <a name="customizing-the-workflow-design-experience"></a><span data-ttu-id="7cc16-102">Dostosowywanie środowiska projektowania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7cc16-102">Customizing the Workflow Design Experience</span></span>

<span data-ttu-id="7cc16-103">Scenariusze dotyczące projektowania niestandardowych działań i rehosting [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] zostały znacznie uproszczone w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cc16-103">The scenarios for designing custom activities and for rehosting the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] have been greatly simplified in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> <span data-ttu-id="7cc16-104">Programowania i wdrażania są teraz łatwiejsze i bardziej elastyczne.</span><span class="sxs-lookup"><span data-stu-id="7cc16-104">Development and deployment are now both easier and more flexible.</span></span> <span data-ttu-id="7cc16-105">Zmian infrastrukturalnych klucza jest, że nowy model programowania projektanta działań bazuje na Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7cc16-105">The key infrastructural change is that the new activity designer programming model is built upon Windows Presentation Foundation (WPF).</span></span> <span data-ttu-id="7cc16-106">Daje to możliwość definiowania Projektanci działań w sposób deklaratywny i rehost [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] w innych aplikacjach przy użyciu porównawczej łatwe.</span><span class="sxs-lookup"><span data-stu-id="7cc16-106">This gives you the ability to define activity designers declaratively and to rehost the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in other applications with comparative easy.</span></span> <span data-ttu-id="7cc16-107">Kiedy ponowny hosting, edytora wyrażeń niestandardowych mogą być tworzone do obsługi technologii IntelliSense lub domeny uproszczone wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7cc16-107">When rehosting, a custom expression editor can be developed to support IntelliSense or a simplified expression domain.</span></span> <span data-ttu-id="7cc16-108">Integracja za pomocą programu Windows Communication Foundation (WCF) stał się aby usprawnić przy użyciu usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7cc16-108">The integration with Windows Communication Foundation (WCF) has become more seamless with use of workflow services.</span></span> <span data-ttu-id="7cc16-109">Projektanci działań niestandardowych i drzewo elementów modelu może służyć do zwiększenia projektowania czasu środowiska w projektantach rehostowanym przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="7cc16-109">Custom activity designers and the Model Item Tree can be used to enhance design time experiences in rehosted workflow designers.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="7cc16-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7cc16-110">In This Section</span></span>

 [<span data-ttu-id="7cc16-111">Używanie niestandardowych szablonów i projektantów działań</span><span class="sxs-lookup"><span data-stu-id="7cc16-111">Using Custom Activity Designers and Templates</span></span>](using-custom-activity-designers-and-templates.md)

 <span data-ttu-id="7cc16-112">W tym artykule opisano sposób tworzenia nowego niestandardowi Projektanci działań i szablony.</span><span class="sxs-lookup"><span data-stu-id="7cc16-112">Describes how to create new custom activity designers and templates.</span></span>

 [<span data-ttu-id="7cc16-113">Rehostowanie projektanta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="7cc16-113">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)

 <span data-ttu-id="7cc16-114">Opisuje sposób ponownego hostowania [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] poza programem Visual Studio i sposób wyświetlania błędów sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7cc16-114">Describes how to re-host the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] outside of Visual Studio and how to display validation errors.</span></span>

 [<span data-ttu-id="7cc16-115">Używanie edytora wyrażeń niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7cc16-115">Using a Custom Expression Editor</span></span>](using-a-custom-expression-editor.md)

 <span data-ttu-id="7cc16-116">Opisuje sposób implementacji edytora wyrażeń niestandardowych do korzystania z przepływu pracy projektanci rehostowanym poza programem Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="7cc16-116">Describes how to implement a custom expression editor to use with workflow designers rehosted outside of Visual Studio 2010.</span></span>

## <a name="reference"></a><span data-ttu-id="7cc16-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="7cc16-117">Reference</span></span>

<xref:System.Activities.Presentation.ActivityDesigner>

## <a name="see-also"></a><span data-ttu-id="7cc16-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cc16-118">See also</span></span>

- [<span data-ttu-id="7cc16-119">Rozszerzanie programu Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="7cc16-119">Extending Windows Workflow Foundation</span></span>](extend.md)
- [<span data-ttu-id="7cc16-120">Projektant</span><span class="sxs-lookup"><span data-stu-id="7cc16-120">Designer</span></span>](./samples/designer.md)
- [<span data-ttu-id="7cc16-121">Projektanci działań niestandardowych</span><span class="sxs-lookup"><span data-stu-id="7cc16-121">Custom Activity Designers</span></span>](./samples/custom-activity-designers.md)
- [<span data-ttu-id="7cc16-122">Rehostowanie projektanta</span><span class="sxs-lookup"><span data-stu-id="7cc16-122">Designer ReHosting</span></span>](./samples/designer-rehosting.md)