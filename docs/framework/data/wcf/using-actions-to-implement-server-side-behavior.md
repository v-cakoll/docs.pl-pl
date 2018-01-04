---
title: "Za pomocą akcji do wykonania zachowanie po stronie serwera"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11a372db-7168-498b-80d2-9419ff557ba5
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d8ca19a5a49815130103672f43452ebbfedfae3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-actions-to-implement-server-side-behavior"></a>Za pomocą akcji do wykonania zachowanie po stronie serwera
Akcji OData umożliwiają wdrożenie zachowanie, który działa na zasób, który został pobrany z usługi OData.  Na przykład należy wziąć pod uwagę film cyfrowy jako zasób, istnieje wiele rzeczy, które można wykonać z film cyfrowy: wyewidencjonowania, szybkość/comment lub zaewidencjonowania. Są to wszystkie przykłady akcji, które mogą być wykonywane przez usługi danych WCF, która zarządza filmów cyfrowych. Działania są opisane w odpowiedzi OData, która zawiera zasób, w którym można wywołać akcję. Gdy użytkownik zażąda z zasobem, który reprezentuje film cyfrowy odpowiedź zwrócona z usługi danych WCF zawiera informacje o akcjach, które są dostępne dla tego zasobu. Dostępność akcji może zależeć od stanu usługi danych lub zasobu. Na przykład po filmu cyfrowego jest wyewidencjonowany go nie może zostać wyewidencjonowany przez innego użytkownika. Klienci mogą wywoływać akcję po prostu, określając adres URL. Na przykład http://MyServer/MovieService.svc/Movies (6) może zidentyfikować określonych film cyfrowy i http://MyServer/MovieService.svc/Movies (6) / Checkout powodowałoby wywołanie akcji w określonych filmu. Akcje umożliwiają można ujawnić modelu usługi bez narażania modelu danych. Kontynuowaniem service przykład movie, można zezwolić użytkownikowi na szybkości filmu, ale nie są bezpośrednio udostępniania danych klasyfikacji jako zasób. Można zaimplementować akcję szybkość pozwala użytkownikom sklasyfikować filmu, ale nie bezpośredni dostęp do danych klasyfikacji jako zasób.  
  
## <a name="implementing-an-action"></a>Implementowanie akcji  
 Do wykonania działania usługi, musisz zaimplementować <xref:System.IServiceProvider>, [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx), i [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) interfejsów. <xref:System.IServiceProvider>Usługi danych WCF można pobrać implementacji umożliwia [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx). [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) umożliwia usługi danych WCF w celu utworzenia, wyszukiwanie, opis i wywołania akcji usługi. [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) umożliwia wywoływać kod, który implementuje zachowanie działania usługi i uzyskiwać wyniki, jeśli istnieje. Należy pamiętać, że usługi danych WCF są każdego wywołania usługi WCF, nowe wystąpienie usługi zostanie utworzona na każdym razem, gdy usługa jest wywoływana.  Upewnij się, że nie niepotrzebne jest wykonać po utworzeniu usługi.  
  
### <a name="iserviceprovider"></a>Dostawca IServiceProvider  
 <xref:System.IServiceProvider>zawiera metodę o nazwie <xref:System.IServiceProvider.GetService%2A>. Ta metoda jest wywoływana przez usługi danych WCF można pobrać liczbę dostawców usług, w tym metadanych, dostawców usług i danych akcji usługodawców. Zwraca monit dla dostawcy danych usług akcji użytkownika [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) implementacji.  
  
### <a name="idataserviceactionprovider"></a>IDataServiceActionProvider  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) zawiera metody, dzięki którym można pobrać informacji o dostępnych akcji. Po zaimplementowaniu [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) są rozbudować metadanych usługi zdefiniowanego przez implementację usługi [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider(v=vs.113).aspx) z akcjami i Obsługa wysyłania te akcje zależnie od potrzeb.  
  
#### <a name="advertiseserviceaction"></a>AdvertiseServiceAction  
 [IDataServiceActionProvider](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.advertiseserviceaction(v=vs.113).aspx) jest wywoływana w celu ustalenia, jakie akcje są dostępne dla określonego zasobu. Ta metoda jest wywoływana tylko dla działań, które nie są zawsze dostępne. Służy do sprawdzania, jeśli akcja powinny być uwzględnione w odpowiedzi OData na podstawie stanu żądanych zasobów lub stan usługi. Jak odbywa się to sprawdzanie jest całkowicie od użytkownika. Jeśli jest kosztowna obliczania dostępności i bieżącego zasobu jest źródło danych, jest dopuszczalne pomijania sprawdzania i anonsowanie akcji. `inFeed` Ustawiono parametr `true` Jeśli bieżącego zasobu, zwracana jest częścią źródła danych.  
  
#### <a name="createinvokable"></a>CreateInvokable  
 [CreateInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceactionprovider.createinvokable(v=vs.113).aspx) jest wywoływana w celu utworzenia [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) zawierający delegata, który hermetyzuje kod, który implementuje zachowanie akcji. Spowoduje to utworzenie [IDataServiceInvokable](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable(v=vs.113).aspx) wystąpienia, ale nie jest wywoływany akcji. Akcje usługi danych WCF mieć skutki uboczne i trzeba również działać łącznie z dostawcą aktualizacji, aby zapisać te zmiany na dysku. [IDataServiceInvokable.Invoke](https://msdn.microsoft.com/library/system.data.services.providers.idataserviceinvokable.invoke(v=vs.113).aspx) metoda jest wywoływana z SaveChanges() dostawcy aktualizacji metoda jest wywoływana.  
  
#### <a name="getserviceactions"></a>GetServiceActions  
 Ta metoda zwraca kolekcję [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) wystąpień, które reprezentują wszystkie działania udostępnia usługi danych WCF. [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) reprezentacja metadanych akcję, która zawiera informacje, takie jak nazwy akcji, parametrów i jej typu zwracanego.  
  
#### <a name="getserviceactionsbybindingparametertype"></a>GetServiceActionsByBindingParameterType  
 Ta metoda zwraca kolekcję wszystkich [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) wystąpień, które może być powiązana z typem parametru określonego powiązania. Innymi słowy, wszystkie [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx)s, który może działać na typ określonego zasobu (nazywanych również typ parametru wiązania). To jest używany podczas usługi zwraca zasobu, aby dołączyć informacje o akcjach, które mogą być wywoływane dla tego zasobu. Ta metoda powinna zwracać tylko akcje, które można powiązać z typem parametru dokładne powiązania (nie typy pochodne). Ta metoda jest wywoływana raz na każde żądanie na typ, a wynik jest buforowany przez usługi danych WCF.  
  
#### <a name="tryresolveserviceaction"></a>TryResolveServiceAction  
 Ta metoda szuka określonej [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) i zwraca `true` Jeśli [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) został znaleziony. Jeśli znaleziono [ServiceAction](https://msdn.microsoft.com/library/system.data.services.providers.serviceaction(v=vs.113).aspx) jest zwracany w `serviceAction``out` parametru.  
  
### <a name="idataserviceinvokable"></a>IDataServiceInvokable  
 Ten interfejs umożliwia wykonanie akcji usługi danych WCF. Podczas implementowania IDataServiceInvokable jest odpowiedzialny za 3 rzeczy:  
  
1.  Przechwytywanie i potencjalnie przekazywanie parametrów  
  
2.  Podczas wysyłania parametrów do kodu, który faktycznie implementuje akcji, gdy jest wywoływana przez metodę invoke() wykonaną  
  
3.  Przechowywanie dowolnego wyniki przez metodę invoke() wykonaną mogą zostać pobrane za pomocą GetResult()  
  
 Parametry mogą być przekazywane jako tokenów. Jest to, ponieważ jest możliwe do zapisania danych dostawcy usług, który współpracuje z tokenów, które reprezentują zasobów, jeśli jest to konieczne może być przekonwertować (kierowanie) tych tokenów w rzeczywistych zasobów przed wysyłką, do rzeczywistych akcji. Po parametrze został skierowany, tak aby wszystkie zmiany do zasobu, występujące po wywołaniu akcji zostaną zapisane i zapisany na dysku musi być w stanie edycji.  
  
 Ten interfejs wymaga dwóch metod: wywołanie i GetResult. Wywołanie wywołuje delegata, który implementuje zachowanie akcji i GetResult zwraca wynik akcji.  
  
## <a name="invoking-a-wcf-data-service-action"></a>Wywoływanie akcję usługi danych WCF  
 Akcje są wywoływane przy użyciu żądania HTTP POST. Adres URL określa zasobów, a po niej nazwę akcji. Parametry są przekazywane w treści żądania. Na przykład jeśli wystąpił usługi o nazwie MovieService, który ujawniany akcji o nazwie szybkości. Wywołanie akcji szybkość na określonych filmu można użyć następującego adresu URL:  
  
 (1) / szybkość http://MovieServer/MovieService.svc/Movies  
  
 Movies(1) określa film, który ma zostać współczynnik i szybkość Określa szybkość działania. Rzeczywistej wartości ocena będzie w treści żądania HTTP, jak pokazano w poniższym przykładzie:  
  
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
>  W powyższym przykładowym kodzie będą działać tylko z 5.2 usługi danych WCF i później, która zawiera obsługę lekkiej serializacji JSON. Jeśli przy użyciu wcześniejszej wersji usługi danych WCF, należy określić właściwości json pełne content-type w następujący sposób: `application/json;odata=verbose`.  
  
 Alternatywnie można wywołać operacji za pomocą klienta usługi danych WCF, jak pokazano w poniższy fragment kodu.  
  
```  
MoviesModel context = new MoviesModel (new Uri("http://MyServer/MoviesService.svc/"));  
            //...  
            context.Execute(new Uri("http://MyServer/MoviesService.svc/Movies(1)/Rate"), "POST", new BodyOperationParameter("rating",4) );           
```  
  
 W powyższym, fragment kodu `MoviesModel` klasa została wygenerowana przy użyciu programu Visual Studio, aby dodać odwołania do usługi do usługi danych WCF.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi danych WCF 4.5](../../../../docs/framework/data/wcf/index.md)  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Tworzenie i wdrażanie usług danych programu WCF](../../../../docs/framework/data/wcf/developing-and-deploying-wcf-data-services.md)  
 [Niestandardowi dostawcy usługi danych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
