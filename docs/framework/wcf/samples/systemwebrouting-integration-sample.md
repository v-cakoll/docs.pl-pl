---
title: Przykład integracji elementu SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 8be76fa97752680700f1c0eb56c1803fc69155d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716632"
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
Ten przykład pokazuje integrację warstwy hostingu z klasami w przestrzeni nazw <xref:System.Web.Routing>. Klasy w przestrzeni nazw <xref:System.Web.Routing> umożliwiają aplikacji korzystanie z adresów URL, które nie są bezpośrednio zgodne z zasobem fizycznym. Użycie routingu sieci Web umożliwia deweloperom tworzenie adresów wirtualnych dla protokołu HTTP, które następnie są mapowane z powrotem do rzeczywistych usług WCF. Jest to przydatne w przypadku, gdy usługa WCF musi być hostowana bez konieczności fizycznego pliku lub zasobu, lub w przypadku uzyskiwania dostępu do usług za pomocą adresów URL, które nie zawierają plików takich jak. html czy. aspx. Ten przykład pokazuje, jak używać klasy <xref:System.Web.Routing.RouteTable> do tworzenia wirtualnych identyfikatorów URI, które mapują na uruchamianie usług zdefiniowanych w Global. asax. 

> [!NOTE]
> Klasy w przestrzeni nazw <xref:System.Web.Routing> działają tylko dla usług hostowanych za pośrednictwem protokołu HTTP.  
  
Ten przykład używa programu WCF do tworzenia dwóch źródeł danych RSS: źródła `movies` i źródła `channels`. Adresy URL do aktywowania usług nie zawierają rozszerzenia i są rejestrowane w metodzie `Application_Start` klasy `Global` pochodzącej od klasy <xref:System.Web.HttpApplication>.  
  
> [!NOTE]
> Ten przykład działa tylko w Internet Information Services (IIS) 7,0 i nowszych, ponieważ usługi IIS 6,0 używają innej metody obsługi adresów URL bez rozszerzenia.  

#### <a name="to-download-this-sample"></a>Aby pobrać ten przykład
  
Ten przykład może już być zainstalowany na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1. Korzystając z programu Visual Studio, Otwórz plik WebRoutingIntegration. sln.  
  
2. Aby uruchomić rozwiązanie i uruchomić serwer Web Development, naciśnij klawisz F5.  
  
     Zostanie wyświetlona lista katalogów dla przykładu. Należy zauważyć, że nie ma plików z rozszerzeniem SVC.  
  
3. Na pasku adresu Dodaj `movies` do adresu URL, tak aby był odczytywany `http://localhost:[port]/movies` i naciśnij klawisz ENTER.  
  
     W przeglądarce pojawi się źródło filmów.  
  
4. Na pasku adresu Dodaj `channels` do adresu URL, a więc odczytuje `http://localhost:[port]/channels` i naciśnij klawisz ENTER.  
  
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
  
    4. Naciśnij przycisk **OK**.  
  
4. Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając pozycję **Zarządzaj aplikacją** , a następnie pozycję **Przeglądaj**.  
  
5. Na pasku adresu Dodaj `movies` do adresu URL, a więc odczytuje `http://localhost:[port]/movies` i naciśnij klawisz ENTER.  
  
     W przeglądarce pojawi się źródło filmów.  
  
6. Na pasku adresu Dodaj `channels` do adresu URL, a więc odczytuje `http://localhost:[port]/channels` i naciśnij klawisz ENTER.  
  
     Kanał informacyjny kanału pojawia się w przeglądarce.  
  
7. Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
 Ten przykład pokazuje, że warstwa hostingu jest w stanie tworzyć klasy w przestrzeni nazw <xref:System.Web.Routing> na potrzeby routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
> Domyślną wersję puli aplikacji należy zaktualizować do .NET Framework 4, jeśli jest ona ustawiona na wersję 2.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady hostingu i trwałości usługi AppFabric](https://go.microsoft.com/fwlink/?LinkId=193961)
