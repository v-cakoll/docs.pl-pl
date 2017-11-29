---
title: "Interpretowanie Śledzenie sieci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: deb191f18bda5b00ef4a967f50e8e983289882a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="interpreting-network-tracing"></a>Interpretowanie Śledzenie sieci
Gdy włączone jest śledzenie sieci, umożliwia śledzenie przechwytywania wywołania aplikacji sprawia, że do różnych <xref:System.Net> klasy elementów członkowskich. Dane wyjściowe z tych wywołań może być podobne do poniższych przykładach.  
  
```  
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61  
```  
  
 W powyższym przykładzie [588] jest unikatowy identyfikator bieżącego wątku. (4357) i (4387) są sygnatury czasowe oznaczający liczbę milisekund, które upłynęły od czasu uruchomienia aplikacji. Dane sygnatury czasowej przedstawiono aplikację wprowadzanie i zamykanie metody **Socket.Send**. Wykonywanie obiektu **wysyłania** metoda ma 33574638 jako unikatowy identyfikator. Exit — metoda uwzględniono wartości zwracanej (61 w poprzednim przykładzie).  
  
 Śladów sieciowych można przechwytywać ruch sieciowy, który jest wysyłany z lub odebranych przez aplikację przy użyciu protokołów na poziomie aplikacji takich jak protokół HTTP (Hypertext Transfer). Te dane, można przechwycić jako tekst i, opcjonalnie, dane szesnastkowe. Szesnastkowe dane są dostępne, określając **includehex** jako wartość **tryb_śledzenia** atrybutu. (Aby uzyskać szczegółowe informacje dotyczące tego atrybutu, zobacz [porady: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).) Następujący przykład śledzenia został wygenerowany za pomocą **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Aby pominąć danych szesnastkowych, określ **protocolonly** jako wartość **tryb_śledzenia** atrybutu. W poniższym przykładzie przedstawiono śledzenia podczas **protocolonly** jest określona.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Zobacz też  
 [Włączanie śledzenia sieci](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Porady: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Śledzenie sieci w programie .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
