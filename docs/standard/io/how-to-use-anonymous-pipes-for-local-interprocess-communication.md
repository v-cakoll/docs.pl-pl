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
ms.openlocfilehash: ea4aee60d090a56eb0cf3f2a81c1b05c04806d4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77627997"
---
# <a name="how-to-use-anonymous-pipes-for-local-interprocess-communication"></a>Porady: stosowanie anonimowych potoków do lokalnej komunikacji międzyprocesowej
Anonimowe potoki zapewniają komunikację międzyprocesową na komputerze lokalnym. Oferują one mniej funkcji niż nazwane potoki, ale również wymagają mniej narzutów. Za pomocą anonimowych potoków można ułatwić komunikację międzyprocesową na komputerze lokalnym. Nie można używać anonimowych potoków do komunikacji za pomocą sieci.  
  
 Aby zaimplementować anonimowe <xref:System.IO.Pipes.AnonymousPipeServerStream> <xref:System.IO.Pipes.AnonymousPipeClientStream> potoki, należy użyć i klas.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono sposób wysyłania ciągu z procesu nadrzędnego do procesu podrzędnego przy użyciu anonimowych potoków. W tym <xref:System.IO.Pipes.AnonymousPipeServerStream> przykładzie tworzy obiekt w <xref:System.IO.Pipes.PipeDirection> procesie <xref:System.IO.Pipes.PipeDirection.Out>nadrzędnym o wartości . Proces nadrzędny następnie tworzy proces podrzędny przy <xref:System.IO.Pipes.AnonymousPipeClientStream> użyciu dojścia klienta do utworzenia obiektu. Proces podrzędny <xref:System.IO.Pipes.PipeDirection> ma <xref:System.IO.Pipes.PipeDirection.In>wartość .  
  
 Następnie proces nadrzędny wysyła ciąg dostarczony przez użytkownika do procesu podrzędnego. Ciąg jest wyświetlany do konsoli w procesie podrzędnym.  
  
 W poniższym przykładzie przedstawiono proces serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeServerStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeServerStream_Sample/vb/program.vb#01)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono proces klienta. Proces serwera uruchamia proces klienta i daje temu procesowi dojście klienta. Wynikowy plik wykonywalny z `pipeClient.exe` kodu klienta powinien zostać nazwany i skopiowany do tego samego katalogu co plik wykonywalny serwera przed uruchomieniem procesu serwera.  
  
 [!code-cpp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cpp/program.cpp#01)]
 [!code-csharp[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/cs/Program.cs#01)]
 [!code-vb[System.IO.Pipes.AnonymousPipeClientStream_Sample#01](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Pipes.AnonymousPipeClientStream_Sample/vb/program.vb#01)]  
  
## <a name="see-also"></a>Zobacz też

- [Potoki](../../../docs/standard/io/pipe-operations.md)
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
