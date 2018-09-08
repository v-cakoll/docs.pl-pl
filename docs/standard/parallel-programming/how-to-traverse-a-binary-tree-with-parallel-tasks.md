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
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Porady: przenoszenie drzewa binarnego z zadaniami równoległymi
Poniższy przykład przedstawia dwa sposoby, w których zadań równoległych może służyć do przechodzenia struktury drzewa danych. Tworzenie drzewa, sama zostanie pozostawiony w charakterze ćwiczenia.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Te dwie metody, wyświetlane są funkcjonalnie równoważne. Za pomocą <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody do tworzenia i uruchamiania zadań podrzędnych, wracając uchwyt z zadania, które mogą być używane na oczekiwanie na zadań i obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
