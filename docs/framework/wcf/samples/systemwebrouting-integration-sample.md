---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143957"
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
W tym przykładzie pokazano integracji warstwy <xref:System.Web.Routing> hostingu z klasami w obszarze nazw. Klasy w <xref:System.Web.Routing> obszarze nazw umożliwiają aplikacji używanie adresów URL, które nie odpowiadają bezpośrednio zasobowi fizycznemu. Za pomocą routingu sieci Web umożliwia deweloperowi tworzenie adresów wirtualnych dla protokołu HTTP, które są następnie mapowane z powrotem do rzeczywistych usług WCF. Jest to przydatne, gdy usługa WCF musi być hostowana bez konieczności fizycznego pliku lub zasobu lub gdy usługi muszą być dostępne za pomocą adresów URL, które nie zawierają plików, takich jak .html lub .aspx. W tym przykładzie pokazano, <xref:System.Web.Routing.RouteTable> jak korzystać z klasy do tworzenia wirtualnych identyfikatorów URI, które mapują do uruchomionych usług zdefiniowanych w global.asax.

> [!NOTE]
> Klasy w <xref:System.Web.Routing> obszarze nazw działają tylko dla usług obsługiwanych za pośrednictwem protokołu HTTP.  
  
W tym przykładzie użyto WCF do utworzenia dwóch źródeł danych RSS: paszy `movies` i `channels` pliku danych. Adresy URL, aby aktywować usługi nie zawierają `Application_Start` rozszerzenia i `Global` są zarejestrowane <xref:System.Web.HttpApplication> w metodzie klasy pochodzące z klasy.  
  
> [!NOTE]
> Ten przykład działa tylko w internetowych usługach informacyjnych (IIS) 7.0 i nowszych, ponieważ usługi IIS 6.0 używają innej metody obsługi adresów URL bez rozszerzenia.  

#### <a name="to-download-this-sample"></a>Aby pobrać ten przykład
  
Ten przykład może być już zainstalowany na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  

`<InstallDrive>:\WF_WCF_Samples`  

 Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tej próbki  
  
1. Za pomocą programu Visual Studio otwórz plik WebRoutingIntegration.sln.  
  
2. Aby uruchomić rozwiązanie i uruchomić serwer programistyczny sieci Web, naciśnij klawisz F5.  
  
     Pojawi się lista katalogów dla próbki. Należy zauważyć, że nie ma żadnych plików z rozszerzeniem pliku .svc.  
  
3. Na pasku adresu `movies` dodaj go do adresu `http://localhost:[port]/movies` URL, aby odczytywać i naciskać klawisz ENTER.  
  
     Kanał filmów pojawi się w przeglądarce.  
  
4. Na pasku adresu `channels` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/channels` i nacisnąć klawisz ENTER.  
  
     Kanał kanałowy pojawi się w przeglądarce.  
  
5. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT+F4.  
  
     Jeśli serwer deweloperów nie został przerwany, kliknij prawym przyciskiem myszy ikonę obszaru powiadomień i wybierz pozycję **Zatrzymaj**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Aby użyć tego przykładu hostowanego w użyczonych w u.  
  
1. Za pomocą programu Visual Studio otwórz plik WebRoutingIntegration.sln.  
  
2. Tworzenie projektu, naciskając klawisze CTRL+SHIFT+B.  
  
3. Tworzenie aplikacji sieci Web w Menedżerze internetowych usług informacyjnych (IIS).  
  
    1. W Menedżerze usług IIS kliknij prawym przyciskiem myszy **domyślną witrynę sieci Web** i wybierz **polecenie Dodaj aplikację**.  
  
    2. Dla **aliasu**wpisz `WebRoutingIntegration`.  
  
    3. W przypadku **ścieżki fizycznej**wybierz folder Usługa wewnątrz projektu.  
  
    4. Naciśnij przycisk **OK**.  
  
4. Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając pozycję **Zarządzaj aplikacją,** a następnie **przeglądaj**.  
  
5. Na pasku adresu `movies` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/movies` i nacisnąć klawisz ENTER.  
  
     Kanał filmów pojawi się w przeglądarce.  
  
6. Na pasku adresu `channels` dodaj do adresu URL, aby był odczytywany `http://localhost:[port]/channels` i nacisnąć klawisz ENTER.  
  
     Kanał kanałowy pojawi się w przeglądarce.  
  
7. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT+F4.  
  
 W tym przykładzie pokazano, że warstwa hostingu jest <xref:System.Web.Routing> w stanie komponować z klasami w obszarze nazw do routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
> Należy zaktualizować domyślną wersję puli aplikacji do programu .NET Framework 4, jeśli jest ustawiona na wersję 2.  
  
## <a name="see-also"></a>Zobacz też

- [AppFabric Hosting i trwałość przykłady](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
