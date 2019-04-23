---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: f4f9772583bbd66d19cc59f453489965aabf74b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302247"
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
W tym przykładzie przedstawiono warstwy obsługi integracji z klas w <xref:System.Web.Routing> przestrzeni nazw. Klasy w <xref:System.Web.Routing> przestrzeni nazw Zezwalaj aplikacji na używanie adresów URL, które nie odpowiadają bezpośrednio zasób fizyczny. Przy użyciu routingu w sieci Web umożliwia deweloperom tworzenie wirtualnych adresów dla protokołu HTTP, które następnie są mapowane z powrotem na rzeczywiste usługi WCF. Jest to przydatne, gdy usługa WCF muszą być obsługiwane bez konieczności fizyczny plik lub zasób lub usług muszą być dostępne z adresami URL, które nie zawierają plików, takich jak HTML lub .aspx. W tym przykładzie pokazano, jak wykorzystywać <xref:System.Web.Routing.RouteTable> klasy w celu utworzenia identyfikatorów URI wirtualnych mapowane na uruchamianie usługi zdefiniowane w pliku global.asax. 

> [!NOTE]
>  Klasy w <xref:System.Web.Routing> przestrzeni nazw jest prawidłowe tylko dla usług hostowanych za pośrednictwem protokołu HTTP.  
  
W tym przykładzie użyto usługi WCF, aby utworzyć dwa źródła danych RSS: `movies` kanału informacyjnego i `channels` źródła danych. Adresy URL, aby aktywować usługi nie zawiera rozszerzenia i są zarejestrowane w usłudze `Application_Start` metody `Global` klasą pochodną <xref:System.Web.HttpApplication> klasy.  
  
> [!NOTE]
>  Ten przykład działa tylko w Internet informacji Services (IIS) 7.0 i nowsze, jako usług IIS 6.0 używa innej metody do obsługi adresów URL bez rozszerzenia.  

#### <a name="to-download-this-sample"></a>Aby pobrać w tym przykładzie
  
W tym przykładzie może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Za pomocą programu Visual Studio, otwórz plik WebRoutingIntegration.sln.  
  
2. Aby uruchomić rozwiązanie i uruchomić serwera wdrożeniowego sieci Web, naciśnij klawisz F5.  
  
     Pojawi się listę katalogów we próbki. Należy pamiętać, że nie istnieją żadne pliki z rozszerzeniem nazwy pliku .svc.  
  
3. Na pasku adresu Dodaj `movies` do adresu URL, tak że odczytuje `http://localhost:[port]/movies` i naciśnij klawisz ENTER.  
  
     Kanał informacyjny filmy zostanie wyświetlona w przeglądarce.  
  
4. Na pasku adresu Dodaj `channels` do adresu URL, więc to odczyty `http://localhost:[port]/channels` i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
5. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
     Jeśli nie zakończył serwera wdrożeniowego programu, kliknij prawym przyciskiem myszy ikonę w obszarze powiadomień, a następnie wybierz **zatrzymać**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Aby użyć tego przykładu, w przypadku hostowania w usługach IIS  
  
1. Za pomocą programu Visual Studio, otwórz plik WebRoutingIntegration.sln.  
  
2. Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.  
  
3. Utwórz aplikację sieci Web w Menedżerze usług Internet Information Services (IIS).  
  
    1.  Kliknij prawym przyciskiem myszy w Menedżerze usług IIS **domyślna witryna sieci Web** i wybierz **Dodawanie aplikacji**.  
  
    2.  Aby uzyskać **alias**, wpisz `WebRoutingIntegration`.  
  
    3.  Aby uzyskać **ścieżkę fizyczną**, wybierz folder usługi w projekcie.  
  
    4.  Naciśnij klawisz **OK**.  
  
4. Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając polecenie **Zarządzanie aplikacją** i następnie **Przeglądaj**.  
  
5. Na pasku adresu Dodaj `movies` do adresu URL, więc to odczyty `http://localhost:[port]/movies` i naciśnij klawisz ENTER.  
  
     Kanał informacyjny filmy zostanie wyświetlona w przeglądarce.  
  
6. Na pasku adresu Dodaj `channels` do adresu URL, więc to odczyty `http://localhost:[port]/channels` i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
7. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
 Niniejszy przykład pokazuje, w warstwie hostingu jest w stanie tworzenie z klasami <xref:System.Web.Routing> przestrzeni nazw w przypadku routingu żądań usług obsługiwanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
>  Należy zaktualizować wersję puli aplikacji domyślnej, aby [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Jeśli jest ustawiony do wersji 2.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady trwałości i hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
