---
title: 'Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 079bbd98b3fc3d5538f87cad39a4a83a0dc1e242
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863338"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET
Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia obsługą ASP.NET AJAX punktu końcowego, który może zostać wywołana z języka JavaScript w witrynie sieci Web klienta. Opisano podstawowe procedury dotyczące tworzenia takich usług w [jak: Użyj konfiguracji, aby dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [porady: Dodawanie platformy ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX obsługuje operacje, które za pomocą usług zleceń HTTP POST i HTTP GET, POST protokołu HTTP, domyślna. Podczas tworzenia operacją, która ma żadnych efektów ubocznych i zwraca dane, które nigdy lub rzadko zmieniają, użyj HTTP GET. Wyniki operacji GET mogą być buforowane, co oznacza, że wiele wywołań do tej samej operacji może spowodować tylko jedno żądanie do usługi. Buforowanie odbywa się przez architekturę WCF, ale może odbywać się na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy i innych poziomów.) Buforowanie jest korzystne, czy chcesz zwiększyć wydajność usługi, ale nie można zaakceptować, jeśli dane zmieniają się często, czy operacja wykonuje jakąś akcję.  
  
 Na przykład w przypadku projektowania usługi do zarządzania użytkownika Biblioteka utworów muzycznych, operacja, która wyszukuje wykonawcy, w oparciu o albumu tytuł korzyści z używania GET, ale operacja, która albumu są dodawane do kolekcji osobistych użytkownika należy użyć POST.  
  
 Aby kontrolować okres istnienia pamięci podręcznej, należy użyć <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu. Na przykład podczas projektowania usługi, która zwraca prognozy pogody aktualizowane co godzinę, należy użyć pobieranie, ale ograniczyć czas trwania pamięci podręcznej na godzinę lub mniej, aby uniemożliwić dostęp do starych danych w użytkownicy usługi.  
  
 Korzystając z usługi ze strony ASP.NET AJAX, które korzystają z kontrolki Menedżera skryptów, nie ma znaczenia, czy używa operacji GET lub POST - mechanizm Menedżera skryptów zapewnia wystawiony typu poprawnego żądania.  
  
 Operacje HTTP GET używają parametrów wejściowych, obsługiwane przez operacje POST, w tym typy kontraktu danych złożonych. Jednak w większości przypadków zalecane jest aby uniknąć zbyt wiele parametrów lub parametry, które są zbyt złożone, w ramach operacji GET, ponieważ redukuje efektywność buforowania.  
  
 W tym temacie pokazano, jak wybrać między GET i POST poprzez dodanie <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty do odpowiednich operacji w kontrakcie usługi. Pozostałe kroki (w celu zaimplementowania, konfigurowania i obsługi usługi), które są wymagane, aby uzyskać usługa jest uruchomiona są podobne do tych używanych przez dowolną usługę środowiska ASP.NET AJAX w programie WCF.  
  
 Operacja oznaczona za pomocą <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądanie GET. Operacja oznaczona za pomocą <xref:System.ServiceModel.Web.WebInvokeAttribute>, lub oznaczona za pomocą dowolnego z tych argumentów, używa żądania POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> Umożliwia korzystanie z innych poleceń HTTP, innymi niż GET i POST (na przykład PUT i DELETE) za pośrednictwem <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości. Tych poleceń nie są obsługiwane przez program ASP.NET AJAX. Jeśli zamierzasz korzystać z usługi strony ASP.NET, za pomocą kontrolki Menedżera skryptów, nie używaj <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.  
  
 Aby uzyskać przykład pracy przełączania GET, zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.  
  
 Dla przykładu korzystającego z wpisu, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Tworzenie usługi WCF, reaguje na HTTP GET lub POST protokołu HTTP żądania  
  
1.  Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>. Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby określić, że operacja powinna odpowiadać na żądania HTTP GET. Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu jawnie określić POST protokołu HTTP lub określono atrybut, którego wartość domyślna to POST protokołu HTTP.  
  
    ```  
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
  
2.  Implementowanie `IMusicService` kontraktu usługi o `MusicService`.  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować punktu końcowego ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Operacje GET usługi bez konieczności wprowadzania kodu klienta można przetestować przy użyciu przeglądarki. Na przykład, jeśli usługa jest skonfigurowana na "http://example.com/service.svc"address, wpisując"http://example.com/service.svc/LookUpArtist?album=SomeAlbum" do przeglądarki wywołuje usługę paska adresu i powoduje, że odpowiedź do pobrania lub wyświetlone.  
  
2.  Za pomocą usług operacje GET w taki sam sposób jak inne usługi ASP.NET AJAX —, wprowadzając usługę kontrolować adres URL do kolekcji skryptów Menedżera skryptów AJAX programu ASP.NET. Aby uzyskać przykład, zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
