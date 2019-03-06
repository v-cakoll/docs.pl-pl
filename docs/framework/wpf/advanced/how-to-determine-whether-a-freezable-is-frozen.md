---
title: 'Instrukcje: Określ, czy Freezable jest zamrożony'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
ms.openlocfilehash: 005bb27803830a2e38a7b143d2c4cff669ad1da6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362516"
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="25b0e-102">Instrukcje: Określ, czy Freezable jest zamrożony</span><span class="sxs-lookup"><span data-stu-id="25b0e-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="25b0e-103">W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Freezable> obiektu jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="25b0e-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="25b0e-104">Jeśli spróbujesz zmodyfikować zamrożone <xref:System.Windows.Freezable> obiekt, w wyniku weryfikacji zgłasza wyjątek <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="25b0e-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="25b0e-105">Aby uniknąć, zostanie zgłoszony wyjątek, należy użyć <xref:System.Windows.Freezable.IsFrozen%2A> właściwość <xref:System.Windows.Freezable> obiektu, aby ustalić, czy jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="25b0e-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25b0e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="25b0e-106">Example</span></span>  
 <span data-ttu-id="25b0e-107">Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush> i sprawdza ją za pomocą <xref:System.Windows.Freezable.IsFrozen%2A> właściwości w celu określenia, czy jest zablokowane.</span><span class="sxs-lookup"><span data-stu-id="25b0e-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="25b0e-108">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [Przegląd obiektów Freezable](freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="25b0e-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b0e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25b0e-109">See also</span></span>
- <xref:System.Windows.Freezable>
- <xref:System.Windows.Freezable.IsFrozen%2A>
- [<span data-ttu-id="25b0e-110">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="25b0e-110">Freezable Objects Overview</span></span>](freezable-objects-overview.md)
- [<span data-ttu-id="25b0e-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="25b0e-111">How-to Topics</span></span>](base-elements-how-to-topics.md)
