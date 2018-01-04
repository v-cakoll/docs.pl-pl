---
title: "Jak określić, czy Freezable jest zamrożony"
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
helpviewer_keywords: Freezable objects [WPF], determining if frozen
ms.assetid: 92e58baa-ee12-4a9e-ac3a-ca458807a8b2
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eed85f982687bfc90f53e57ab1ec3949820097e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-whether-a-freezable-is-frozen"></a><span data-ttu-id="0112d-102">Jak określić, czy Freezable jest zamrożony</span><span class="sxs-lookup"><span data-stu-id="0112d-102">How to: Determine Whether a Freezable Is Frozen</span></span>
<span data-ttu-id="0112d-103">W tym przykładzie pokazano, jak ustalić, czy <xref:System.Windows.Freezable> obiektu jest zablokowany.</span><span class="sxs-lookup"><span data-stu-id="0112d-103">This example shows how to determine whether a <xref:System.Windows.Freezable> object is frozen.</span></span> <span data-ttu-id="0112d-104">Jeśli użytkownik próbuje zmodyfikować zablokowane <xref:System.Windows.Freezable> obiekt zgłasza <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="0112d-104">If you try to modify a frozen <xref:System.Windows.Freezable> object, it throws an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="0112d-105">Aby uniknąć generowania tego wyjątku, użyj <xref:System.Windows.Freezable.IsFrozen%2A> właściwość <xref:System.Windows.Freezable> obiektem, aby określić, czy jest zablokowana.</span><span class="sxs-lookup"><span data-stu-id="0112d-105">To avoid throwing this exception, use the <xref:System.Windows.Freezable.IsFrozen%2A> property of the <xref:System.Windows.Freezable> object to determine whether it is frozen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0112d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0112d-106">Example</span></span>  
 <span data-ttu-id="0112d-107">Poniższy przykład zawiesza się <xref:System.Windows.Media.SolidColorBrush> i sprawdza ją przy użyciu <xref:System.Windows.Freezable.IsFrozen%2A> właściwości w celu określenia, czy jest zablokowana.</span><span class="sxs-lookup"><span data-stu-id="0112d-107">The following example freezes a <xref:System.Windows.Media.SolidColorBrush> and then tests it by using the <xref:System.Windows.Freezable.IsFrozen%2A> property to determine whether it is frozen.</span></span>  
  
 [!code-csharp[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#checkisfrozenexample)]
 [!code-vb[freezablesample_procedural#CheckIsFrozenExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#checkisfrozenexample)]  
  
 <span data-ttu-id="0112d-108">Aby uzyskać więcej informacji na temat <xref:System.Windows.Freezable> obiekty, zobacz [obiektu Freezable Przegląd obiektów](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0112d-108">For more information about <xref:System.Windows.Freezable> objects, see the [Freezable Objects Overview](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0112d-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0112d-109">See Also</span></span>  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.IsFrozen%2A>  
 [<span data-ttu-id="0112d-110">Przegląd obiektów Freezable</span><span class="sxs-lookup"><span data-stu-id="0112d-110">Freezable Objects Overview</span></span>](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [<span data-ttu-id="0112d-111">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="0112d-111">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
