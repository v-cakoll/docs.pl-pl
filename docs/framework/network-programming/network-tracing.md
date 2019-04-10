---
title: Śledzenie sieci w .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework], network tracing
- methods, network tracing
- Networking
- trace enabled debugging
- network tracing, about network tracing
- network tracing
- network, network tracing
- traffic tracing
- tracing [.NET Framework], network
- deploying applications [.NET Framework], network traffic
- capturing network traffic
- Internet, network tracing
- Network Resources
- output, network tracing
- method invocations
ms.assetid: e993b7c3-087f-45d8-9c02-9dded936d804
ms.openlocfilehash: 45ec7b83824777c594b966a38d2b7fcd4f63b596
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221192"
---
# <a name="network-tracing-in-the-net-framework"></a>Śledzenie sieci w .NET Framework
Mechanizm śledzenia sieci w środowisku .NET Framework umożliwia dostęp do informacji o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację. Funkcja ułatwia debugowanie aplikacji na etapie ich tworzenia oraz analizowanie już wdrożonych aplikacji. Dane wyjściowe funkcji śledzenia sieci można adaptować, dostosowując je do różnych scenariuszy fazy programowania i środowiska produkcyjnego.  
  
 Aby włączyć śledzenie sieci w środowisku .NET Framework, należy wskazać miejsce docelowe danych wyjściowych funkcji oraz dodać jej ustawienia konfiguracyjne do pliku konfiguracyjnego aplikacji lub maszyny. Opisy plików konfiguracyjnych i sposób ich użycia można znaleźć [pliki konfiguracyjne](../../../docs/framework/configure-apps/index.md). Aby uzyskać informacje o włączaniu funkcji śledzenia sieci, zobacz [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md). Aby uzyskać informacje o ustawieniach, które należy dodać do pliku konfiguracji, zobacz [jak: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Gdy śledzenie jest włączone, można przechwycić informacje śledzenia generowane przez **przestrzeni nazw System.Net** klasy. Do składowych klasy sieciowej generujących dane ze śledzenia obowiązuje następująca uwaga zawarta w sekcji Uwaga w dokumentacji biblioteki klas środowiska NET Framework:  
  
> [!NOTE]
>  Ten element członkowski generuje informacje ze śledzenia pod warunkiem włączenia funkcji śledzenia sieci w aplikacji. Aby dowiedzieć się więcej, zobacz Śledzenie sieci.  
  
## <a name="see-also"></a>Zobacz także

- [Włączanie śledzenia sieci](../../../docs/framework/network-programming/enabling-network-tracing.md)
- [Instrukcje: konfigurowanie funkcji śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)
- [Interpretowanie śledzenia sieci](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
