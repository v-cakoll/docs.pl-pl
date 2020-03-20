---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184835"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia ASP.NET punkt końcowy z obsługą AJAX, który można wywołać z języka JavaScript w witrynie sieci Web klienta. Aby utworzyć taki punkt końcowy, można użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych programu Windows Communication Foundation (WCF) lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono podejście konfiguracji.  
  
 Część procedury, która umożliwia punkt końcowy usługi, aby stać się ASP.NET ajax włączone polega <xref:System.ServiceModel.WebHttpBinding> na skonfigurowaniu punktu końcowego do korzystania i dodać [ \<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie punktu końcowego. Po skonfigurowaniu punktu końcowego kroki implementacji i hostowania usługi są podobne do tych używanych przez dowolną usługę WCF. Na przykład roboczy zobacz [usługę AJAX przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Aby uzyskać więcej informacji na temat konfigurowania punktu końcowego ASP.NET AJAX bez użycia konfiguracji, zobacz [Jak: Dodawanie ASP.NET punktu końcowego AJAX bez użycia konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawową usługę WCF  
  
1. Zdefiniuj podstawową umowę serwisową <xref:System.ServiceModel.ServiceContractAttribute> WCF za pomocą interfejsu oznaczonego atrybutem. Oznacz każdą operację <xref:System.ServiceModel.OperationContractAttribute>za pomocą pliku . Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwość.  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
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
        // Other operations omitted…
    }
    ```  
  
3. Zdefiniuj `ICalculator` obszar `CalculatorService` nazw dla i implementacji, zawijając je w bloku obszaru nazw.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Aby utworzyć ASP.NET punkt końcowy AJAX dla usługi  
  
1. Utwórz konfigurację zachowania i określ zachowanie [ \<>enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) dla ASP.NET punktów końcowych usługi obsługujących technologię AJAX.  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. Utwórz punkt końcowy dla usługi, <xref:System.ServiceModel.WebHttpBinding> która używa i ASP.NET zachowanie AJAX zdefiniowane w poprzednim kroku.  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>
    ```  
  
## <a name="to-host-the-service-in-iis"></a>Aby hostować usługę w usługach IIS  
  
1. Aby hostować usługę w usługach IIS, należy utworzyć nowy plik o nazwie usługa z rozszerzeniem .svc w aplikacji. Edytuj ten plik, [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dodając odpowiednie informacje o dyrektywie ServiceHost dla usługi. Na przykład zawartość w pliku usługi `CalculatorService` dla próbki zawiera następujące informacje.  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [Jak: Hostowanie usługi WCF w usługach IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Aby zadzwonić do usługi  
  
1. Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku .svc, więc usługa jest teraz dostępna i może\<być wywoływana przez wysyłanie żądań do service.svc/ operation> — na przykład service.svc/Add dla `Add` operacji. Można go użyć, wprowadzając adres URL punktu końcowego do kolekcji Skrypty ASP.NET kontrolki Menedżera skryptów AJAX. Na przykład zobacz [usługę AJAX przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
