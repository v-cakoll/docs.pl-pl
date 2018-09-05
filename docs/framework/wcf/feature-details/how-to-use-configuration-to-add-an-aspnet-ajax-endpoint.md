---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3a3474dc04ce2cda63157e68597d1184e9b2bf15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559954"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji
Windows Communication Foundation (WCF) pozwala utworzyć usługę, która sprawia, że obsługą ASP.NET AJAX punkt końcowy dostępny, którą można wywołać z kodu JavaScript w witrynie sieci Web klienta. Aby utworzyć punkt końcowy, można za pomocą pliku konfiguracji, jak wszystkie inne punkty końcowe usług Windows Communication Foundation (WCF) lub należy użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono metody konfiguracji.  
  
 Część procedury, która umożliwia punkt końcowy usługi staną się obsługą ASP.NET AJAX składa się z Konfigurowanie punkt końcowy do użycia <xref:System.ServiceModel.WebHttpBinding> i dodawanie [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie punktu końcowego. Po skonfigurowaniu punktu końcowego, kroki do wdrażania i obsługi usługi są podobne do tych używanych przez żadnej usługi WCF. Aby uzyskać przykład pracy, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
 Aby uzyskać więcej informacji o sposobie konfigurowania punktu końcowego ASP.NET AJAX bez używania konfiguracji, zobacz [porady: Dodawanie platformy ASP.NET AJAX konfiguracji punktu końcowego bez przy użyciu](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawowe usługi WCF  
  
1.  Zdefiniuj podstawowego kontraktu usługi WCF z interfejsem oznaczone <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznaczania każdej operacji za pomocą <xref:System.ServiceModel.OperationContractAttribute>. Pamiętaj ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
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
  
3.  Definiowanie przestrzeni nazw `ICalculator` i `CalculatorService` implementacje opakowując w bloku przestrzeni nazw.  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>Aby utworzyć punktu końcowego ASP.NET AJAX dla usługi  
  
1.  Utwórz konfigurację zachowania i określ [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) zachowanie dla komputerów z obsługą ASP.NET AJAX punktów końcowych usługi.  
  
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
  
2.  Utworzenie punktu końcowego usługi, która używa <xref:System.ServiceModel.WebHttpBinding> i zachowanie ASP.NET AJAX, zdefiniowane w poprzednim kroku.  
  
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
  
### <a name="to-host-the-service-in-iis"></a>Do hostowania usługi w usługach IIS  
  
1.  Aby hostować usługi w programie IIS, Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytuj ten plik, dodając odpowiednie [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Na przykład zawartość w pliku usługi `CalculatorService` przykład zawiera następujące informacje.  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  Aby uzyskać więcej informacji o hostingu w usługach IIS, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Konfigurowany jest punkt końcowy adresem pusty względem pliku SVC, dzięki czemu usługa jest teraz dostępny i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji. Używając go, wprowadzając adres URL punktu końcowego w kolekcji skryptów kontrolki Menedżera skryptów AJAX programu ASP.NET. Aby uzyskać przykład, zobacz [AJAX usługi za pomocą żądania HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
