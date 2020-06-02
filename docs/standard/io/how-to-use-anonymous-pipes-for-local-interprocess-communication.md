---
title: 'Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej'
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
ms.openlocfilehash: 9962471697888041e98e38dd5f7feaecc306894d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291789"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Instrukcje: Stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej
Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym. Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniejszego obciążenia. Można używać potoków anonimowych, aby ułatwić komunikację międzyprocesową na komputerze lokalnym. Nie można używać potoków anonimowych do komunikacji za pośrednictwem sieci.  
  
 Aby zaimplementować anonimowe potoki, <xref:System.IO.Pipes.AnonymousPipeServerStream> Użyj <xref:System.IO.Pipes.AnonymousPipeClientStream> klas i.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu potoków anonimowych. Ten przykład tworzy <xref:System.IO.Pipes.AnonymousPipeServerStream> obiekt w procesie nadrzędnym z <xref:System.IO.Pipes.PipeDirection> wartością <xref:System.IO.Pipes.PipeDirection.Out> . Następnie proces nadrzędny tworzy proces podrzędny przy użyciu dojścia klienta do utworzenia <xref:System.IO.Pipes.AnonymousPipeClientStream> obiektu. Proces podrzędny ma <xref:System.IO.Pipes.PipeDirection> wartość <xref:System.IO.Pipes.PipeDirection.In> .  
  
 Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego. Ten ciąg jest wyświetlany w konsoli w procesie podrzędnym.  
  
 Poniższy przykład przedstawia proces serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia proces klienta. Proces serwera uruchamia proces klienta i zapewnia, że proces obsługi klienta. Utworzony plik wykonywalny z kodu klienta powinien mieć nazwę `pipeClient.exe` i być kopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Zobacz także

- [Potoki](pipe-operations.md)
- [Instrukcje: Stosowanie nazwanych potoków do sieciowej komunikacji międzyprocesowej](how-to-use-named-pipes-for-network-interprocess-communication.md)
