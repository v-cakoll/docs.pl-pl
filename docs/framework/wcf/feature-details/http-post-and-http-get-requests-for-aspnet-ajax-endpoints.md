---
title: 'Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184753"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET

Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta. Podstawowe procedury tworzenia takich usług zostały omówione w artykule [Jak: Użyj konfiguracji, aby dodać ASP.NET punkt końcowy AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [Jak: Dodaj ASP.NET punkt końcowy AJAX bez użycia konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX obsługuje operacje korzystające z zleceń HTTP POST i HTTP GET, przy czym domyślnym ustawieniem jest protokół HTTP POST. Podczas tworzenia operacji, która nie ma skutków ubocznych i zwraca dane, które rzadko lub nigdy się nie zmienia, należy użyć HTTP GET zamiast. Wyniki operacji GET mogą być buforowane, co oznacza, że wiele wywołań tej samej operacji może spowodować tylko jedno żądanie do usługi. Buforowanie nie jest wykonywane przez WCF, ale może odbywać się na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy i innych poziomach). Buforowanie jest korzystne, jeśli chcesz zwiększyć wydajność usługi, ale może nie być dopuszczalne, jeśli dane często się zmieniają lub jeśli operacja wykonuje pewne działania.  
  
 Na przykład jeśli projektujesz usługę do zarządzania biblioteką muzyczną użytkownika, operacja, która wyszukuje wykonawcę na podstawie tytułu albumu, korzysta z użycia GET, ale operacja, która dodaje album do osobistej kolekcji użytkownika, musi używać postu.  
  
 Aby kontrolować okres istnienia pamięci <xref:System.ServiceModel.Web.OutgoingWebResponseContext> podręcznej, należy użyć typu. Na przykład podczas projektowania usługi, która zwraca prognozy pogody aktualizowane co godzinę, należy użyć GET, ale ograniczyć czas trwania pamięci podręcznej do godziny lub mniej, aby uniemożliwić użytkownikom usługi dostęp do starych danych.  
  
 Podczas korzystania z usług ze strony ASP.NET AJAX, które używają formantu Menedżera skryptów, nie ma znaczenia, czy operacja używa GET lub POST — mechanizm menedżera skryptów zapewnia, że zostanie wystawiony poprawny typ żądania.  
  
 Operacje HTTP GET używają dowolnych parametrów wejściowych obsługiwanych przez operacje POST, w tym złożonych typów kontraktów danych. Jednak w większości przypadków zaleca się unikanie zbyt wielu parametrów lub parametrów, które są zbyt złożone w operacjach GET, ponieważ zmniejsza wydajność buforowania.  
  
 W tym temacie pokazano, jak wybrać między <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> GET i POST, dodając lub atrybuty do odpowiednich operacji w umowie serwisowej. Inne kroki (do zaimplementowania, skonfigurować i obsługiwać usługę), które są wymagane do uruchomienia usługi są podobne do tych używanych przez dowolny ASP.NET usługi AJAX w WCF.  
  
 Operacja oznaczona <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądania GET. Operacja oznaczona <xref:System.ServiceModel.Web.WebInvokeAttribute>, lub nie oznaczona dowolnym z dwóch atrybutów, używa żądania POST. Umożliwia <xref:System.ServiceModel.Web.WebInvokeAttribute> korzystanie z innych zleceń HTTP, innych niż GET i POST <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> (takich jak PUT i DELETE) za pośrednictwem właściwości. Jednak te zlecenia nie są obsługiwane przez ASP.NET AJAX. Jeśli zamierzasz korzystać z usługi z ASP.NET stron za pomocą formantu Menedżera skryptów, nie należy używać <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.  
  
 Aby uzyskać działający przykład przełączania do GET, zobacz przykład [podstawowej usługi AJAX.](../../../../docs/framework/wcf/samples/basic-ajax-service.md)  
  
 Przykładowy używany post można znaleźć w przykładzie usługi AJAX przy użyciu protokołu [HTTP POST.](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Aby utworzyć usługę WCF, która odpowiada na żądania HTTP GET lub HTTP POST
  
1. Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem. Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku . Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybut, aby określić, że operacja powinna odpowiadać na żądania HTTP GET. Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybut, aby jawnie określić HTTP POST lub nie określić atrybutu, który domyślnie jest HTTP POST.
  
    ```csharp
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. `IMusicService` Zaimplementuj `MusicService`umowę serwisową z programem .
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. Utwórz nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji. Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi. Określ, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> że ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować ASP.NET punktu końcowego AJAX.  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a>Aby zadzwonić do usługi  
  
1. Można przetestować operacje GET usługi bez kodu klienta, za pomocą przeglądarki. Na przykład jeśli usługa jest skonfigurowana `http://example.com/service.svc` pod adresem, a następnie wpisanie `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na pasku adresu przeglądarki wywołuje usługę i powoduje, że odpowiedź ma zostać pobrana lub wyświetlona.
  
2. Usługi z operacjami GET można używać w taki sam sposób, jak w przypadku innych usług ASP.NET usługi AJAX — wprowadzając adres URL usługi w kolekcji Skrypty formantu ASP.NET menedżera skryptów AJAX. Na przykład zobacz [podstawową usługę AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
