---
title: "Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa8aceace03d1abb3bb83de1262331485f12ded3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a>Instrukcje: Wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Służy do tworzenia usługi, która przedstawia włączone ASP.NET AJAX punktu końcowego, który można wywołać z poziomu języka JavaScript w witrynie sieci Web klienta. Omówiono podstawowe czynności umożliwiające tworzenie tych usług w [jak: Użyj konfiguracji można dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) i [porady: Dodawanie ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
 ASP.NET AJAX obsługuje operacje, które używających zleceń HTTP POST i HTTP GET, POST protokołu HTTP jest wartość domyślna. Podczas tworzenia operacji, która nie ma skutków ubocznych i zwraca dane, które nigdy lub rzadko zmiany, należy użyć HTTP GET. Można buforować wyniki operacji GET, co oznacza, że wiele wywołań do tej samej operacji może spowodować tylko jedno żądanie do usługi. Buforowanie nie została wykonana [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , ale może odbywać się na dowolnym poziomie (w przeglądarce użytkownika, na serwerze proxy oraz innych poziomach.) Buforowanie jest korzystne w przypadku, jeśli chcesz zwiększyć wydajność usługi, ale nie można zaakceptować, jeśli często zmiany danych lub, gdy działanie wykonuje akcję.  
  
 Na przykład w przypadku projektowania usługi biblioteki utworów muzycznych użytkownika zarządzania operację, która wyszukuje wykonawcy oparte na albumu tytuł korzyści z używania GET, ale jest operacja, która dodaje albumu do kolekcji osobistych użytkownika musi użyć POST.  
  
 Aby kontrolować okres istnienia pamięci podręcznej, użyj <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu. Na przykład podczas projektowania usługi, która zwraca prognozy pogody aktualizowane co godzinę, należy użyć GET, ale ograniczyć czas buforowania na godzinę lub mniej, aby uniemożliwić dostęp do starych danych użytkowników usługi.  
  
 Podczas korzystania z usług ze strony ASP.NET AJAX, korzystających z kontroli Menedżer skryptów, nie ma różnicy czy używa operacji GET lub POST - mechanizm skryptu w Menedżerze zapewnia wystawiony typ poprawne żądania.  
  
 Operacji HTTP GET, użyj parametrów wejściowych obsługiwane przez operacje POST, w tym typy kontraktu danych złożonych. Jednak w większości przypadków zaleca się unikać zbyt wiele parametrów i parametrów, które są zbyt złożone, w ramach operacji GET, ponieważ zmniejsza wydajność buforowania.  
  
 W tym temacie przedstawiono sposób wybierania między GET i POST poprzez dodanie <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty do odpowiednich operacji w kontrakcie usługi. Inne czynności (w celu wdrożenia, konfigurowania i obsługi usługi), które są wymagane do pobrania działanie usługi są podobne do tych używanych przez usługi ASP.NET AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Operacja oznaczonych <xref:System.ServiceModel.Web.WebGetAttribute> zawsze używa żądanie GET. Operacja oznaczonych <xref:System.ServiceModel.Web.WebInvokeAttribute>, lub oznaczone za pomocą dowolnego z tych argumentów, używa żądania POST. <xref:System.ServiceModel.Web.WebInvokeAttribute> Zezwala na korzystanie z innych zleceń HTTP innych niż GET i POST (na przykład PUT i DELETE) za pośrednictwem <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości. Tych poleceń nie są obsługiwane przez program ASP.NET AJAX. Jeśli zamierzasz korzystać z stron ASP.NET, za pomocą skryptu menedżera kontroli usługi, nie używaj <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> właściwości.  
  
 Na przykład pracy przełączania do pobrania, zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) próbki.  
  
 Dla przykładu, która używa POST, zobacz [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) próbki.  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a>Tworzenie usługi WCF który odpowiada na HTTP GET lub POST protokołu HTTP żądania  
  
1.  Zdefiniuj podstawowego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdej operacji z <xref:System.ServiceModel.OperationContractAttribute>. Dodaj <xref:System.ServiceModel.Web.WebGetAttribute> atrybutu, aby określić, że operacja powinna odpowiadać na żądania HTTP GET. Można również dodać <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutu, aby jawnie określić HTTP POST, lub Określa atrybut, który domyślnie HTTP POST.  
  
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
  
3.  Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytowanie tego pliku, dodając odpowiednie [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy do automatycznego konfigurowania punktu końcowego ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Operacje GET z usługi bez żadnych kod klienta można przetestować przy użyciu przeglądarki. Na przykład jeśli usługa jest skonfigurowana pod adresem "http://example.com/service.svc", wpisując "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" na pasku adresu przeglądarki wywołuje usługę i powoduje, że odpowiedź jako pobrane lub wyświetlone.  
  
2.  Wykorzystanie usług z operacjami GET w taki sam sposób jak inne usługi ASP.NET AJAX — wprowadzając usługę kontrola adres URL do kolekcji skryptów Menedżer skryptów AJAX ASP.NET. Na przykład zobacz [podstawowa usługa AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
