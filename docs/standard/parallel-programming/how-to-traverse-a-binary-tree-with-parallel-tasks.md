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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fd937d6ce2edf0c47fce78d48a90ec1aa409eef
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44196650"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="fe542-102">Porady: przenoszenie drzewa binarnego z zadaniami równoległymi</span><span class="sxs-lookup"><span data-stu-id="fe542-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="fe542-103">Poniższy przykład przedstawia dwa sposoby, w których zadań równoległych może służyć do przechodzenia struktury drzewa danych.</span><span class="sxs-lookup"><span data-stu-id="fe542-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="fe542-104">Tworzenie drzewa, sama zostanie pozostawiony w charakterze ćwiczenia.</span><span class="sxs-lookup"><span data-stu-id="fe542-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe542-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe542-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="fe542-106">Te dwie metody, wyświetlane są funkcjonalnie równoważne.</span><span class="sxs-lookup"><span data-stu-id="fe542-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="fe542-107">Za pomocą <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody do tworzenia i uruchamiania zadań podrzędnych, wracając uchwyt z zadania, które mogą być używane na oczekiwanie na zadań i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="fe542-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe542-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe542-108">See also</span></span>

- [<span data-ttu-id="fe542-109">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="fe542-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
