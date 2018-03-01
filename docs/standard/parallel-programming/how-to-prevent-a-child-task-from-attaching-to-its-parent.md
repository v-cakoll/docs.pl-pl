---
title: "Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym"
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
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2cab2fb9c26a8ddaa868cafebac718e5dfd6baa0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Porady: Jak zapobiec łączeniu zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym
Ten dokument pokazano, jak zapobiec łączeniu zadania podrzędnego z odpowiadającym zadaniem nadrzędnym. Zapobieganie zadania podrzędnego z odpowiadającym mu zadaniem nadrzędnym jest przydatne, gdy wywołanie składnika, która została napisana przez innych firm i używa również zadania. Na przykład składnikiem innej firmy, który używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> obiektu może spowodować problemy w kodzie, jeśli jest długotrwałe lub nieobsługiwany wyjątek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład porównuje skutków przy użyciu opcji domyślnych skutki zapobieganie zadania podrzędnego z odpowiadającym zadaniem nadrzędnym. W przykładzie jest tworzony <xref:System.Threading.Tasks.Task> obiektu, który odwołuje się do biblioteki innej firmy, który także używa <xref:System.Threading.Tasks.Task> obiektu. Biblioteka innych firm używa <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> opcję, aby utworzyć <xref:System.Threading.Tasks.Task> obiektu. Aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcję, aby utworzyć zadaniem nadrzędnym. Ta opcja powoduje, że środowisko uruchomieniowe, aby usunąć <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> Specyfikacja zadania podrzędne.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Ponieważ zadaniem nadrzędnym nie zakończy się do momentu zakończenia wszystkich zadań podrzędnych, długotrwałe zadania podrzędnego może spowodować ogólną aplikacji do niskiej wydajności. W tym przykładzie Jeśli aplikacja używa domyślnych opcji, można utworzyć zadania nadrzędnego zadania podrzędnego musi zakończyć przed zakończeniem zadaniem nadrzędnym. Jeśli aplikacja używa <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> opcji, obiekt podrzędny nie jest dołączony do obiektu nadrzędnego. Aplikacja może wykonywać dodatkowe czynności, po zakończeniu zadania nadrzędnego i przed należy poczekać na zakończenie zadania podrzędne.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Skopiuj przykładowy kod i wklej go w projekcie programu Visual Studio lub wklej go w pliku o nazwie `DenyChildAttach.cs` (`DenyChildAttach.vb` dla [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a następnie uruchom następujące polecenie w oknie Wiersz polecenia programu Visual Studio.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **CSC.exe DenyChildAttach.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **vbc.exe DenyChildAttach.vb**  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne oparte na zadaniach](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
