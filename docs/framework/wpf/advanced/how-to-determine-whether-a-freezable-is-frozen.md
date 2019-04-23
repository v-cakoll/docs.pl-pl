---
title: 'Instrukcje: Określanie, czy obiekt Freezable jest zamrożony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 6a63862d35f2c40289ea6445eb3dab8a2abe4a61
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197064"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="6a73c-102">Instrukcje: Określanie, czy obiekt Freezable jest zamrożony</span><span class="sxs-lookup"><span data-stu-id="6a73c-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="6a73c-103">W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Freezable> obiektu jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="6a73c-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="6a73c-104">Jeśli spróbujesz zmodyfikować zamrożone <xref:System.Windows.Freezable> obiekt, w wyniku weryfikacji zgłasza wyjątek <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="6a73c-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="6a73c-105">Aby uniknąć, zostanie zgłoszony wyjątek, należy użyć <xref:System.Windows.Freezable.IsFrozen%2A> właściwość <xref:System.Windows.Freezable> obiektu, aby ustalić, czy jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="6a73c-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a73c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a73c-106">Example</span></span>  
 <span data-ttu-id="6a73c-107">Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush> i sprawdza ją za pomocą <xref:System.Windows.Freezable.IsFrozen%2A> właściwości w celu określenia, czy jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="6a73c-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="6a73c-108">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6a73c-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a73c-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a73c-109">See also</span></span>

- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="6a73c-110">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="6a73c-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="6a73c-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="6a73c-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
