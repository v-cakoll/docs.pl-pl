---
title: Hostowanie w aplikacji usługi systemu Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: a07aade4619b644dadd1d5acdcb5252b305b94d0
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964487"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostowanie w aplikacji usługi systemu Windows
Usługi systemu Windows (znane wcześniej jako usługi systemu Windows NT) oferują model procesu szczególnie odpowiedni dla aplikacji, które muszą się znajdować w długim, uruchomionym pliku wykonywalnym i nie mogą wyświetlać żadnych form interfejsu użytkownika. Okres istnienia aplikacji usługi systemu Windows jest zarządzany przez menedżera kontroli usług (SCM), który pozwala uruchamiać, zatrzymywać i wstrzymywać aplikacje usług systemu Windows. Proces usługi systemu Windows można skonfigurować do automatycznego uruchamiania podczas uruchamiania komputera, co sprawia, że jest to odpowiednie środowisko hostingu dla aplikacji "zawsze włączone". Aby uzyskać więcej informacji o aplikacjach usług systemu Windows, zobacz [aplikacje usług systemu Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikacje, które obsługują długotrwałe usługi Windows Communication Foundation (WCF), współdzielą wiele cech z usługami systemu Windows. W szczególności usługi WCF są długotrwałymi plikami wykonywalnymi serwera, które nie współdziałają bezpośrednio z użytkownikiem i w związku z tym nie implementują żadnej formy interfejsu użytkownika. W związku z tym hosting usług WCF w ramach aplikacji usługi systemu Windows to jedna z opcji tworzenia niezawodnych, długotrwałych aplikacji WCF.  
  
 Często deweloperzy programu WCF muszą zdecydować, czy hostować swoją aplikację WCF w ramach aplikacji usługi systemu Windows, czy w ramach środowiska usług Internet Information Services (IIS) czy usługi aktywacji procesów systemu Windows (WAS). Należy rozważyć użycie aplikacji usługi systemu Windows w następujących warunkach:  
  
- Aplikacja wymaga jawnej aktywacji. Na przykład należy używać usług systemu Windows, gdy aplikacja musi być uruchamiana automatycznie podczas uruchamiania serwera, zamiast uruchamiania dynamicznego w odpowiedzi na pierwszy komunikat przychodzący.  
  
- Proces hostujący aplikację musi pozostać uruchomiony po uruchomieniu. Po uruchomieniu proces usługi systemu Windows pozostaje uruchomiony, chyba że zostanie jawnie zamknięty przez administratora serwera przy użyciu Menedżera kontroli usług. Aplikacje hostowane w usługach IIS lub mogły zostać uruchomione i dynamicznie zatrzymane w celu optymalnego wykorzystania zasobów systemowych. Aplikacje, które wymagają jawnej kontroli nad okresem istnienia procesu hostingu, powinny używać usług systemu Windows zamiast usług IIS lub WAS.  
  
- Usługa WCF musi działać w systemie Windows Server 2003 i używać transportów innych niż HTTP. W systemie Windows Server 2003 środowisko hostingu usług IIS 6,0 jest ograniczone tylko do komunikacji HTTP. Aplikacje usług systemu Windows nie podlegają temu ograniczeniu i mogą korzystać z dowolnego obsługiwanego przez transport WCF, w tym net. TCP, net. pipe i net. MSMQ.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Aby hostować WCF w aplikacji usługi systemu Windows  
  
1. Utwórz aplikację usługi systemu Windows. Można napisać aplikacje usług systemu Windows w zarządzanym kodzie przy użyciu klas w przestrzeni nazw <xref:System.ServiceProcess>. Ta aplikacja musi zawierać jedną klasę, która dziedziczy po <xref:System.ServiceProcess.ServiceBase>.  
  
2. Połącz okres istnienia usług WCF w okresie istnienia aplikacji usługi systemu Windows. Zazwyczaj usługi WCF hostowane w aplikacji usługi systemu Windows stają się aktywne po uruchomieniu usługi hostingu, przerywają nasłuchiwanie komunikatów, gdy usługa hostingu jest zatrzymana, i zamyka proces hostingu, gdy usługa WCF napotka błąd. Można to zrobić w następujący sposób:  
  
    - Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, aby otworzyć co najmniej jedno wystąpienie <xref:System.ServiceModel.ServiceHost>. Pojedyncza aplikacja usługi systemu Windows może obsługiwać wiele usług WCF, które są uruchamiane i zatrzymywane jako Grupa.  
  
    - Przesłoń <xref:System.ServiceProcess.ServiceBase.OnStop%2A>, aby wywołać <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> wszystkich uruchomionych usług WCF, które zostały uruchomione w <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    - Zasubskrybuj zdarzenie <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> <xref:System.ServiceModel.ServiceHost> i użyj klasy <xref:System.ServiceProcess.ServiceController>, aby zamknąć aplikację usługi systemu Windows w przypadku błędu.  
  
     Aplikacje usług systemu Windows obsługujące usługi WCF są wdrażane i zarządzane w taki sam sposób, jak aplikacje usług systemu Windows, które nie korzystają z programu WCF.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceProcess>
- [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](https://go.microsoft.com/fwlink/?LinkId=94875)
- [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Host usług systemu Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)
- [Architektura programowania aplikacji usług](https://go.microsoft.com/fwlink/?LinkId=94876)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
