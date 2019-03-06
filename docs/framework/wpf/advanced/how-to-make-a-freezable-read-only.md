---
title: 'Instrukcje: Utwórz Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 874724584b44c17ff6c01331295cfa1a60978d54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360358"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="f36ae-102">Instrukcje: Utwórz Freezable tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f36ae-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="f36ae-103">W tym przykładzie pokazano, jak wprowadzić <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego <xref:System.Windows.Freezable.Freeze%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f36ae-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="f36ae-104">Nie można zablokować <xref:System.Windows.Freezable> obiektu, jeśli jeden z następujących warunków jest `true` dotyczących obiektu:</span><span class="sxs-lookup"><span data-stu-id="f36ae-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
-   <span data-ttu-id="f36ae-105">Ma ona animowane lub powiązania danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f36ae-105">It has animated or data bound properties.</span></span>  
  
-   <span data-ttu-id="f36ae-106">Posiada właściwości, które są ustawiane przez zasób dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="f36ae-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="f36ae-107">Aby uzyskać więcej informacji o zasobach dynamicznej, zobacz [zasoby XAML](xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="f36ae-107">For more information about dynamic resources, see the [XAML Resources](xaml-resources.md).</span></span>  
  
-   <span data-ttu-id="f36ae-108">Zawiera on <xref:System.Windows.Freezable> obiekty podrzędne, które nie mogą być zablokowane.</span><span class="sxs-lookup"><span data-stu-id="f36ae-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="f36ae-109">Jeśli te warunki są `false` dla Twojego <xref:System.Windows.Freezable> obiektu, a nie zamierzasz go zmodyfikować, należy wziąć pod uwagę zawiesza się on do korzyści w zakresie wydajności.</span><span class="sxs-lookup"><span data-stu-id="f36ae-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f36ae-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f36ae-110">Example</span></span>  
 <span data-ttu-id="f36ae-111">Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush>, który jest typem <xref:System.Windows.Freezable> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f36ae-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="f36ae-112">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f36ae-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36ae-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f36ae-113">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="f36ae-114">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="f36ae-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="f36ae-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f36ae-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
