---
title: HttpListener
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP
ms.assetid: 5b89d3fb-3c9a-49e2-af1f-c34c020c68ac
ms.openlocfilehash: d3fecb9fe78ca54f68d3c5a97dae5d5dd9fbb28d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642376"
---
# <a name="httplistener"></a>HttpListener
<xref:System.Net.HttpListener> Klasa udostępnia programowo kontrolowanego odbiornika protokołu HTTP. Odbiornik jest aktywna przez okres istnienia <xref:System.Net.HttpListener> obiektu i jest uruchamiana w ramach aplikacji.  
  
## <a name="httpsys"></a>HTTP.SYS  
 <xref:System.Net.HttpListener> Klasy są wbudowane HTTP.sys, czyli odbiornik trybu jądra, który obsługuje cały ruch HTTP dla Windows. Sterownik HTTP.sys zapewnia zarządzanie połączeniami, ograniczenie przepustowości i rejestrowanie serwera sieci Web. Użyj `HttpCfg.exe` narzędzie, aby dodać certyfikaty SSL. Aby uzyskać więcej informacji, zobacz dokumentację na [HttpCfg.exe](https://go.microsoft.com/fwlink/?LinkID=178284) narzędzia w [serwera](https://go.microsoft.com/fwlink/?LinkID=178285) dokumentacji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpWebRequest>
- <xref:System.Net.HttpWebResponse>
- [HTTP Server](https://go.microsoft.com/fwlink/?LinkID=178285)
- [Usprawnienia zabezpieczeń w IIS](https://go.microsoft.com/fwlink/?LinkID=178286)
- [Przykład aplikacji hosta HttpListener ASPX](https://go.microsoft.com/fwlink/?LinkID=179560)
- [Przykład technologii HttpListener](https://go.microsoft.com/fwlink/?LinkID=179558)
- [Przykłady programowania sieciowego](../../../docs/framework/network-programming/network-programming-samples.md)
