---
title: Warunkowe operacje Get i Put
ms.date: 03/30/2017
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
ms.openlocfilehash: 29819f89327128cdd71cc89eb8d14126522dc2df
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324428"
---
# <a name="conditional-get-and-put"></a>Warunkowe operacje Get i Put
W tym przykładzie pokazano, jak nowe pobrać warunkowe i zaktualizuj interfejsów API modelu programowania REST programu WCF. Ponieważ pobranie warunkowe i aktualizacji są najbardziej odpowiednie dla korzystający z zasobów i rozszerza w tym przykładzie usług REST [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. Ten przykład koncentruje się na dodanie obsługi pobierania warunkowe i przeprowadź aktualizację do [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) przykładowy przy użyciu nowych interfejsów API, wprowadzona w [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstracje  
 Pobranie warunkowe i aktualizacji  
  
## <a name="discussion"></a>Dyskusja  
 Usługi WCF w tym przykładzie ujawnia zbiorze klientów w zorientowanej na zasób i sposób REST. Aby uzyskać szczegółowy opis implementacji usługi, zobacz [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki.  
  
 Ten przykład dodaje pobranie warunkowe i możliwości aktualizacji [podstawowej usługi do zasobu](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. Warunkowe pobierania i aktualizowania, użyj tagów jednostki HTTP i nagłówków HTTP If-None-Match i If-Match, aby sprawdzić, czy klienci mają lub nie masz najnowszej jednostki dla danego zasobu. Jednak implementacja kodu można poprawnie przeanalizować nagłówki HTTP If-None-Match i If-Match może być uciążliwe i podatne na błędy. W związku z tym <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> i <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody zostały dodane do <xref:System.ServiceModel.Web.IncomingWebRequestContext>, który jest możliwy przy użyciu bieżącego wystąpienia <xref:System.ServiceModel.Web.WebOperationContext>. Ponadto `SetETag` metoda została dodana do <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, ułatwiając zwróciła tagów prawidłową jednostkę.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda jest przeznaczona do użycia z operacjami [WebGet]. Trwa bieżącego tagu jednostki dla danego zasobu jako `entityTag` parametr, który może być `string`, `int`, `long` lub `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda sprawdza, czy tag jednostki względem nagłówek HTTP If-None-Match żądania. Jeśli tag jednostki znajduje się w nagłówku HTTP If-None-Match, a następnie <xref:System.ServiceModel.Web.WebFaultException> ze stanem jest generowany, kod nie zmodyfikowany (304); w przeciwnym razie metoda zwraca wartość. Mechanizm pobieranie warunkowego umożliwia klientowi przekazaniu do serwera, czy ma ona tej jednostki i jeśli klient nie ma już go wysłać tylko bieżąca jednostka. Przykład użycia elementu <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody są widoczne w `GetCustomer` i `GetCustomers` operacji usługi. Ważne jest, aby należy pamiętać, który wywołuje w celu <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> mogą nie zwracać. Deweloperzy powinny implementować operacji, więc, że żądanie jest już znany zakończy się powodzeniem przed wywołaniem do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> jest wykonywany, tak że jeśli wywołanie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> został nie istnieje, usługa wysyłane odpowiedzi z kodem stanu powodzenia.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda jest podobna do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody. Trwa bieżącego tagu jednostki dla danego zasobu. Jednak jest przeznaczona do użycia z operacjami [WebInvoke], w którym metoda jest równa "PUT" lub "DELETE". <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda sprawdza, czy tag jednostki względem nagłówek HTTP If-Match żądania. Jeśli tag jednostki nie znajduje się w nagłówku If-Match protokołu HTTP, a następnie <xref:System.ServiceModel.Web.WebFaultException> ze stanem generowany jest kod niepowodzenie warunku wstępnego (412). Mechanizm aktualizacji warunkowego umożliwia klientowi przekazaniu do serwera, czy ma ona tę jednostkę, dla zasobu i Zezwalaj tylko na klienta do zmiany zasobu. Jeśli jednostka ma jest aktualny. Przykład użycia elementu <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody są widoczne w `UpdateCustomer` i `DeleteCustomer` operacji usługi. Podobnie jak <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, ważne jest, aby należy pamiętać, który wywołuje w celu <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> mogą nie zwracać. Deweloperzy powinny implementować operacji w taki sposób, że żądanie jest już znany zakończy się powodzeniem przed wywołaniem do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> jest wykonywany, tak że jeśli wywołanie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nie istnieje, usługa będzie odpowiadać z kodem stanu powodzenia.  
  
 Przykład składa się z samodzielnie hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Po uruchomieniu aplikacji konsolowej klienta zgłasza żądania do usługi i zapisuje odpowiednie informacje z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykład  
  
1.  Otwórz rozwiązanie dla przykładu warunkowego Get i Put. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator, aby pomyślnie wykonać próbki. W tym celu kliknij prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikonę i wybierając pozycję **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B, Skompiluj rozwiązanie, a następnie naciśnij klawisz CTRL + F5, aby uruchomić projekt aplikacji konsoli. Jeśli do uruchomienia tego projektu z włączonym (naciskając klawisz F5, a nie CTRL + F5) debugowaniem, zatrzymanie debugera, gdy wyjątek jest generowany przez warunkowy GET i PUT, sprawdzanie. W takim przypadku, naciśnij klawisz F5, aby kontynuować wykonywanie próbki.  
  
3.  W oknie konsoli są wyświetlane piasku zawiera identyfikator URI uruchomioną usługę i identyfikator URI stronę pomocy HTML do uruchomionej usługi.  
  
4.  Po uruchomieniu przykładu klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli.  
  
5.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
