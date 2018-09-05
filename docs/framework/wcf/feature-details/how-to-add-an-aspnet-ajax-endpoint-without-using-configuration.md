---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 18c02644319dd9d11be39ac4956a4dcf50db3078
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525142"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji
Windows Communication Foundation (WCF) pozwala utworzyć usługę, która udostępnia obsługą ASP.NET AJAX punktu końcowego, który może zostać wywołana z języka JavaScript w witrynie sieci Web klienta. Aby utworzyć punkt końcowy, można za pomocą pliku konfiguracji, jak wszystkie inne punkty końcowe WCF lub należy użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono drugiego podejścia.  
  
 Aby tworzyć usługi przy użyciu punktów końcowych ASP.NET AJAX bez konfiguracji, usług musi być hostowany przez Internetowe usługi informacyjne (IIS). Aby aktywować tę funkcję punktu końcowego ASP.NET AJAX przy użyciu tej metody, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku svc. Ta fabryka niestandardowego jest składnikiem, który automatycznie konfiguruje punktu końcowego ASP.NET AJAX, dzięki czemu może ona zostać wywołana z kodu JavaScript w witrynie sieci Web klienta.  
  
 Aby uzyskać przykład pracy, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Aby uzyskać omówienie sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji, zobacz [porady: Użyj konfiguracji, aby dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawowe usługi WCF  
  
1.  Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>. Pamiętaj ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Definiowanie przestrzeni nazw `ICalculator` i `CalculatorService` implementacje opakowując w bloku przestrzeni nazw.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Do hostowania usługi w programie Internet Information Services bez konfiguracji  
  
1.  Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować punktu końcowego ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Twórz usługi i wywołać go z klienta. Internet Information Services (IIS) aktywuje usługę, gdy zostanie wywołana. Aby uzyskać więcej informacji o hostingu w usługach IIS, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Konfigurowany jest punkt końcowy adresem pusty względem pliku SVC, dzięki czemu usługa jest teraz dostępny i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji. Używając go, wprowadzając adres URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX programu ASP.NET. Aby uzyskać przykład, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Przykład  
  
 Punkt końcowy automatycznie konfigurowany jest tworzony w pusty adres względem podstawowego adresu URL. Plik konfiguracji mogą być również dodawane lub używany w przypadku tej metody. Jeśli plik konfiguracji zawiera definicji punktów końcowych, tych punktów końcowych są dodawane do endpoint automatycznie konfigurowane.  
  
 Na przykład używa service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> i katalog usługi zawiera pliku Web.config, który definiuje punktu końcowego dla tej samej usługi za pomocą <xref:System.ServiceModel.BasicHttpBinding> pod adresem względna "soap". W tym przypadku usługa zawiera dwa punkty końcowe: pojedynczo service.svc (co odpowiada na żądania ASP.NET AJAX), a drugi na service.svc/soap (co odpowiada na żądania protokołu SOAP).  
  
 Jeśli plik konfiguracyjny definiuje punkt końcowy na pusty adres względny i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używany, zostanie zgłoszony wyjątek i nie można uruchomić usługi.  
  
 Nie można użyć konfiguracji, aby zmodyfikować ustawienia w punkcie końcowym automatycznie konfigurowane. Jeśli wszystkie ustawienia (np. czytnik limit przydziału) musi być zmodyfikowany, nie można używać bezpłatnie konfiguracji podejście, usuwając <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> z pliku svc i tworzenie wpisu konfiguracji dla punktu końcowego.  
  
 Jeśli usługa wymaga tryb zgodności ASP.NET — na przykład, jeśli używa <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji platformy ASP.NET — plik konfiguracji jest nadal wymagane, aby włączyć ten tryb. Element konfiguracji, wymagane jest [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który musi zostać dodany w następujący sposób.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Aby uzyskać więcej informacji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Klasa jest klasy pochodnej <xref:System.ServiceModel.Activation.ServiceHostFactory>. Aby uzyskać szczegółowy opis mechanizm fabryka hostów usługi zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
