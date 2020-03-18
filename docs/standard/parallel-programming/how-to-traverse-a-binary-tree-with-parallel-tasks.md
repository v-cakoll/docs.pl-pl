---
title: 'Porady: przenoszenie drzewa binarnego z zadaniami równoległymi'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: b79337e6ee8057506ff87c696cecd6b038eeebfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141644"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="8e62a-102">Porady: przenoszenie drzewa binarnego z zadaniami równoległymi</span><span class="sxs-lookup"><span data-stu-id="8e62a-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="8e62a-103">W poniższym przykładzie przedstawiono dwa sposoby, w których zadania równoległe mogą służyć do przechodzenia przez strukturę danych drzewa.</span><span class="sxs-lookup"><span data-stu-id="8e62a-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="8e62a-104">Stworzenie samego drzewa pozostaje ćwiczeniem.</span><span class="sxs-lookup"><span data-stu-id="8e62a-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e62a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e62a-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="8e62a-106">Obie przedstawione metody są funkcjonalnie równoważne.</span><span class="sxs-lookup"><span data-stu-id="8e62a-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="8e62a-107">Za pomocą <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody do tworzenia i uruchamiania zadań, można uzyskać dojście z zadań, które mogą służyć do oczekiwania na zadania i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="8e62a-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e62a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e62a-108">See also</span></span>

- [<span data-ttu-id="8e62a-109">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="8e62a-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
