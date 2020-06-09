---
title: 'Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9aab53d6457aa7848fd4acea6317a30da352cc98
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579634"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>Instrukcje: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji
Windows Communication Foundation (WCF) umożliwia utworzenie usługi, która uwidacznia punkt końcowy z obsługą technologii AJAX ASP.NET, który można wywołać z JavaScript w witrynie sieci Web klienta. Aby utworzyć taki punkt końcowy, możesz użyć pliku konfiguracji, podobnie jak w przypadku wszystkich innych punktów końcowych WCF, lub użyć metody, która nie wymaga żadnych elementów konfiguracji. W tym temacie przedstawiono drugie podejście.  
  
 Aby można było tworzyć usługi z ASP.NETymi punktami końcowymi AJAX bez konfiguracji, usługi muszą być hostowane przez Internet Information Services (IIS). Aby aktywować punkt końcowy ASP.NET AJAX przy użyciu tego podejścia, określ <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr fabryki w dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) w pliku SVC. Ta fabryka niestandardowa jest składnikiem, który automatycznie konfiguruje punkt końcowy ASP.NET AJAX, aby można go było wywołać z JavaScript w klienckiej witrynie sieci Web.  
  
 Aby zapoznać się z przykładem roboczym, zobacz [Usługa AJAX bez konfiguracji](../samples/ajax-service-without-configuration.md).  
  
 Aby uzyskać informacje na temat sposobu konfigurowania punktu końcowego ASP.NET AJAX przy użyciu elementów konfiguracji, zobacz [How to: use Configuration to Add a ASP.NET AJAX Endpoint](how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
### <a name="to-create-a-basic-wcf-service"></a>Aby utworzyć podstawową usługę WCF  
  
1. Zdefiniuj podstawową umowę usługi WCF z interfejsem oznaczonym przy użyciu <xref:System.ServiceModel.ServiceContractAttribute> atrybutu. Oznacz każdą operację za pomocą <xref:System.ServiceModel.OperationContractAttribute> . Upewnij się, że właściwość jest ustawiona <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> .  
  
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
  
2. Zaimplementuj `ICalculator` kontrakt usługi za pomocą `CalculatorService` .  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. Zdefiniuj przestrzeń nazw dla `ICalculator` implementacji i, `CalculatorService` umieszczając je w bloku przestrzeni nazw.  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>Aby hostować usługę w Internet Information Services bez konfiguracji  
  
1. Utwórz nowy plik o nazwie usługa z rozszerzeniem SVC w aplikacji. Edytuj ten plik, dodając odpowiednie informacje o dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) dla usługi. Określ, że <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ma być używana w dyrektywie [ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) , aby automatycznie konfigurować punkt końcowy ASP.NET AJAX.  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. Utwórz usługę i Wywołaj ją z poziomu klienta. Internet Information Services (IIS) aktywuje usługę po wywołaniu. Aby uzyskać więcej informacji na temat hostingu w usługach IIS, zobacz [How to: hosting a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).  
  
### <a name="to-call-the-service"></a>Aby wywołać usługę  
  
1. Punkt końcowy jest skonfigurowany pod pustym adresem względem pliku SVC, więc usługa jest teraz dostępna i może być wywoływana przez wysyłanie żądań do usługi Service. svc/ \<operation> -na przykład Service. svc/Add dla `Add` operacji. Można go użyć, wprowadzając adres URL usługi do kolekcji skryptów kontrolki Menedżera skryptów AJAX ASP.NET. Aby zapoznać się z przykładem, zobacz [Usługa AJAX bez konfiguracji](../samples/ajax-service-without-configuration.md).  
  
## <a name="example"></a>Przykład  
  
 Automatycznie skonfigurowany punkt końcowy jest tworzony pod pustym adresem względem podstawowego adresu URL. Plik konfiguracji można także dodać i użyć z tym podejściem. Jeśli plik konfiguracji zawiera definicje punktów końcowych, te punkty końcowe są dodawane do automatycznie skonfigurowanego punktu końcowego.  
  
 Na przykład usługa Service. svc korzysta z programu <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> , a katalog usługi zawiera plik Web. config, który definiuje punkt końcowy dla tej samej usługi przy użyciu <xref:System.ServiceModel.BasicHttpBinding> adresu względnego "SOAP". W takim przypadku usługa zawiera dwa punkty końcowe: jeden w usłudze Service. svc (który reaguje na żądania ASP.NET AJAX) i inny w usłudze Service. svc/SOAP (który reaguje na żądania protokołu SOAP).  
  
 Jeśli plik konfiguracji definiuje punkt końcowy w pustym adresie względnym i <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jest używany, zostanie zgłoszony wyjątek i uruchomienie usługi nie powiedzie się.  
  
 Nie można użyć konfiguracji w celu zmodyfikowania ustawień w automatycznie skonfigurowanym punkcie końcowym. Jeśli konieczne jest zmodyfikowanie dowolnego ustawienia (takiego jak przydział czytnika), nie należy używać podejścia z bezpłatną konfiguracją, usuwając <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> plik z pliku svc i tworząc wpis konfiguracji dla punktu końcowego.  
  
 Jeśli usługa wymaga trybu zgodności ASP.NET — na przykład jeśli używa <xref:System.Web.HttpContext> klasy lub mechanizmów autoryzacji ASP.NET — plik konfiguracji jest nadal wymagany do włączenia tego trybu. Wymagany element konfiguracji to [\<serviceHostingEnvironment>](../../configure-apps/file-schema/wcf/servicehostingenvironment.md) element, który należy dodać w następujący sposób.  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 Aby uzyskać więcej informacji, zobacz temat [usługi WCF i ASP.NET](wcf-services-and-aspnet.md) .  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>Klasa jest klasą pochodną <xref:System.ServiceModel.Activation.ServiceHostFactory> . Szczegółowy opis mechanizmu fabryki hosta usługi znajduje się w temacie [Rozszerzanie hostingu przy użyciu obiektu ServiceHostFactory](../extending/extending-hosting-using-servicehostfactory.md) .  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie usług WCF w technologii AJAX na platformie ASP.NET](creating-wcf-services-for-aspnet-ajax.md)
- [Instrukcje: Migrowanie usług sieci Web obsługujących technologię AJAX i opartych na platformie ASP.NET do programu WCF](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
