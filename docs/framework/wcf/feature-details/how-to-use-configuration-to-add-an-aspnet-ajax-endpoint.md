---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: f14b441ead7c701aa4f794370fc5f54ad3b4a4e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji
Windows Communication Foundation (WCF) służy do tworzenia usługi, która sprawia, że włączone ASP.NET AJAX punktu końcowego dostępne, który można wywołać z poziomu języka JavaScript w witrynie sieci Web klienta. Można utworzyć punktu końcowego, można użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych usług Windows Communication Foundation (WCF) lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono podejście konfiguracji.  
  
 Część tej procedury, która umożliwia punktu końcowego usługi stać się z obsługą środowiska ASP.NET AJAX składa się z konfigurowania punktu końcowego, aby użyć <xref:System.ServiceModel.WebHttpBinding> i dodać [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowania punktu końcowego. Po skonfigurowaniu punktu końcowego, kroki do wdrażania i obsługi usługi są podobne do tych używanych przez usługi WCF. Na przykład pracy, zobacz [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Aby uzyskać więcej informacji o sposobie konfigurowania punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [porady: Dodawanie ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawowej usługi WCF  
  
1.  Zdefiniuj podstawowego kontraktu usługi WCF przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdej operacji z <xref:System.ServiceModel.OperationContractAttribute>. Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  Implementowanie `ICalculator` kontraktu usługi o `CalculatorService`.  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  Zdefiniuj przestrzeń nazw dla `ICalculator` i `CalculatorService` implementacje zawijania je w bloku przestrzeni nazw.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Można utworzyć punktu końcowego ASP.NET AJAX dla usługi  
  
1.  Utwórz konfigurację zachowania i określ [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla komputerów z obsługą środowiska ASP.NET AJAX punktów końcowych usługi.  
  
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
  
2.  Tworzenie punktu końcowego usługi, która używa <xref:System.ServiceModel.WebHttpBinding> i zachowanie środowiska ASP.NET AJAX, zdefiniowane w poprzednim kroku.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>Do obsługi usługi w usługach IIS  
  
1.  Do obsługi usługi w usługach IIS, Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytowanie tego pliku, dodając odpowiednie [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Na przykład zawartość w pliku usługi `CalculatorService` przykład zawiera następujące informacje.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Punkt końcowy jest skonfigurowana pod adresem pusty względem pliku SVC, dlatego usługa jest teraz dostępna i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji. Można go przy użyciu adresu URL punktu końcowego do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET. Na przykład zobacz [AJAX Service przy użyciu protokołu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
