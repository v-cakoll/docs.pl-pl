---
title: 'Instrukcje: Przenoszenie drzewa binarnego z zadaniami równoległymi'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: 5ac81a61691ec20daafc9e18978ba5814a150383
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288072"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Instrukcje: Przenoszenie drzewa binarnego z zadaniami równoległymi
W poniższym przykładzie pokazano dwa sposoby użycia zadań równoległych do przechodzenia przez strukturę danych drzewa. Tworzenie drzewa jest pozostawione jako ćwiczenie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Dwie przedstawione metody są funkcjonalnie równoważne. Korzystając z <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody tworzenia i uruchamiania zadań, otrzymujesz dojście z zadań, których można użyć do oczekiwania na zadania i obsłużyć wyjątki.  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka zadań równoległych (TPL)](task-parallel-library-tpl.md)
