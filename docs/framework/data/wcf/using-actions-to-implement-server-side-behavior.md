---
title: Używanie akcji do implementacji zachowania po stronie serwera
ms.date: 03/30/2017
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
ms.openlocfilehash: 5c71cfe8965cf8edbe07ff7ae4c6be95b437bf80
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894254"
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Używanie akcji do implementacji zachowania po stronie serwera

Akcje OData umożliwiają wdrożenie zachowania, które działa w przypadku zasobu pobranego z usługi OData. Na przykład w przypadku filmu cyfrowego należy wziąć pod uwagę wiele rzeczy, które można wykonać za pomocą filmu cyfrowego: wyewidencjonowywanie, wskaźnik/komentarz lub ewidencjonowanie. Są to wszystkie przykłady akcji, które mogą być implementowane przez usługę danych programu WCF, która zarządza cyfrowymi filmami. Akcje są opisane w odpowiedzi OData, która zawiera zasób, w którym można wywołać akcję. Gdy użytkownik zażąda zasobu, który reprezentuje film cyfrowy, odpowiedź zwrócona z usługi danych programu WCF zawiera informacje o akcjach, które są dostępne dla tego zasobu. Dostępność akcji może zależeć od stanu usługi danych lub zasobu. Na przykład po wyewidencjonowaniu filmu cyfrowego nie można go wyewidencjonować przez innego użytkownika. Klienci mogą wywołać akcję po prostu podając adres URL. Na przykład `http://MyServer/MovieService.svc/Movies(6)` zidentyfikuje określony film cyfrowy i `http://MyServer/MovieService.svc/Movies(6)/Checkout` wywoła akcję na określonym filmie. Akcje umożliwiają udostępnienie modelu usług bez uwidaczniania modelu danych. Kontynuując korzystanie z przykładu usługi filmowej, możesz chcieć zezwolić użytkownikowi na ocenianie filmu, ale nie ujawniać bezpośrednio danych klasyfikacji jako zasobu. Można zaimplementować akcję rate, aby umożliwić użytkownikowi ocenę filmu, ale nie uzyskanie bezpośredniego dostępu do danych klasyfikacji jako zasobu.
  
## <a name="implementing-an-action"></a>Implementowanie akcji  
 Aby zaimplementować akcję usługi <xref:System.IServiceProvider>, należy zaimplementować interfejsy, [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103))i [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) . <xref:System.IServiceProvider>zezwala Usługi danych programu WCF na pobieranie implementacji [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)). [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) umożliwia usługi danych programu WCF tworzenie, Znajdowanie, opisywanie i wywoływanie akcji usługi. [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) umożliwia wywołanie kodu, który implementuje zachowanie działania usługi i pobiera wyniki, jeśli istnieją. Należy pamiętać, że Usługi danych programu WCF są usługi WCF dla wywołań, nowe wystąpienie usługi zostanie utworzone za każdym razem, gdy usługa zostanie wywołana.  Upewnij się, że nie ma żadnych niepotrzebnych zadań podczas tworzenia usługi.  
  
### <a name="iserviceprovider"></a>IServiceProvider  
 <xref:System.IServiceProvider>zawiera metodę o nazwie <xref:System.IServiceProvider.GetService%2A>. Ta metoda jest wywoływana przez Usługi danych programu WCF w celu pobrania wielu dostawców usług, w tym dostawców usług metadanych i dostawców akcji usługi danych. Po wyświetleniu monitu o dostawcę akcji usługi danych Zwróć implementację programu [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) .  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) zawiera metody, które umożliwiają pobieranie informacji o dostępnych akcjach. Podczas implementowania [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) są rozszerzane metadane usługi, która jest definiowana przez implementację usługi [IDataServiceActionProvider](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859915(v=vs.103)) z akcjami i obsługa wysyłania do tych akcji jako wymaga.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [Metoda AdvertiseServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859971(v=vs.103)) jest wywoływana w celu określenia, jakie akcje są dostępne dla określonego zasobu. Ta metoda jest wywoływana tylko w przypadku akcji, które nie są zawsze dostępne. Służy do sprawdzania, czy akcja powinna zostać uwzględniona w odpowiedzi OData w zależności od stanu żądanego zasobu lub stanu usługi. Jak to sprawdzanie jest wykonywane całkowicie do Ciebie. Jeśli Obliczanie dostępności jest kosztowne, a bieżący zasób jest w strumieniu, można pominąć sprawdzanie i zaanonsować akcję. Parametr jest ustawiany na, `true` Jeśli bieżący zwracany zasób jest częścią źródła danych. `inFeed`  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859940(v=vs.103)) jest wywoływana, aby utworzyć [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , który zawiera delegata, który hermetyzuje kod implementujący zachowanie akcji. Spowoduje to utworzenie wystąpienia [IDataServiceInvokable](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859893(v=vs.103)) , ale nie wywołanie akcji. Akcje usługi danych programu WCF mają efekty uboczne i muszą współpracować z dostawcą aktualizacji w celu zapisania tych zmian na dysku. Metoda [IDataServiceInvokable. Invoke](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh859924(v=vs.103)) jest wywoływana z metody metody SaveChanges () dostawcy aktualizacji.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Ta metoda zwraca kolekcję wystąpień [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) , które reprezentują wszystkie akcje ujawniane przez usługę danych programu WCF. [ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) to reprezentacja metadanych akcji, która obejmuje informacje takie jak nazwa akcji, jej parametry i typ zwracany.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Ta metoda zwraca kolekcję wszystkich wystąpień [akcji](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) , które można powiązać z określonym typem parametru powiązania. Innymi słowy, wszystkie [Akcje ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103))s, które mogą działać na określonym typie zasobu (nazywany również typem parametru wiązania). Jest on używany, gdy usługa zwraca zasób w celu uwzględnienia informacji o akcjach, które mogą być wywoływane względem tego zasobu. Ta metoda powinna zwracać tylko akcje, które można powiązać z dokładnym typem parametru powiązania (brak typów pochodnych). Ta metoda jest wywoływana raz dla każdego żądania na typ, a wynik jest buforowany przez Usługi danych programu WCF.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Ta metoda wyszukuje określoną [akcję ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) i zwraca `true` czy znaleziono [akcję ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) . Jeśli zostanie znaleziona, w `serviceAction` `out` parametrze zostanie zwrócona [Akcja ServiceAction](https://docs.microsoft.com/previous-versions/dotnet/wcf-data-services/hh544089(v=vs.103)) .  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Ten interfejs zapewnia sposób wykonywania akcji usługi danych programu WCF. Podczas wdrażania IDataServiceInvokable użytkownik jest odpowiedzialny za 3 rzeczy:  
  
1. Przechwytywanie i potencjalnie organizowanie parametrów  
  
2. Wysyłanie parametrów do kodu, który faktycznie implementuje akcję, gdy wywoływana jest metoda Invoke ()  
  
3. Przechowywanie jakichkolwiek wyników z wywołania (), aby można je było pobrać przy użyciu metody GetResult ()  
  
 Parametry mogą być przesyłane jako tokeny. Wynika to z faktu, że można napisać dostawcę usługi danych, który działa z tokenami reprezentującymi zasoby. Jeśli tak jest, może być konieczne przekonwertowanie (kierowanie) tych tokenów na rzeczywiste zasoby przed wysłaniem ich do rzeczywistej akcji. Po przekierowaniu parametru musi on być w stanie umożliwiającym edycję, aby wszelkie zmiany w zasobie, które wystąpiły po wywołaniu akcji, zostaną zapisane i zapisane na dysku.  
  
 Ten interfejs wymaga dwóch metod: Invoke i GetResult. Wywołanie wywołuje obiekt delegowany implementujący zachowanie akcji i GetResult zwraca wynik akcji.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Wywoływanie akcji usługi danych programu WCF  
 Akcje są wywoływane za pomocą żądania HTTP POST. Adres URL określa zasób, po którym następuje nazwa akcji. Parametry są przesyłane w treści żądania. Na przykład jeśli istnieje usługa o nazwie MovieService, która uwidacznia akcję o nazwie rate. Aby wywołać akcję rate dla określonego filmu, można użyć następującego adresu URL:  
  
 `http://MovieServer/MovieService.svc/Movies(1)/Rate`
  
 Filmy (1) określają film, który ma być oceniany, i szybkość Określa akcję stawki. Rzeczywista wartość klasyfikacji będzie w treści żądania HTTP, jak pokazano w następującym przykładzie:  
  
```http
POST http://MovieServer/MoviesService.svc/Movies(1)/Rate HTTP/1.1   
Content-Type: application/json   
Content-Length: 20   
Host: localhost:15238  
{   
   "rating": 4   
}  
```  
  
> [!WARNING]
> Powyższy przykładowy kod będzie działał tylko z Usługi danych programu WCF 5,2 i nowszymi, które obsługują oświetlenie JSON. W przypadku korzystania ze starszej wersji Usługi danych programu WCF należy określić pełną zawartość JSON typu w następujący sposób: `application/json;odata=verbose`.  
  
 Alternatywnie można wywołać akcję przy użyciu klienta Usługi danych programu WCF, jak pokazano w poniższym fragmencie kodu.  
  
```csharp
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
//...  
context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );
```
  
 W powyższym fragmencie kodu `MoviesModel` Klasa została wygenerowana przy użyciu programu Visual Studio, aby Dodaj odwołanie do usługi do usługi danych programu WCF.  
  
## <a name="see-also"></a>Zobacz także

- [Usługi danych WCF 4.5](index.md)
- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Tworzenie i wdrażanie usług danych programu WCF](developing-and-deploying-wcf-data-services.md)
- [Niestandardowi dostawcy usługi danych](custom-data-service-providers-wcf-data-services.md)
