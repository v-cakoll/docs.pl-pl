---
title: 'Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db23b424d4357ad94b8b0de66ca71726b765321e
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709026"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej
Anonimowe potoki zapewniają komunikację międzyprocesorową na komputerze lokalnym. One oferuje mniej funkcji niż nazwane potoki, ale wymagają również mniejsze obciążenie. Za pomocą potoków anonimowych ułatwiają komunikację międzyprocesorową na komputerze lokalnym. Anonimowe potoki nie można używać do komunikacji za pośrednictwem sieci.  
  
 Aby zaimplementować potoki anonimowe, użyj <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób wysyłania ciąg z procesu nadrzędnego do procesu podrzędnego, za pomocą potoków anonimowych. Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiektu w proces nadrzędny <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.Out>. Proces nadrzędny następnie tworzy proces podrzędny przy użyciu dojścia klienta w celu utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu. Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Proces nadrzędny wysyła następnie ciąg dostarczone przez użytkownika do procesu podrzędnego. Ten ciąg jest wyświetlana w konsoli w procesu podrzędnego.  
  
 Poniższy przykład przedstawia proces serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje procesu klienta. Proces serwera rozpoczyna się proces klienta i zapewnia procesu dojście do klienta. Wynikowy plik wykonywalny z poziomu kodu klienta powinno się nazywać `pipeClient.exe` i skopiowany do tego samego katalogu co serwer pliku wykonywalnego przed uruchomieniem procesu serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Zobacz także

- [Potoki](../../../docs/standard/io/pipe-operations.md)  
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
