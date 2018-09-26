---
title: Używanie akcji do implementacji zachowania po stronie serwera
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 515553540053ed0c16085fde06e2cc2d2dedda1e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204482"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Używanie akcji do implementacji zachowania po stronie serwera

Akcje protokołu OData umożliwiają implementowanie zachowania, które podejmuje działania dotyczące zasobów, pobierane z usługi OData. Na przykład rozważmy film cyfrowy jako zasób, istnieje wiele rzeczy, które można wykonać za pomocą cyfrowych film: wyewidencjonowanie, szybkość/comment lub ewidencjonowania. Są to wszystkie przykłady działań, które mogą być zaimplementowane przez usługi danych WCF, która zarządza filmów cyfrowych. Akcje są opisane w odpowiedzi OData, która zawiera zasób, na którym może być wywołana Akcja. Gdy użytkownik zażąda z zasobem, który reprezentuje film cyfrowy odpowiedź zwrócona z usługi danych WCF zawiera informacje o akcjach, które są dostępne dla tego zasobu. Dostępność akcji może zależeć od stanu zasobu lub usługi danych. Na przykład, gdy film cyfrowy jest wyewidencjonowany go nie może być wyewidencjonowany przez innego użytkownika. Klienci mogą wywołać akcję poprzez określenie adresu URL. Na przykład `http://MyServer/MovieService.svc/Movies(6)` będzie identyfikować określonych film cyfrowy i `http://MyServer/MovieService.svc/Movies(6)/Checkout` powodowałoby wywołanie pliku wykonywalnego działania w określonym filmu. Akcje umożliwiają możesz udostępnić modelu usługi bez narażania modelu danych. Kontynuując przykład usługi filmu, możesz umożliwić użytkownikowi szybkości filmu, ale nie są bezpośrednio uwidaczniać dane ocenę jako zasób. Można zaimplementować akcją kurs pozwala użytkownikom sklasyfikować filmu, ale nie są bezpośrednio uzyskać dostęp do danych klasyfikację jako zasób.
  
## <a name="implementing-an-action"></a>Implementowanie akcji  
 Do wykonania działania usługi, musisz zaimplementować <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), i [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) interfejsów. <xref:System.IServiceProvider> Umożliwia WCF Data Services uzyskać implementacji [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) umożliwia usługi danych WCF w celu tworzenia, znajdowanie, opis i wywołania akcji usługi. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) pozwala wywołuje kod, który implementuje zachowanie akcji usługi i uzyskiwać wyniki, jeśli istnieje. Należy pamiętać o tym, czy na wywołanie usług WCF, nowe wystąpienie klasy usługi WCF Data Services zostanie utworzony w każdym razem, gdy usługa jest wywoływana.  Upewnij się, że bez niepotrzebnych wykonywania pracy po utworzeniu usługi.  
  
### <a name="iserviceprovider"></a>Element IServiceProvider  
 <xref:System.IServiceProvider> zawiera metodę o nazwie <xref:System.IServiceProvider.GetService%2A>. Ta metoda jest wywoływana przez usługi danych WCF w celu pobrania liczba dostawców usług, w tym metadanych, dostawców usług i dostawcy akcji usługi danych. Po wyświetleniu monitu Akcja dostawcy usługi danych, zwraca swoje [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) implementacji.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) zawiera metody, które umożliwiają pobieranie informacji o dostępnych akcji. Podczas implementacji [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) są przestarzałe metadanych dla usługi, która jest zdefiniowana przez implementację usługi [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) z akcjami i Obsługa wysyłania tych akcji, zgodnie z potrzebami.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) jest wywoływana w celu określenia, jakie akcje są dostępne dla określonego zasobu. Ta metoda jest wywoływana tylko w akcji, które nie są zawsze dostępne. Służy do sprawdzenia, czy akcja powinien być uwzględniony w odpowiedzi OData, w zależności od stanu żądanych zasobów lub stanu usługi. Jak odbywa się to sprawdzanie jest całkowicie do Ciebie. Jeśli jest kosztowna obliczania dostępności i bieżącego zasobu jest źródło danych, jest dopuszczalne pomijania sprawdzania i anonsowanie akcji. `inFeed` Parametr ma wartość `true` Jeśli bieżącego zasobu, zwracana jest częścią źródła danych.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) jest wywoływana, aby utworzyć [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) zawierający delegata, który hermetyzuje kod, który implementuje zachowanie akcji. Spowoduje to utworzenie [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) wystąpienia, ale nie wywołuje akcję. Akcje usługi danych WCF mają skutki uboczne i musisz pracować w połączeniu z dostawcą aktualizacji, aby zapisać te zmiany na dysku. [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) metoda jest wywoływana z SaveChanges() dostawca aktualizacji, zostanie wywołana metoda.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Ta metoda zwraca kolekcję [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) wystąpień, które reprezentują wszystkie akcje udostępnia usługi danych WCF. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) to reprezentacja metadanych akcję, która zawiera informacje, takie jak nazwy akcji, jego parametry i jego typem zwracanym.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Ta metoda zwraca kolekcję wszystkich [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) wystąpień, które może być powiązana z typem parametru określonego powiązania. Innymi słowy, wszystkie [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)s, która może działać na określony typ zasobu (nazywane również typ parametru wiązania). Służy to, gdy usługa zwraca zasobu, aby dołączyć informacje o akcjach, które można wywołać wobec tego zasobu. Ta metoda powinna zwrócić tylko akcje, które można powiązać typ parametru wiązania dokładne (Brak typów pochodnych). Ta metoda jest wywoływana jeden raz na każde żądanie, według typu napotkał, a wynik jest buforowany przez WCF Data Services.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Metoda ta wyszukuje określoną [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) i zwraca `true` Jeśli [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) zostanie znaleziony. Jeśli znaleziono [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) jest zwracany w `serviceAction` `out` parametru.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Ten interfejs umożliwia wykonywanie akcji usług danych WCF. Podczas implementowania IDataServiceInvokable odpowiedzialność za 3 rzeczy:  
  
1.  Przechwytywanie i potencjalnie przekazywanie parametrów  
  
2.  Parametry, aby kod, który faktycznie implementuje akcji, gdy wywoływana jest Invoke() wysyłki  
  
3.  Przechowywanie dowolnego wynikiem Invoke(), dzięki czemu mogą być pobierane, za pomocą GetResult()  
  
 Parametry mogą być przekazywane jako tokenów. To dlatego istnieje możliwość zapisu danych dostawcy usług, działająca z tokenów, które reprezentują zasoby, jeśli jest to przypadek, konieczne może być przekonwertować (marshal) tokeny te służą do rzeczywistych zasobów przed wysłaniem do rzeczywistego akcji. Po parametrze został skierowany, tak aby zmiany do zasobu, które występują podczas wywoływania akcji zostaną zapisane i będą zapisane na dysku musi być w stanie edycji.  
  
 Ten interfejs wymaga dwóch metod: wywołania i GetResult. Wywoływanie wywołuje delegata, który implementuje zachowanie akcji i zwraca GetResult wynik monitorowanej akcji.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Wywołanie akcji usług danych WCF  
 Akcje są wywoływane za pomocą żądania HTTP POST. Adres URL Określa zasób następuje nazwa akcji. Parametry są przekazywane w treści żądania. Na przykład, jeśli było usługi o nazwie MovieService, na której widoczne akcję o nazwie szybkości. Można użyć następującego adresu URL wywołanie akcji stawki na określonych film:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Movies(1) określa filmu, którą chcesz nawiązać za oraz stawkę za określa szybkość akcji. Rzeczywistej wartości ocena będzie w treści żądania HTTP, jak pokazano w poniższym przykładzie:  
  
```  
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> Powyższy kod przykładowy będzie działać tylko w przypadku 5.2 usług danych WCF i później, który ma pomocy technicznej dla lekkiej serializacji JSON. Jeśli przy użyciu starszej wersji usługi danych WCF, należy określić właściwość json pełne content-type w następujący sposób: `application/json;odata=verbose`.  
  
 Alternatywnie możesz wywołać akcję za pomocą klienta usługi danych WCF, jak pokazano w poniższym fragmencie kodu.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 W powyższym fragmencie kodu `MoviesModel` klasy został wygenerowany przy użyciu programu Visual Studio Dodaj odwołanie do usługi z usługą danych programu WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi danych WCF 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Tworzenie i wdrażanie usług danych programu WCF](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Niestandardowi dostawcy usługi danych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
