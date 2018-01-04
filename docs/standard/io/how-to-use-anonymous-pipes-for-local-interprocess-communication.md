---
title: "Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej"
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
- cpp
helpviewer_keywords:
- anonymous pipes [.NET Framework]
- parent-child communication [.NET Framework]
- pipes [.NET Framework]
- one-way communication [.NET Framework]
- local computer communication [.NET Framework], pipes
ms.assetid: e7773c77-c646-4a01-8a96-a003d59fc4c9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0679e09a52fab68d8da83863afde1568794ba561
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej
Potoki anonimowe zapewnienia komunikacji międzyprocesowej na komputerze lokalnym. One oferują mniej funkcji niż nazwane potoki, ale również wymagać mniejsze koszty. Potoki anonimowe umożliwia łatwiejsze komunikacji międzyprocesowej na komputerze lokalnym. Potoki anonimowe nie można używać do komunikacji za pośrednictwem sieci.  
  
 Aby zaimplementować potoki anonimowe, użyj <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób wysyłania ciąg z procesu nadrzędnego procesów podrzędnych za pomocą potoków anonimowych. Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiekt w ramach procesu nadrzędnego z <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.Out>. Proces nadrzędny tworzy następnie procesu podrzędnego przy użyciu dojścia klienta w celu utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu. Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Proces nadrzędny wysyła następnie ciągu podanego przez użytkownika do procesu podrzędnego. Ciąg jest wyświetlana w konsoli w procesu podrzędnego.  
  
 W poniższym przykładzie przedstawiono proces serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono procesu klienta. Proces serwera rozpoczyna proces klienta i zapewnia procesu obsługi klienta. Wynikowy plik wykonywalny z kodu klienta powinno być nazwanym `pipeClient.exe` i skopiowane do katalogu, co serwer pliku wykonywalnego przed uruchomieniem procesu serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Zobacz też  
 [Potoki](../../../docs/standard/io/pipe-operations.md)  
 [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
