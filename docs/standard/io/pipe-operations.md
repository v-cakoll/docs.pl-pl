---
title: Operacje potoku w .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706559"
---
# <a name="pipe-operations-in-net"></a>Operacje potoku w .NET
Rury zapewniają środki komunikacji międzyprocesowej. Istnieją dwa rodzaje rur:  
  
- Anonimowe rury.  
  
     Anonimowe potoki zapewniają komunikację międzyprocesową na komputerze lokalnym. Anonimowe potoki wymagają mniejszego narzutów niż nazwane potoki, ale oferują ograniczone usługi. Anonimowe potoki są jednokierunkowe i nie mogą być używane w sieci. Obsługują one tylko jedno wystąpienie serwera. Anonimowe potoki są przydatne do komunikacji między wątkami lub między procesami nadrzędnymi i podrzędnych, gdzie uchwyty potoku mogą być łatwo przekazywane do procesu podrzędne podczas jego tworzenia.  
  
     W .NET implementujesz potoki <xref:System.IO.Pipes.AnonymousPipeServerStream> anonimowe przy użyciu i <xref:System.IO.Pipes.AnonymousPipeClientStream> klas.  
  
     Zobacz [Jak: Korzystanie z anonimowych potoków do komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Nazwane potoki.  
  
     Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku. Nazwane potoki mogą być jednokierunkowe lub dupleksowe. Obsługują komunikację opartą na komunikatach i umożliwiają wielu klientom jednoczesne łączenie się z procesem serwera przy użyciu tej samej nazwy potoku. Nazwane potoki obsługują również personifikację, która umożliwia łączenie procesów w celu używania własnych uprawnień na serwerach zdalnych.  
  
     W .NET implementujesz nazwane potoki przy użyciu <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream> klas.  
  
     Zobacz [Jak: Używanie nazwanych potoków do komunikacji międzyprocesowej sieci](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Zobacz też

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
- [Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
