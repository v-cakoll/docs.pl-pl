---
title: 'Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 265b6d06f17a1dfbee3f009feff1ee1645e62a46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139258"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym
W tym dokumencie przedstawiono sposób zapobiegania dołączeniu zadania podrzędnego do zadania nadrzędnego. Zapobieganie dołączeniu zadania podrzędnego do jego obiektu nadrzędnego jest przydatne w przypadku wywołania składnika, który jest zapisany przez inną firmę, który również korzysta z zadań. Na przykład składnik innej firmy, który używa opcji <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType>, aby utworzyć obiekt <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, może spowodować problemy w kodzie, jeśli jest długotrwały lub zgłasza nieobsługiwany wyjątek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład porównuje efekty używania opcji domyślnych z efektami zapobiegania dołączeniu zadania podrzędnego do elementu nadrzędnego. Przykład tworzy obiekt <xref:System.Threading.Tasks.Task>, który wywołuje do biblioteki innej firmy, która również używa obiektu <xref:System.Threading.Tasks.Task>. Biblioteka innych firm używa opcji <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent>, aby utworzyć obiekt <xref:System.Threading.Tasks.Task>. Aplikacja używa opcji <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, aby utworzyć zadanie nadrzędne. Ta opcja powoduje, że środowisko uruchomieniowe usuwa specyfikację <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> w zadaniach podrzędnych.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Ponieważ zadanie nadrzędne nie kończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadanie podrzędne może spowodować niewłaściwe działanie ogólnej aplikacji. W tym przykładzie, gdy aplikacja używa domyślnych opcji do utworzenia zadania nadrzędnego, zadanie podrzędne musi zakończyć się przed ukończeniem zadania nadrzędnego. Gdy aplikacja używa opcji <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType>, element podrzędny nie jest dołączony do elementu nadrzędnego. W związku z tym aplikacja może wykonać dodatkową pracę po zakończeniu zadania nadrzędnego i zanim będzie musiało oczekiwać na zakończenie zadania podrzędnego.  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
