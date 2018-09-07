---
title: Operacje potokowe w oprogramowaniu .NET Framework
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdc12091a377a118dc533e5f299fa4833af64baf
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44081872"
---
# <a name="pipe-operations-in-the-net-framework"></a>Operacje potokowe w oprogramowaniu .NET Framework
Potoki zapewniają środki do komunikacji międzyprocesowej. Istnieją dwa rodzaje potoków:  
  
-   Anonimowe potoki.  
  
     Anonimowe potoki zapewniają komunikację międzyprocesorową na komputerze lokalnym. Anonimowe potoki wymagają mniejsze obciążenie niż nazwane potoki, ale oferują ograniczonej liczbie usług. Anonimowe potoki są jednokierunkowe i nie można używać za pośrednictwem sieci. Obsługują tylko jeden serwer wystąpienie. Anonimowe potoki są przydatne do komunikacji między wątkami lub między procesami nadrzędnymi i podrzędnymi, gdzie uchwyty potoku mogą być łatwo przekazywane do procesu podrzędnego podczas jego tworzenia.  
  
     W .NET Framework, zaimplementować anonimowych potoków przy użyciu <xref:System.IO.Pipes.AnonymousPipeServerStream> i <xref:System.IO.Pipes.AnonymousPipeClientStream> klasy.  
  
     Zobacz [porady: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md).  
  
-   Nazwane potoki.  
  
     Nazwane potoki zapewniają komunikację międzyprocesorową pomiędzy serwerem potoku i jednym lub kilkoma klientami potoku. Nazwane potoki mogą być jednokierunkowe lub dwukierunkowego. One obsługi komunikacji typu oparta na komunikatach i umożliwić wielu klientów jednocześnie nawiązać proces serwera, korzystając z tej samej nazwy potoku. Nazwane potoki obsługują także personifikacji, która pozwala łączyć procesy z ich własnych uprawnień na serwerach zdalnych.  
  
     W .NET Framework, zaimplementować nazwane potoki przy użyciu <xref:System.IO.Pipes.NamedPipeServerStream> i <xref:System.IO.Pipes.NamedPipeClientStream> klasy.  
  
     Zobacz [porady: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md).  
  
## <a name="see-also"></a>Zobacz także

- [We/Wy plików i strumieni](../../../docs/standard/io/index.md)  
- [Instrukcje: stosowanie potoków anonimowych do lokalnej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-anonymous-pipes-for-local-interprocess-communication.md)  
- [Instrukcje: stosowanie potoków nazwanych do sieciowej komunikacji międzyprocesowej](../../../docs/standard/io/how-to-use-named-pipes-for-network-interprocess-communication.md)
