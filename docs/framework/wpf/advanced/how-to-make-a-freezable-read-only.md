---
title: "Jak utworzyć Freezable tylko do odczytu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aa6d3f7109e8258dff0a07556bc8572f6071c961
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="9d870-102">Jak utworzyć Freezable tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9d870-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="9d870-103">W tym przykładzie pokazano, jak utworzyć <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego <xref:System.Windows.Freezable.Freeze%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9d870-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="9d870-104">Nie można zablokować <xref:System.Windows.Freezable> obiektu, jeśli którykolwiek z następujących warunków jest `true` o obiektu:</span><span class="sxs-lookup"><span data-stu-id="9d870-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="9d870-105">Ma on animowany lub właściwości powiązany z danymi.</span><span class="sxs-lookup"><span data-stu-id="9d870-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="9d870-106">Ma właściwości, które są ustawiane przez zasobu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="9d870-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="9d870-107">Aby uzyskać więcej informacji o zasobach dynamicznej, zobacz [zasobów XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="9d870-107">For more information about dynamic resources, see the [XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="9d870-108">Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie może być zablokowany.</span><span class="sxs-lookup"><span data-stu-id="9d870-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="9d870-109">Jeśli te warunki są `false` dla Twojego <xref:System.Windows.Freezable> obiektu, a nie zamierzasz go zmodyfikować, należy wziąć pod uwagę zamrażanie go do korzyści wydajności.</span><span class="sxs-lookup"><span data-stu-id="9d870-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d870-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9d870-110">Example</span></span>  
 <span data-ttu-id="9d870-111">Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush>, który jest typem <xref:System.Windows.Freezable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9d870-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="9d870-112">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9d870-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d870-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d870-113">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CanFreeze%2A>  
 <xref:System.Windows.Freezable.Freeze%2A>  
 [<span data-ttu-id="9d870-114">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="9d870-114">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="9d870-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="9d870-115">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
