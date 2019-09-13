---
title: 'Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895080"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia punkt końcowy z obsługą technologii AJAX ASP.NET, który można wywołać z JavaScript w witrynie sieci Web klienta. Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, podobnie jak w przypadku wszystkich innych punktów końcowych WCF, lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono drugie podejście.  
  
 Aby można było tworzyć usługi z ASP.NETymi punktami końcowymi AJAX bez konfiguracji, usługi muszą być hostowane przez Internet Information Services (IIS). Aby aktywować punkt końcowy ASP.NET AJAX przy użyciu tego podejścia, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki [ \@w dyrektywie ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) w pliku SVC. Ta fabryka niestandardowa jest składnikiem, który automatycznie konfiguruje punkt końcowy ASP.NET AJAX, aby można go było wywołać z JavaScript w klienckiej witrynie sieci Web.  
  
 Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
 Aby uzyskać informacje na temat sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji, [zobacz How to: Użyj konfiguracji, aby dodać punkt końcowy](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawową usługę WCF  
  
1. Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute>. Upewnij się, <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> że właściwość jest ustawiona.  
  
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
  
2. Zaimplementuj kontrakt `CalculatorService` `ICalculator` usługi za pomocą.  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i `CalculatorService` , umieszczając je w bloku przestrzeni nazw.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Aby hostować usługę w Internet Information Services bez konfiguracji  
  
1. Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji. Edytuj ten plik, dodając odpowiednie [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informacje o dyrektywie ServiceHost dla usługi. Określ, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używana [ \@w dyrektywie ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) , aby automatycznie konfigurować punkt końcowy ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Utwórz usługę i Wywołaj ją z poziomu klienta. Internet Information Services (IIS) aktywuje usługę po wywołaniu. Aby uzyskać więcej informacji na temat hostingu w usługach [IIS, zobacz How to: Hostowanie usługi WCF w usługach](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)IIS.  
  
### <a name="to-call-the-service"></a>Aby wywołać usługę  
  
1. Punkt końcowy jest skonfigurowany pod adresem pustym względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/\<Operation > — na przykład Service. svc/Add `Add` dla operacji. Można go użyć, wprowadzając adres URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET. Aby zapoznać się z przykładem, zobacz [Usługa AJAX bez konfiguracji](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Przykład  
  
 Automatycznie skonfigurowany punkt końcowy jest tworzony pod pustym adresem względem podstawowego adresu URL. Plik konfiguracji można także dodać i użyć z tym podejściem. Jeśli plik konfiguracji zawiera definicje punktów końcowych, te punkty końcowe są dodawane do automatycznie skonfigurowanego punktu końcowego.  
  
 Na przykład usługa Service. svc korzysta z <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> programu, a katalog usługi zawiera plik Web. config, który definiuje punkt końcowy dla tej samej usługi <xref:System.ServiceModel.BasicHttpBinding> przy użyciu adresu względnego "SOAP". W takim przypadku usługa zawiera dwa punkty końcowe: jeden w usłudze Service. svc (który reaguje na żądania ASP.NET AJAX) i inny w usłudze Service. svc/SOAP (który reaguje na żądania protokołu SOAP).  
  
 Jeśli plik konfiguracji definiuje punkt końcowy w pustym adresie względnym i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używany, zostanie zgłoszony wyjątek i uruchomienie usługi nie powiedzie się.  
  
 Nie można użyć konfiguracji w celu zmodyfikowania ustawień w automatycznie skonfigurowanym punkcie końcowym. Jeśli konieczne jest zmodyfikowanie dowolnego ustawienia (takiego jak przydział czytnika), nie należy używać podejścia <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> z bezpłatną konfiguracją, usuwając plik z pliku svc i tworząc wpis konfiguracji dla punktu końcowego.  
  
 Jeśli usługa wymaga trybu zgodności ASP.NET — na przykład jeśli używa <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji ASP.NET — plik konfiguracji jest nadal wymagany do włączenia tego trybu. Wymagany element konfiguracji jest [ \<elementem ServiceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) , który należy dodać w następujący sposób.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Aby uzyskać więcej informacji, zobacz temat [usługi WCF i ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) .  
  
 Klasa jest klasą pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory> <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> . Szczegółowy opis mechanizmu fabryki hosta usługi znajduje się w temacie [Rozszerzanie hostingu przy użyciu obiektu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) .  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web ASP.NET z obsługą technologii AJAX do programu WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
