---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 032be700beaa38ed6c08ed1940aab558b2106591
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964480"
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
Ten przykład pokazuje integrację warstwy hostingu z klasami w <xref:System.Web.Routing> przestrzeni nazw. Klasy w <xref:System.Web.Routing> przestrzeni nazw umożliwiają aplikacji korzystanie z adresów URL, które nie są bezpośrednio zgodne z zasobem fizycznym. Użycie routingu sieci Web umożliwia deweloperom tworzenie adresów wirtualnych dla protokołu HTTP, które następnie są mapowane z powrotem do rzeczywistych usług WCF. Jest to przydatne w przypadku, gdy usługa WCF musi być hostowana bez konieczności fizycznego pliku lub zasobu, lub w przypadku uzyskiwania dostępu do usług za pomocą adresów URL, które nie zawierają plików takich jak. html czy. aspx. Ten przykład pokazuje, <xref:System.Web.Routing.RouteTable> jak używać klasy do tworzenia wirtualnych identyfikatorów URI, które mapują na uruchamianie usług zdefiniowanych w Global. asax. 

> [!NOTE]
> Klasy w <xref:System.Web.Routing> przestrzeni nazw działają tylko dla usług hostowanych za pośrednictwem protokołu HTTP.  
  
Ten przykład używa programu WCF do tworzenia dwóch źródeł danych RSS `movies` : źródła danych `channels` i źródła danych. Adresy URL do aktywowania usług nie zawierają rozszerzenia i są zarejestrowane w `Application_Start` metodzie `Global` klasy pochodzącej od <xref:System.Web.HttpApplication> klasy.  
  
> [!NOTE]
> Ten przykład działa tylko w Internet Information Services (IIS) 7,0 i nowszych, ponieważ usługi IIS 6,0 używają innej metody obsługi adresów URL bez rozszerzenia.  

#### <a name="to-download-this-sample"></a>Aby pobrać ten przykład
  
Ten przykład może już być zainstalowany na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Korzystając z programu Visual Studio, Otwórz plik WebRoutingIntegration. sln.  
  
2. Aby uruchomić rozwiązanie i uruchomić serwer Web Development, naciśnij klawisz F5.  
  
     Zostanie wyświetlona lista katalogów dla przykładu. Należy zauważyć, że nie ma plików z rozszerzeniem SVC.  
  
3. Na pasku adresu Dodaj `movies` do adresu URL, aby `http://localhost:[port]/movies` odczytywać i naciskać klawisz ENTER.  
  
     W przeglądarce pojawi się źródło filmów.  
  
4. Na pasku adresu Dodaj `channels` do adresu URL, więc jest to odczyt `http://localhost:[port]/channels` i naciśnięcie klawisza ENTER.  
  
     Kanał informacyjny kanału pojawia się w przeglądarce.  
  
5. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
     Jeśli serwer programistyczny nie został zakończony, kliknij prawym przyciskiem myszy ikonę obszaru powiadomień i wybierz polecenie **Zatrzymaj**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Aby użyć tego przykładu, gdy jest hostowany w usługach IIS  
  
1. Korzystając z programu Visual Studio, Otwórz plik WebRoutingIntegration. sln.  
  
2. Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.  
  
3. Utwórz aplikację sieci Web w Menedżerze Internet Information Services (IIS).  
  
    1. W Menedżerze usług IIS kliknij prawym przyciskiem myszy pozycję **Domyślna witryna sieci Web** i wybierz polecenie **Dodaj aplikację**.  
  
    2. Dla **aliasu**wpisz w `WebRoutingIntegration`.  
  
    3. W polu **Ścieżka fizyczna**wybierz folder usługi wewnątrz projektu.  
  
    4. Naciśnij klawisz **OK**.  
  
4. Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając pozycję **Zarządzaj aplikacją** , a następnie pozycję **Przeglądaj**.  
  
5. Na pasku adresu Dodaj `movies` do adresu URL, więc jest to odczyt `http://localhost:[port]/movies` i naciśnięcie klawisza ENTER.  
  
     W przeglądarce pojawi się źródło filmów.  
  
6. Na pasku adresu Dodaj `channels` do adresu URL, więc jest to odczyt `http://localhost:[port]/channels` i naciśnięcie klawisza ENTER.  
  
     Kanał informacyjny kanału pojawia się w przeglądarce.  
  
7. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
 Ten przykład pokazuje, że warstwa hostingu może tworzyć klasy w <xref:System.Web.Routing> przestrzeni nazw na potrzeby routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
> Domyślną wersję puli aplikacji należy zaktualizować do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] wersji 2.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
