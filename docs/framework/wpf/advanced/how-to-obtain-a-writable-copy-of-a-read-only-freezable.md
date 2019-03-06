---
title: 'Instrukcje: Uzyskaj zapisywalną kopię Freezable tylko do odczytu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 08b7007911d15019c043a74e093ccc0fba072fd1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361619"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a><span data-ttu-id="14620-102">Instrukcje: Uzyskaj zapisywalną kopię Freezable tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="14620-102">How to: Obtain a Writable Copy of a Read-Only Freezable</span></span>
<span data-ttu-id="14620-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Freezable.Clone%2A> metodę w celu utworzenia zapisywalną kopię tylko do odczytu <xref:System.Windows.Freezable>.</span><span class="sxs-lookup"><span data-stu-id="14620-103">This example shows how to use the <xref:System.Windows.Freezable.Clone%2A> method to create a writable copy of a read-only <xref:System.Windows.Freezable>.</span></span>  
  
 <span data-ttu-id="14620-104">Po <xref:System.Windows.Freezable> obiekt jest oznaczony jako tylko do odczytu ("zamrożona"), nie można go modyfikować.</span><span class="sxs-lookup"><span data-stu-id="14620-104">After a <xref:System.Windows.Freezable> object is marked as read-only ("frozen"), you cannot modify it.</span></span> <span data-ttu-id="14620-105">Można jednak użyć <xref:System.Windows.Freezable.Clone%2A> metodę, aby sklonować można modyfikować zamrożonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="14620-105">However, you can use the <xref:System.Windows.Freezable.Clone%2A> method to create a modifiable clone of the frozen object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14620-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="14620-106">Example</span></span>  
 <span data-ttu-id="14620-107">Poniższy przykład obejmuje tworzenie modyfikowalnych klonu zamrożone <xref:System.Windows.Media.SolidColorBrush> obiektu.</span><span class="sxs-lookup"><span data-stu-id="14620-107">The following example creates a modifiable clone of a frozen <xref:System.Windows.Media.SolidColorBrush> object.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CloneExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 <span data-ttu-id="14620-108">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="14620-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14620-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="14620-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.CloneCurrentValue%2A>
- [<span data-ttu-id="14620-110">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="14620-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="14620-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="14620-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
