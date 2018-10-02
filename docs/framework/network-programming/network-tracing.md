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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 65bd172d184b1346000c2bc84cb888dfab28bb61
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459779"
---
# <a name="network-tracing-in-the-net-framework"></a>Śledzenie sieci w .NET Framework
Mechanizm śledzenia sieci w środowisku .NET Framework umożliwia dostęp do informacji o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację. Funkcja ułatwia debugowanie aplikacji na etapie ich tworzenia oraz analizowanie już wdrożonych aplikacji. Dane wyjściowe funkcji śledzenia sieci można adaptować, dostosowując je do różnych scenariuszy fazy programowania i środowiska produkcyjnego.  
  
 Aby włączyć śledzenie sieci w środowisku .NET Framework, należy wskazać miejsce docelowe danych wyjściowych funkcji oraz dodać jej ustawienia konfiguracyjne do pliku konfiguracyjnego aplikacji lub maszyny. Opisy plików konfiguracyjnych i sposób ich użycia można znaleźć [pliki konfiguracyjne](../../../docs/framework/configure-apps/index.md). Aby uzyskać informacje o włączaniu funkcji śledzenia sieci, zobacz [Enabling Network Tracing](../../../docs/framework/network-programming/enabling-network-tracing.md). Aby uzyskać informacje o ustawieniach, które należy dodać do pliku konfiguracji, zobacz [porady: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md).  
  
 Gdy śledzenie jest włączone, można przechwycić informacje śledzenia generowane przez **przestrzeni nazw System.Net** klasy. Do składowych klasy sieciowej generujących dane ze śledzenia obowiązuje następująca uwaga zawarta w sekcji Uwaga w dokumentacji biblioteki klas środowiska NET Framework:  
  
> [!NOTE]
>  Ten element członkowski generuje informacje ze śledzenia pod warunkiem włączenia funkcji śledzenia sieci w aplikacji. Aby dowiedzieć się więcej, zobacz Śledzenie sieci.  
  
## <a name="see-also"></a>Zobacz też  
 [Włączanie śledzenia sieci](../../../docs/framework/network-programming/enabling-network-tracing.md)  
 [Instrukcje: konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md)  
 [Interpretowanie śledzenia sieci](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Wprowadzenie do Instrumentacji i śledzenia](https://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
