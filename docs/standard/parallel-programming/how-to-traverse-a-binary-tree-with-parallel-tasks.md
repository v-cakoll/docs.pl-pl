---
title: "Porady: przenoszenie drzewa binarnego z zadaniami równoległymi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c029a763faaa0b4d6ea5612efe079e47415b6fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="61796-102">Porady: przenoszenie drzewa binarnego z zadaniami równoległymi</span><span class="sxs-lookup"><span data-stu-id="61796-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="61796-103">Poniższy przykład przedstawia dwa sposoby, w których zadań równoległych może służyć do przechodzenia drzewa struktura danych.</span><span class="sxs-lookup"><span data-stu-id="61796-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="61796-104">Tworzenie drzewo pozostaje wykonywania.</span><span class="sxs-lookup"><span data-stu-id="61796-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61796-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="61796-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="61796-106">Te dwie metody pokazano działają tak samo.</span><span class="sxs-lookup"><span data-stu-id="61796-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="61796-107">Za pomocą <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody do tworzenia i uruchamiania zadań, wracając dojścia z zadań, które mogą być używane na oczekiwanie na zadań i obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="61796-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61796-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61796-108">See Also</span></span>  
 [<span data-ttu-id="61796-109">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="61796-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
