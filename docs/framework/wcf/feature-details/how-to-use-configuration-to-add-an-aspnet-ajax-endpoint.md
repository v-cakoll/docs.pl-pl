---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 97f8174161068f2c72b6bd2bc4e8a3044f5bccdd
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051665"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która udostępnia punkt końcowy z obsługą technologii AJAX ASP.NET, który może być wywoływany z JavaScript w klienckiej witrynie sieci Web. Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych programu Windows Communication Foundation (WCF), lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono podejście konfiguracyjne.  
  
 Część procedury, która umożliwia przeznaczenie punktu końcowego usługi ASP.NET z włączoną obsługą technologii AJAX, obejmuje skonfigurowanie punktu końcowego do użycia <xref:System.ServiceModel.WebHttpBinding> i do dodania [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) zachowania punktu końcowego. Po skonfigurowaniu punktu końcowego czynności do wdrożenia i hostowania usługi są podobne do tych, które są używane przez usługę WCF. Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX przy użyciu protokołu HTTP Post](../samples/ajax-service-using-http-post.md).  
  
 Aby uzyskać więcej informacji o konfigurowaniu punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [How to: Add a ASP.NET AJAX Endpoint bez using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
## <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawową usługę WCF  
  
1. Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute> . Upewnij się, że właściwość jest ustawiona <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .  
  
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
  
2. Zaimplementuj `ICalculator` kontrakt usługi za pomocą `CalculatorService` .  
  
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
  
3. Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i, `CalculatorService` umieszczając je w bloku przestrzeni nazw.  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Aby utworzyć punkt końcowy ASP.NET AJAX dla usługi  
  
1. Utwórz konfigurację zachowań i określ [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla punktów końcowych z obsługą technologii AJAX ASP.NET.  
  
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
  
2. Utwórz punkt końcowy dla usługi używającej <xref:System.ServiceModel.WebHttpBinding> zachowania ASP.NET AJAX zdefiniowanej w poprzednim kroku.  
  
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
  
1. Aby hostować usługę w usługach IIS, Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji. Edytuj ten plik, dodając odpowiednie informacje o dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) dla usługi. Na przykład zawartość pliku usługi dla `CalculatorService` przykładu zawiera poniższe informacje.  
  
    ```aspx-csharp
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [How to: hosting a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).  
  
## <a name="to-call-the-service"></a>Aby wywołać usługę  
  
1. Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/ \<operation> -na przykład Service. svc/Add dla `Add` operacji. Można go użyć, wprowadzając adres URL punktu końcowego do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET. Aby zapoznać się z przykładem, zobacz [usługi AJAX przy użyciu protokołu HTTP Post](../samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
