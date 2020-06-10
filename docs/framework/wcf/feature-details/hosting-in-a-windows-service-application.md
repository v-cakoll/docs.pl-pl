---
title: Hostowanie w aplikacji usługi systemu Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: ba49d123508ceb8da677d1e9c67721e4f86aa7c3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597335"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostowanie w aplikacji usługi systemu Windows
Usługi systemu Windows (znane wcześniej jako usługi systemu Windows NT) oferują model procesu szczególnie odpowiedni dla aplikacji, które muszą się znajdować w długim, uruchomionym pliku wykonywalnym i nie mogą wyświetlać żadnych form interfejsu użytkownika. Okres istnienia aplikacji usługi systemu Windows jest zarządzany przez menedżera kontroli usług (SCM), który pozwala uruchamiać, zatrzymywać i wstrzymywać aplikacje usług systemu Windows. Proces usługi systemu Windows można skonfigurować do automatycznego uruchamiania podczas uruchamiania komputera, co sprawia, że jest to odpowiednie środowisko hostingu dla aplikacji "zawsze włączone". Aby uzyskać więcej informacji o aplikacjach usług systemu Windows, zobacz [aplikacje usług systemu Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikacje, które obsługują długotrwałe usługi Windows Communication Foundation (WCF), współdzielą wiele cech z usługami systemu Windows. W szczególności usługi WCF są długotrwałymi plikami wykonywalnymi serwera, które nie współdziałają bezpośrednio z użytkownikiem i w związku z tym nie implementują żadnej formy interfejsu użytkownika. W związku z tym hosting usług WCF w ramach aplikacji usługi systemu Windows to jedna z opcji tworzenia niezawodnych, długotrwałych aplikacji WCF.  
  
 Często deweloperzy programu WCF muszą zdecydować, czy hostować swoją aplikację WCF w ramach aplikacji usługi systemu Windows, czy w ramach środowiska usług Internet Information Services (IIS) czy usługi aktywacji procesów systemu Windows (WAS). Należy rozważyć użycie aplikacji usługi systemu Windows w następujących warunkach:  
  
- Aplikacja wymaga jawnej aktywacji. Na przykład należy używać usług systemu Windows, gdy aplikacja musi być uruchamiana automatycznie podczas uruchamiania serwera, zamiast uruchamiania dynamicznego w odpowiedzi na pierwszy komunikat przychodzący.  
  
- Proces hostujący aplikację musi pozostać uruchomiony po uruchomieniu. Po uruchomieniu proces usługi systemu Windows pozostaje uruchomiony, chyba że zostanie jawnie zamknięty przez administratora serwera przy użyciu Menedżera kontroli usług. Aplikacje hostowane w usługach IIS lub mogły zostać uruchomione i dynamicznie zatrzymane w celu optymalnego wykorzystania zasobów systemowych. Aplikacje, które wymagają jawnej kontroli nad okresem istnienia procesu hostingu, powinny używać usług systemu Windows zamiast usług IIS lub WAS.  
  
- Usługa WCF musi działać w systemie Windows Server 2003 i używać transportów innych niż HTTP. W systemie Windows Server 2003 środowisko hostingu usług IIS 6,0 jest ograniczone tylko do komunikacji HTTP. Aplikacje usług systemu Windows nie podlegają temu ograniczeniu i mogą korzystać z dowolnego obsługiwanego przez transport WCF, w tym net. TCP, net. pipe i net. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Aby hostować WCF w aplikacji usługi systemu Windows  
  
1. Utwórz aplikację usługi systemu Windows. Można napisać aplikacje usług systemu Windows w zarządzanym kodzie przy użyciu klas w <xref:System.ServiceProcess> przestrzeni nazw. Ta aplikacja musi zawierać jedną klasę, która dziedziczy z <xref:System.ServiceProcess.ServiceBase> .  
  
2. Połącz okres istnienia usług WCF w okresie istnienia aplikacji usługi systemu Windows. Zazwyczaj usługi WCF hostowane w aplikacji usługi systemu Windows stają się aktywne po uruchomieniu usługi hostingu, przerywają nasłuchiwanie komunikatów, gdy usługa hostingu jest zatrzymana, i zamyka proces hostingu, gdy usługa WCF napotka błąd. Można to zrobić w następujący sposób:  
  
    - Przesłoń <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> , aby otworzyć co najmniej jedno wystąpienie elementu <xref:System.ServiceModel.ServiceHost> . Pojedyncza aplikacja usługi systemu Windows może obsługiwać wiele usług WCF, które są uruchamiane i zatrzymywane jako Grupa.  
  
    - Przesłoń, <xref:System.ServiceProcess.ServiceBase.OnStop%2A> Aby wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Closed> <xref:System.ServiceModel.ServiceHost> wszystkie uruchomione usługi WCF, które zostały uruchomione w czasie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> .  
  
    - Zasubskrybuj <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> zdarzenie <xref:System.ServiceModel.ServiceHost> i Użyj <xref:System.ServiceProcess.ServiceController> klasy, aby zamknąć aplikację usługi systemu Windows w przypadku błędu.  
  
     Aplikacje usług systemu Windows obsługujące usługi WCF są wdrażane i zarządzane w taki sam sposób, jak aplikacje usług systemu Windows, które nie korzystają z programu WCF.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceProcess>
- [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Host usług systemu Windows](../samples/windows-service-host.md)
- [Architektura programowania aplikacji usług](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
