---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: cc3cca2ed703c4329b3da7c6fde286c341459fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496129"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji
Windows Communication Foundation (WCF) służy do tworzenia usługi, która przedstawia włączone ASP.NET AJAX punktu końcowego, który można wywołać z poziomu języka JavaScript w witrynie sieci Web klienta. Można utworzyć punktu końcowego, można użyć pliku konfiguracji, tak jak w przypadku wszystkich innych punktów końcowych WCF lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono drugiej metody.  
  
 Do tworzenia usług z punktów końcowych ASP.NET AJAX bez konfiguracji, usługi musi być obsługiwana przez Internet Information Services (IIS). Aby aktywować punktu końcowego ASP.NET AJAX przy użyciu tej metody, należy określić <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki w [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy w pliku svc. Ta fabryka niestandardowych jest składnik, który automatycznie konfiguruje punktu końcowego ASP.NET AJAX, dzięki czemu mogą być wywoływane z JavaScript w witrynie sieci Web klienta.  
  
 Na przykład pracy, zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Omówienie sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji dla [porady: Użyj konfiguracji można dodać punktu końcowego AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawowej usługi WCF  
  
1.  Zdefiniuj podstawowego kontraktu usługi WCF przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdej operacji z <xref:System.ServiceModel.OperationContractAttribute>. Należy ustawić <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> właściwości.  
  
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
  
3.  Zdefiniuj przestrzeń nazw dla `ICalculator` i `CalculatorService` implementacje zawijania je w bloku przestrzeni nazw.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Do obsługi usługi przez Internetowe usługi informacyjne bez konfiguracji  
  
1.  Utwórz nowy plik o nazwie usługi z rozszerzeniem .svc w aplikacji. Edytowanie tego pliku, dodając odpowiednie [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy informacji dla usługi. Określić, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używany w [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) dyrektywy do automatycznego konfigurowania punktu końcowego ASP.NET AJAX.  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  Tworzenie usługi i wywołać go z klienta. Internet Information Services (IIS) aktywuje usługę po wywołaniu. Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Do wywołania tej usługi  
  
1.  Punkt końcowy jest skonfigurowana pod adresem pusty względem pliku SVC, dlatego usługa jest teraz dostępna i może być wywoływany przez wysyłanie żądań do service.svc/\<operacji > — na przykład service.svc/Add dla `Add` operacji. Można go przy użyciu adresu URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET. Na przykład zobacz [usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Przykład  
  
 Punkt końcowy skonfigurowany automatycznie jest tworzony w pusty adres względem podstawowego adresu URL. Plik konfiguracji można również dodany i używany z tą metodą. Jeśli plik konfiguracji zawiera definicje punktu końcowego, te punkty końcowe są dodawane do punktu końcowego skonfigurowane automatycznie.  
  
 Na przykład używa service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> i katalog usługi zawiera plik Web.config, który definiuje punktu końcowego dla tego samego przy użyciu usługi <xref:System.ServiceModel.BasicHttpBinding> pod adresem względnej "soap". W takim przypadku usługa zawiera dwa punkty końcowe: po service.svc (który odpowiada na żądania środowiska ASP.NET AJAX) i drugi w service.svc/soap (który odpowiada na żądania SOAP).  
  
 Jeśli plik konfiguracyjny definiuje punkt końcowy pod adresem pustą względnej i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używana, jest zwracany wyjątek, i nie można uruchomić usługi.  
  
 Nie można użyć konfiguracji, aby zmodyfikować ustawienia automatycznie konfigurowane w punkcie końcowym. Jeśli wszystkie ustawienia (np. czytnik limit przydziału) musi być zmodyfikowana, nie można używać bez konfiguracji korzystania przez usunięcie <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> w pliku svc i tworzenie pozycji konfiguracji punktu końcowego.  
  
 Jeśli usługa wymaga tryb zgodności ASP.NET — na przykład, gdy jest używana funkcja <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji programu ASP.NET — plik konfiguracji jest nadal wymagane, aby włączyć ten tryb. Element konfiguracji, wymagane jest [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który musi zostać dodany w następujący sposób.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Aby uzyskać więcej informacji, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tematu.  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Klasy jest klasy pochodnej z <xref:System.ServiceModel.Activation.ServiceHostFactory>. Aby uzyskać szczegółowy opis mechanizmu fabryki hosta usługi, zobacz [rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [Instrukcje: migrowanie usług internetowych obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
