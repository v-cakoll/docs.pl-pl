---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185138"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta. Aby utworzyć taki punkt końcowy, można użyć pliku konfiguracji, podobnie jak w przypadku wszystkich innych punktów końcowych WCF lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono drugie podejście.  
  
 Aby utworzyć usługi z ASP.NET punktami końcowymi AJAX bez konfiguracji, usługi muszą być hostowane przez internetowe usługi informacyjne (IIS). Aby aktywować punkt końcowy ASP.NET AJAX przy użyciu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> tej metody, należy określić jako Factory parametru w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku .svc. Ta niestandardowa fabryka jest składnikiem, który automatycznie konfiguruje ASP.NET punkt końcowy AJAX, dzięki czemu można go wywołać z języka JavaScript w witrynie sieci Web klienta.  
  
 Na przykład roboczy zobacz [usługę AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Aby uzyskać kontur sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracyjnych, zobacz [Jak: Dodawanie ASP.NET punktu końcowego ajaxu za pomocą funkcji Konfigurowania.](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawową usługę WCF  
  
1. Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem. Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku . Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwość.  
  
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
  
2. `ICalculator` Zaimplementuj `CalculatorService`umowę serwisową z programem .  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Zdefiniuj `ICalculator` obszar `CalculatorService` nazw dla i implementacji, zawijając je w bloku obszaru nazw.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Hostować usługę w internetowych usługach informacyjnych bez konfiguracji  
  
1. Utwórz nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji. Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi. Określ, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> że ma być używany w [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy, aby automatycznie skonfigurować ASP.NET punktu końcowego AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Skompiluj usługę i wywołaj ją od klienta. Internetowe usługi informacyjne (IIS) aktywują usługę po wywołaniu. Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [Jak: Hostowanie usługi WCF w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Aby zadzwonić do usługi  
  
1. Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku .svc, więc usługa jest teraz dostępna i może\<być wywoływana przez wysyłanie żądań do service.svc/ operation> — na przykład service.svc/Add dla `Add` operacji. Można go użyć, wprowadzając adres URL usługi do kolekcji Skrypty ASP.NET kontrolki Menedżera skryptów AJAX. Na przykład zobacz [usługę AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Przykład  
  
 Automatycznie skonfigurowany punkt końcowy jest tworzony przy pustym adresie względem podstawowego adresu URL. Plik konfiguracji można również dodać i używać z tym podejściem. Jeśli plik konfiguracji zawiera definicje punktów końcowych, te punkty końcowe są dodawane do automatycznie skonfigurowany punkt końcowy.  
  
 Na przykład service.svc używa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> katalogu usługi i zawiera plik Web.config, który definiuje punkt końcowy <xref:System.ServiceModel.BasicHttpBinding> dla tej samej usługi przy użyciu w "mydło" względny adres. W takim przypadku usługa zawiera dwa punkty końcowe: jeden w service.svc (który odpowiada na żądania ASP.NET AJAX) i inny w service.svc/soap (który odpowiada na żądania protokołu SOAP).  
  
 Jeśli plik konfiguracji definiuje punkt końcowy przy pustym <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> adresie względnym i jest używany, wyjątek jest zgłaszany i usługa nie może się uruchomić.  
  
 Nie można użyć konfiguracji do modyfikowania ustawień w automatycznie skonfigurowanym punkcie końcowym. Jeśli należy zmodyfikować dowolne ustawienie (takie jak przydział czytnika), nie należy <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> używać podejścia bezkonfiguracyjnego, usuwając z pliku .svc i tworząc wpis konfiguracji dla punktu końcowego.  
  
 Jeśli usługa wymaga ASP.NET trybu zgodności — na przykład, jeśli <xref:System.Web.HttpContext> używa mechanizmów autoryzacji klasy lub ASP.NET — do włączenia tego trybu nadal jest wymagany plik konfiguracyjny. Wymagany element konfiguracji jest [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który należy dodać w następujący sposób.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Aby uzyskać więcej informacji, zobacz [WCF Services i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.  
  
 Klasa <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest klasą pochodną . <xref:System.ServiceModel.Activation.ServiceHostFactory> Aby uzyskać szczegółowe wyjaśnienie mechanizmu fabrycznego hosta usługi, zobacz [rozszerzenie hostingu przy użyciu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
