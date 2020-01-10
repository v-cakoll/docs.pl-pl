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
ms.openlocfilehash: 16018be820951a2739d602edb99845eb89495d5e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706650"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej
Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym. Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniejszego obciążenia. Można używać potoków anonimowych, aby ułatwić komunikację międzyprocesową na komputerze lokalnym. Nie można używać potoków anonimowych do komunikacji za pośrednictwem sieci.  
  
 Aby zaimplementować anonimowe potoki, użyj klas <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu potoków anonimowych. Ten przykład tworzy obiekt <xref:System.IO.Pipes.AnonymousPipeServerStream> w procesie nadrzędnym z <xref:System.IO.Pipes.PipeDirection> wartością <xref:System.IO.Pipes.PipeDirection.Out>. Następnie proces nadrzędny tworzy proces podrzędny przy użyciu dojścia klienta do tworzenia obiektu <xref:System.IO.Pipes.AnonymousPipeClientStream>. Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In>.  
  
 Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego. Ten ciąg jest wyświetlany w konsoli w procesie podrzędnym.  
  
 Poniższy przykład przedstawia proces serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia proces klienta. Proces serwera uruchamia proces klienta i zapewnia, że proces obsługi klienta. Utworzony plik wykonywalny z kodu klienta powinien mieć nazwę `pipeClient.exe` i być kopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Zobacz także

- [Potoki](../../../docs/standard/io/pipe-operations.md)
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
