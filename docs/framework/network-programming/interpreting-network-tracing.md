---
title: Interpretowanie śledzenia sieci
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 8813bf68ee2b354ed7fc5e981904b8e4b807c1be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576528"
---
# <a name="interpreting-network-tracing"></a>Interpretowanie śledzenia sieci
Po włączeniu funkcji śledzenia sieci umożliwia śledzenie przechwytywania wywołania aplikacji sprawia, że do różnych <xref:System.Net> składowych klasy. Dane wyjściowe z tych wywołań może być podobne do poniższych przykładach.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 W powyższym przykładzie [588] to unikatowy identyfikator bieżącego wątku. (4357) i (4387) są sygnatury czasowe oznaczający liczbę milisekund, które upłynęły od czasu uruchomienia aplikacji. Dane zgodnie z sygnaturą czasową przedstawiono aplikację i wychodzą z metody **Socket.Send**. Wykonywanie obiektu **wysyłania** metoda ma 33574638 jako unikatowego identyfikatora. Śledzenia zakończenia metody zawiera wartość zwracaną (61 w powyższym przykładzie).  
  
 Danych śledzenia sieci można przechwytywać ruch sieciowy, który jest wysłanych lub odebranych przez aplikację za pomocą protokoły poziomu aplikacji, takich jak protokół HTTP (Hypertext Transfer). Te dane mogą być przechwytywane jako tekst i, opcjonalnie, dane szesnastkowe. Dane szesnastkowe jest dostępna po określeniu **includehex** jako wartość **tryb_śledzenia** atrybutu. (Aby uzyskać szczegółowe informacje dotyczące tego atrybutu, zobacz [jak: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Poniższy przykład śledzenia został wygenerowany za pomocą **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Aby pominąć szesnastkowe dane, należy określić **protocolonly** jako wartość pozycji **tryb_śledzenia** atrybutu. W poniższym przykładzie pokazano śledzenia podczas **protocolonly** jest określony.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Zobacz także
- [Włączanie śledzenia sieci](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Instrukcje: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Śledzenie sieci w programie .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
