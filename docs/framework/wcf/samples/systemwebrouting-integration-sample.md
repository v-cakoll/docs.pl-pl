---
title: "Przykład integracji elementu SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c38c7af4988e6e47ee307f5cd7a8b6733b043a7c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
W tym przykładzie pokazano integracji hostingu warstwy z klas w <xref:System.Web.Routing> przestrzeni nazw. Klasy w <xref:System.Web.Routing> przestrzeni nazw Zezwalaj aplikacji na używanie adresów URL, które nie odpowiadają bezpośrednio zasób fizyczny. Przy użyciu routingu w sieci Web umożliwia deweloperom tworzenie wirtualnych adresów dla protokołu HTTP, które następnie są mapowane do rzeczywistego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług. Jest to przydatne, gdy usługa WCF musi być obsługiwana bez konieczności fizycznej plik lub zasób, lub gdy usług muszą być dostępne z adresami URL, które nie zawierają plików, takich jak HTML lub aspx. W tym przykładzie pokazano, jak korzystać z <xref:System.Web.Routing.RouteTable> klasy w celu utworzenia wirtualnego identyfikatorów URI mapowane na uruchamianie usług zdefiniowane w pliku global.asax. Na przykład istnieją dwa źródła danych RSS utworzone przy użyciu programu WCF: `movies` źródła danych i `channels` źródła danych. Adresy URL do aktywowania usługi nie zawiera rozszerzenia i są rejestrowane w `Application_Start` metody `Global` klasą pochodną <xref:System.Web.HttpApplication.Application_Start> klasy.  
  
> [!NOTE]
>  Klasy w <xref:System.Web.Routing> przestrzeni nazw jest prawidłowe tylko dla usługi hostowanej za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
>  W tym przykładzie działa tylko [!INCLUDE[iisver](../../../../includes/iisver-md.md)], jako [!INCLUDE[iis60](../../../../includes/iis60-md.md)] używa innej metody do obsługi adresów URL bez rozszerzeń.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik WebRoutingIntegration.sln.  
  
2.  Aby uruchomić rozwiązanie i uruchomić serwera wdrożeniowego sieci Web, naciśnij klawisz F5.  
  
     Zostanie wyświetlone listę przykładowej katalogów. Należy pamiętać, że nie ma żadnych plików z rozszerzeniem nazwy pliku svc.  
  
3.  Na pasku adresu dodać `movies` do adresu URL, więc to odczyty http://localhost: [portu] / filmy i naciśnij klawisz ENTER.  
  
     Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.  
  
4.  Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
5.  Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
     Jeśli nie zakończył serwera wdrożeniowego programu, kliknij prawym przyciskiem myszy ikonę w obszarze powiadomień i wybierz **zatrzymać**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Aby użyć tego przykładu, podczas udostępniania w usługach IIS  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik WebRoutingIntegration.sln.  
  
2.  Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Utwórz aplikację sieci Web w programie Internet Information Services (IIS) Manager.  
  
    1.  W Menedżerze usług IIS kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Dodawanie aplikacji**.  
  
    2.  Aby uzyskać **alias**, wpisz w `WebRoutingIntegration`.  
  
    3.  Aby uzyskać **ścieżka fizyczna**, wybierz folder usługi wewnątrz projektu.  
  
    4.  Press **OK**.  
  
4.  Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając polecenie **aplikacji Zarządzanie** , a następnie **Przeglądaj**.  
  
5.  Na pasku adresu dodać `movies` do adresu URL, więc to odczyty http://localhost: [portu] / filmy i naciśnij klawisz ENTER.  
  
     Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.  
  
6.  Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
7.  Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
 W przykładzie pokazano warstwy obsługi jest w stanie składających się z klas w <xref:System.Web.Routing> przestrzeń nazw dla routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
>  Zaktualizuj domyślnej wersji puli aplikacji do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Jeśli ustawiono w wersji 2.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
