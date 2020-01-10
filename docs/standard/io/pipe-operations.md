---
title: Operacje potokowe w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: 693dd1eb0b0b9bb87973eead26a344ed67641e34
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706559"
---
# <a name="pipe-operations-in-net"></a>Operacje potokowe w programie .NET
Potoki zapewniają metodę komunikacji międzyprocesowej. Istnieją dwa typy potoków:  
  
- Potoki anonimowe.  
  
     Potoki anonimowe zapewniają komunikację międzyprocesową na komputerze lokalnym. Potoki anonimowe wymagają mniej obciążenia niż potoki nazwane, ale oferują ograniczone usługi. Potoki anonimowe są jednokierunkowe i nie mogą być używane w sieci. Obsługują one tylko jedno wystąpienie serwera. Potoki anonimowe są przydatne do komunikacji między wątkami lub między procesami nadrzędnymi i podrzędnymi, w których uchwyty potoku mogą być łatwo przesłane do procesu podrzędnego po jego utworzeniu.  
  
     W programie .NET można zaimplementować anonimowe potoki przy użyciu klas <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream>.  
  
     Zobacz [jak: korzystanie z anonimowych potoków do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
- Nazwane potoki.  
  
     Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku. Nazwane potoki mogą być jednokierunkowe lub dwustronne. Obsługują komunikację opartą na komunikatach i umożliwiają wielu klientom jednoczesne łączenie się z procesem serwera przy użyciu tej samej nazwy potoku. Nazwane potoki obsługują również personifikację, która umożliwia łączenie procesów w celu używania ich własnych uprawnień na serwerach zdalnych.  
  
     W programie .NET należy zaimplementować nazwane potoki przy użyciu klas <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream>.  
  
     Zobacz [jak: używanie nazwanych potoków do komunikacji międzyprocesowej sieci](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Zobacz także

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)
- [Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
