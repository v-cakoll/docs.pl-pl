---
title: Interpretowanie śledzenia sieci
description: Dowiedz się, jak używać funkcji śledzenia do przechwytywania wywołań wysyłanych przez aplikację do różnych elementów członkowskich klasy System.Net w .NET Framework.
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 7a17e4ba14d8c5fe136667c4eb5bc5b2fd7a8242
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502369"
---
# <a name="interpreting-network-tracing"></a>Interpretowanie śledzenia sieci
Po włączeniu śledzenia sieci można użyć funkcji śledzenia do przechwytywania wywołań aplikacji do różnych <xref:System.Net> elementów członkowskich klasy. Dane wyjściowe tych wywołań mogą wyglądać podobnie jak w poniższych przykładach.  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 W poprzednim przykładzie [588] jest unikatowym identyfikatorem bieżącego wątku. (4357) i (4387) to sygnatury czasowe określające liczbę milisekund, które upłynęły od momentu uruchomienia aplikacji. Dane po znaczniku czasu pokazują aplikację wprowadzającą i opuszczają metodę **Socket. Send**. Obiekt wykonujący metodę **send** ma 33574638 jako unikatowy identyfikator. Ślad wyjścia metody zawiera wartość zwracaną (61 w poprzednim przykładzie).  
  
 Ślady sieci mogą przechwytywać ruch sieciowy, który jest wysyłany z lub odbierany przez aplikację przy użyciu protokołów na poziomie aplikacji, takich jak protokół HTTP (Hypertext Transfer Protocol). Te dane można przechwytywać jako tekst i, opcjonalnie, dane szesnastkowe. Dane szesnastkowe są dostępne po określeniu **includehex** jako wartości atrybutu **TraceMode** . (Aby uzyskać szczegółowe informacje na temat tego atrybutu, zobacz [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) Poniższy przykład śledzenia został wygenerowany przy użyciu **includehex**.  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 Aby pominąć dane szesnastkowe, określ **protocolonly** jako wartość atrybutu **TraceMode** . Poniższy przykład pokazuje ślad, gdy **protocolonly** jest określony.  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a>Zobacz także

- [Włączanie śledzenia sieci](enabling-network-tracing.md)
- [Instrukcje: konfigurowanie śledzenia sieci](how-to-configure-network-tracing.md)
- [Śledzenie sieci w .NET Framework](network-tracing.md)
