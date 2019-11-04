---
title: Jak utworzyć Freezable tylko do odczytu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], making read-only
ms.assetid: 6c544b7d-d3c9-4736-aa90-4b8728234ccb
ms.openlocfilehash: 4185966d864be425bc631953461f6f27ab983bee
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460070"
---
# <a name="how-to-make-a-freezable-read-only"></a><span data-ttu-id="6801a-102">Jak utworzyć Freezable tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6801a-102">How to: Make a Freezable Read-Only</span></span>
<span data-ttu-id="6801a-103">Ten przykład pokazuje, jak wykonać <xref:System.Windows.Freezable> tylko do odczytu przez wywołanie jego metody <xref:System.Windows.Freezable.Freeze%2A>.</span><span class="sxs-lookup"><span data-stu-id="6801a-103">This example shows how to make a <xref:System.Windows.Freezable> read-only by calling its <xref:System.Windows.Freezable.Freeze%2A> method.</span></span>  
  
 <span data-ttu-id="6801a-104">Nie można zablokować obiektu <xref:System.Windows.Freezable>, jeśli jeden z następujących warunków jest `true` o obiekcie:</span><span class="sxs-lookup"><span data-stu-id="6801a-104">You cannot freeze a <xref:System.Windows.Freezable> object if any one of the following conditions is `true` about the object:</span></span>  
  
- <span data-ttu-id="6801a-105">Ma właściwości animowane lub powiązane z danymi.</span><span class="sxs-lookup"><span data-stu-id="6801a-105">It has animated or data bound properties.</span></span>  
  
- <span data-ttu-id="6801a-106">Ma właściwości, które są ustawiane przez zasób dynamiczny.</span><span class="sxs-lookup"><span data-stu-id="6801a-106">It has properties that are set by a dynamic resource.</span></span> <span data-ttu-id="6801a-107">Aby uzyskać więcej informacji na temat zasobów dynamicznych, zobacz [zasoby XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="6801a-107">For more information about dynamic resources, see the [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>  
  
- <span data-ttu-id="6801a-108">Zawiera <xref:System.Windows.Freezable> obiektów podrzędnych, które nie mogą być zamrożone.</span><span class="sxs-lookup"><span data-stu-id="6801a-108">It contains <xref:System.Windows.Freezable> sub-objects that cannot be frozen.</span></span>  
  
 <span data-ttu-id="6801a-109">Jeśli te warunki są `false` dla obiektu <xref:System.Windows.Freezable> i nie zamierzasz go modyfikować, rozważ zamarzanie go w celu uzyskania korzyści z wydajności.</span><span class="sxs-lookup"><span data-stu-id="6801a-109">If these conditions are `false` for your <xref:System.Windows.Freezable> object and you do not intend to modify it, consider freezing it to gain performance benefits.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6801a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6801a-110">Example</span></span>  
 <span data-ttu-id="6801a-111">Poniższy przykład zawiesza <xref:System.Windows.Media.SolidColorBrush>, który jest typem obiektu <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="6801a-111">The following example freezes a <xref:System.Windows.Media.SolidColorBrush>, which is a type of <xref:System.Windows.Freezable> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#FreezeExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#freezeexample1)]
 [!code-vb[freezablesample_procedural#FreezeExample1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#freezeexample1)]  
  
 <span data-ttu-id="6801a-112">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiektów, zobacz [Omówienie obiektów Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6801a-112">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6801a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6801a-113">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CanFreeze%2A>
- <xref:System.Windows.Freezable.Freeze%2A>
- [<span data-ttu-id="6801a-114">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="6801a-114">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="6801a-115">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6801a-115">How-to Topics</span></span>](base-elements-how-to-topics.md)
