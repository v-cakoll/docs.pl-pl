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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141644"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="b293f-102">Porady: przenoszenie drzewa binarnego z zadaniami równoległymi</span><span class="sxs-lookup"><span data-stu-id="b293f-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="b293f-103">W poniższym przykładzie pokazano dwa sposoby użycia zadań równoległych do przechodzenia przez strukturę danych drzewa.</span><span class="sxs-lookup"><span data-stu-id="b293f-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="b293f-104">Tworzenie drzewa jest pozostawione jako ćwiczenie.</span><span class="sxs-lookup"><span data-stu-id="b293f-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b293f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="b293f-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="b293f-106">Dwie przedstawione metody są funkcjonalnie równoważne.</span><span class="sxs-lookup"><span data-stu-id="b293f-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="b293f-107">Za pomocą metody <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> do tworzenia i uruchamiania zadań, otrzymujesz obsługę z zadań, których można użyć do oczekiwania na zadania i obsłużyć wyjątki.</span><span class="sxs-lookup"><span data-stu-id="b293f-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b293f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b293f-108">See also</span></span>

- [<span data-ttu-id="b293f-109">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="b293f-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
