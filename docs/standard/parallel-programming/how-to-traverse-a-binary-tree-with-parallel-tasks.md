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
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Porady: przenoszenie drzewa binarnego z zadaniami równoległymi
W poniższym przykładzie przedstawiono dwa sposoby, w których zadania równoległe mogą służyć do przechodzenia przez strukturę danych drzewa. Stworzenie samego drzewa pozostaje ćwiczeniem.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Obie przedstawione metody są funkcjonalnie równoważne. Za pomocą <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody do tworzenia i uruchamiania zadań, można uzyskać dojście z zadań, które mogą służyć do oczekiwania na zadania i obsługi wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Biblioteka zadań równoległych (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
