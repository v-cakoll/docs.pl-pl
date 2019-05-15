---
title: 'Instrukcje: Zapobieganie łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 55b9c6c7175d8c7c33d8bfa03330c8e4b8816531
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592025"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Instrukcje: Zapobieganie łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym
Ten dokument przedstawia sposób zapobiec łączeniu zadania podrzędnego z zadaniem do zadania nadrzędnego. Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym jest przydatne w przypadku, gdy wywołujesz składnik, który jest zapisywany przez stronę trzecią i używa również zadania. Na przykład składnikiem innej firmy, który używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu może spowodować problemy w kodzie, gdy jest długotrwałe lub zwraca nieobsługiwany wyjątek.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie porównano skutki przy użyciu opcji domyślnej do efektów uniemożliwianie zadaniu podrzędnemu dołączania do elementu nadrzędnego. W przykładzie jest tworzony <xref:System.Threading.Tasks.Task> obiekt, który wywołuje bibliotekę innych firm, która używa również <xref:System.Threading.Tasks.Task> obiektu. Używa biblioteki innego producenta <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> obiektu. Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby utworzyć zadanie nadrzędne. Ta opcja powoduje, że środowisko uruchomieniowe, aby usunąć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specyfikacji w zadaniach podrzędnych.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Ponieważ zadanie nadrzędne nie zakończy się aż do zakończenia wszystkich zadań podrzędnych, długo uruchamiające się zadanie podrzędne może spowodować cała aplikacja do niskiej wydajności. W tym przykładzie Jeśli aplikacja używa domyślnych opcji do utworzenia zadania nadrzędnego, zadanie podrzędne musi zakończyć przed zakończeniem zadania nadrzędnego. Jeśli aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji element podrzędny nie jest dołączony do obiektu nadrzędnego. Aplikację można wykonać dodatkową pracę, po zakończeniu zadania nadrzędnego i przed musi czekać na zakończenie zadania podrzędnego.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
