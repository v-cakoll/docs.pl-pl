---
title: Warunkowe operacje Get i Put
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e4ab4d0a97cbbaa2e5aaee25e0154e1cc94a82f8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="conditional-get-and-put"></a>Warunkowe operacje Get i Put
W tym przykładzie pokazano, jak nowy pobrać warunkowe i zaktualizować interfejsów API REST usługi WCF modelu programowania. Ponieważ warunkowego pobrania i aktualizacji są najbardziej odpowiednie dla zorientowane na zasobu i rozszerzenia tego przykładu usług REST, [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. W tym przykładzie koncentruje się na obsługę warunkowego pobierania i zaktualizuj go do [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbkowania przy użyciu nowych interfejsów API, wprowadzone w systemie [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstracje  
 Warunkowe pobrania i aktualizacji  
  
## <a name="discussion"></a>Omówienie  
 Usługi WCF w tym przykładzie udostępnia kolekcję klientów w realizacji konkretnych zasobów i sposób REST. Aby uzyskać szczegółowy opis implementacji usługi, zobacz [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki.  
  
 W tym przykładzie dodaje warunkowego pobieranie oraz możliwości aktualizacji [podstawowej usługi zasobów](../../../../docs/framework/wcf/samples/basic-resource-service.md) próbki. Warunkowe pobierania i aktualizowania Użyj tagów jednostki HTTP i nagłówków HTTP If-None-Match i If-Match, aby sprawdzanie, czy klienci mają lub nie masz najnowszej jednostki dla danego zasobu. Jednak wdrażania kodu można poprawnie przeanalizować nagłówków HTTP If-None-Match i If-Match może być niewygodny i podatne na błędy. W związku z tym <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> i <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody zostały dodane do <xref:System.ServiceModel.Web.IncomingWebRequestContext>, którego można uzyskać dostęp za pomocą bieżące wystąpienie klasy <xref:System.ServiceModel.Web.WebOperationContext>. Ponadto `SetETag` metody został dodany do <xref:System.ServiceModel.Web.OutgoingWebRequestContext>, ułatwiając zwracać prawidłową jednostkę tagów.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda jest przeznaczona do użycia z operacjami [WebGet]. Trwa bieżący tag jednostki dla danego zasobu jako `entityTag` parametr, który może być `string`, `int`, `long` lub `Guid`. <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> Metoda sprawdza tag jednostki przed nagłówka HTTP If-None-Match żądania. Jeśli tag jednostki znajduje się w nagłówku HTTP If-None-Match, a następnie <xref:System.ServiceModel.Web.WebFaultException> ze stanem jest generowany kod niezmodyfikowane (304); w przeciwnym razie metoda zwraca. Mechanizm warunkowego pobrać umożliwia klientowi przekazaniu do serwera, czy ma ona tej jednostki i jeśli klient nie ma jeszcze go wysłać tylko bieżącego obiektu. Przykład użycia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody są widoczne w `GetCustomer` i `GetCustomers` operacje usługi. Należy pamiętać, który odwołuje się do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> nie może zwracać. Deweloperzy powinny implementować operacji, dzięki czemu żądanie jest już znana się powodzeniem przed wywołaniem do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> wykonane, na przykład jeśli wywołanie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> został nie istnieje, usługa są wysyłane odpowiedzi z kodem stanu powiodło się.  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda jest podobna do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody. Trwa bieżący tag jednostki dla danego zasobu. Jednak jest ona przeznaczona do użycia z operacjami [WebInvoke], w których jest ustawiona metoda "PUT" lub "DELETE". <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> Metoda sprawdza tag jednostki przed nagłówka HTTP If-Match żądania. Jeśli tag jednostki nie znajduje się w nagłówku HTTP If-Match, a następnie <xref:System.ServiceModel.Web.WebFaultException> ze stanem jest generowany kod warunek wstępny nie powiodło się (412). Mechanizm aktualizacji warunkowego umożliwia klientowi serwera stwierdzić, że ma tej jednostki dla zasobu i tylko umożliwia klientowi alter zasobu. Jeśli jednostka ma jest aktualny. Przykład użycia <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> metody są widoczne w `UpdateCustomer` i `DeleteCustomer` operacje usługi. Tylko jako z <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>, ważne jest, aby należy zwrócić uwagę, który odwołuje się do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nie może zwracać. Deweloperzy powinien implementować operacji w taki sposób, że żądanie jest już znana się powodzeniem przed wywołaniem do <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> wykonane, na przykład jeśli wywołanie <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> nie jest obecny, usługa będzie odpowiadać, podając kod stanu powiodło się.  
  
 Próbka składa się z własnym hostowana usługa i klient, który jest uruchamiany w ramach aplikacji konsoli. Podczas działania aplikacji konsoli, klient wysyła żądania do usługi i zapisuje istotnych informacji z odpowiedzi w oknie konsoli.  
  
#### <a name="to-run-the-sample"></a>Aby uruchomić przykładowy  
  
1.  Otwórz rozwiązanie przykładowej warunkowego Get i Put. Podczas uruchamiania [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], należy uruchomić jako administrator, aby pomyślnie wykonać próbki. To zrobić, klikając prawym przyciskiem myszy [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ikony, jak i wybieranie **Uruchom jako Administrator** z menu kontekstowego.  
  
2.  Naciśnij klawisze CTRL + SHIFT + B Skompiluj rozwiązanie, a następnie naciśnij klawisz CTRL + F5, aby uruchomić projekt aplikacji konsoli. Jeśli uruchomiony ten projekt z włączonym (naciskając klawisz F5 zamiast CTRL + F5) debugowaniem, zatrzymuje debugera, gdy wyjątek przez warunkowy GET i PUT, sprawdzanie. W takim przypadku naciśnij klawisz F5, aby kontynuować wykonywanie przykładowej.  
  
3.  Wyświetlenie okna konsoli piasku zawiera identyfikator URI uruchomionej usługi i identyfikator URI strony pomocy HTML do uruchomionej usługi.  
  
4.  Jak działa próbki, klient wysyła żądania do usługi i zapisuje odpowiedzi w oknie konsoli.  
  
5.  Naciśnij dowolny klawisz, aby zakończyć próbki.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`
