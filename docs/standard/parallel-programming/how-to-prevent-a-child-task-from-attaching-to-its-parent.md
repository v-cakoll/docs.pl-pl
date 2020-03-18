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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139258"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym
W tym dokumencie pokazano, jak zapobiec dołączaniu zadania podrzędnego do zadania nadrzędnego. Zapobieganie dołączaniu zadania podrzędnego do jego elementu nadrzędnego jest przydatne podczas wywoływania składnika napisanego przez stronę trzecią, który również używa zadań. Na przykład składnik innej firmy, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> który używa <xref:System.Threading.Tasks.Task> opcji <xref:System.Threading.Tasks.Task%601> do tworzenia lub obiektu może powodować problemy w kodzie, jeśli jest długotrwały lub zgłasza nieobsługiwany wyjątek.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie porównano efekty używania opcji domyślnych z efektami uniemożliwiania dołączania zadania podrzędnego do rodzica. Przykład tworzy <xref:System.Threading.Tasks.Task> obiekt, który wywołuje do biblioteki innej <xref:System.Threading.Tasks.Task> firmy, która również używa obiektu. Biblioteka innych firm używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcji do <xref:System.Threading.Tasks.Task> utworzenia obiektu. Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji, aby utworzyć zadanie nadrzędne. Ta opcja powoduje, że czas <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> wykonywania powoduje usunięcie specyfikacji w zadaniach podrzędnych.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Ponieważ zadanie nadrzędne nie kończy się, dopóki wszystkie zadania podrzędne nie zakończą się, długotrwałe zadanie podrzędne może spowodować, że ogólna aplikacja będzie działać słabo. W tym przykładzie, gdy aplikacja używa opcji domyślnych do utworzenia zadania nadrzędnego, zadanie podrzędne musi zakończyć się przed zakończeniem zadania nadrzędnego. Gdy aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> tej opcji, dziecko nie jest dołączone do rodzica. W związku z tym aplikacja może wykonać dodatkową pracę po zakończeniu zadania nadrzędnego i przed musi czekać na zakończenie zadania podrzędne.  
  
## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
