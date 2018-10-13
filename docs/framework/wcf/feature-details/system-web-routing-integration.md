---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3b95b3117941ce7d019b87b00181b2cbac652f43
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308211"
---
# <a name="systemwebrouting-integration"></a>Integracja elementu System.Web.Routing
W przypadku hostowania usługi Windows Communication Foundation (WCF) w Internet Information Service (IIS) możesz umieścić plik .svc w katalogu wirtualnym. Ten plik .svc określa fabryki hostów usług do użycia oraz klasy, która implementuje usługę. W przypadku wysyłania żądań do usługi można określić plików .svc w identyfikatorze URI, na przykład: `http://contoso.com/EmployeeServce.svc`. Programistom pisanie usług REST tego rodzaju identyfikatora URI nie jest optymalne. Identyfikatory URI dla usługi REST Określ określonego zasobu i zwykle nie mają żadnych rozszerzeń. <xref:System.Web.Routing> Funkcji integracji umożliwia hostowanie usługi WCF REST reagującego na identyfikatory URI bez rozszerzenia. Aby uzyskać więcej informacji o routingu, zobacz [routingu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).  
  
## <a name="using-systemwebrouting-integration"></a>Za pomocą integracja elementu System.Web.Routing  
 Aby użyć <xref:System.Web.Routing> używać funkcji integracji <xref:System.ServiceModel.Activation.ServiceRoute> klasy, aby utworzyć jeden lub więcej tras i dodać je do <xref:System.Web.Routing.RouteTable> w pliku Global.asax. Te trasy Określ względne identyfikatory URI, które odpowiada usługa. W przykładzie poniżej pokazano, jak to zrobić.  
  
```  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));   
   }  
</script>  
```  
  
 Kierowane wszystkie żądania z względny identyfikator URI rozpoczynający się ze swoimi klientami, aby `Service` usługi.  
  
 W pliku Web.config musisz dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawia `runAllManagedModulesForAllRequests` atrybutu `true`i Dodaj `UrlRoutingHandler` program obsługi `<system.webServer>` elementu, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 Spowoduje to załadowanie modułu i obsługi wymagane do routingu. Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md). Należy także ustawić `aspNetCompatibilityEnabled` atrybutu `true` w `<serviceHostingEnvironment>` elementu, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Klasa, która implementuje usługę należy włączyć wymagania dotyczące zgodności platformy ASP.NET, jak pokazano w poniższym przykładzie.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Routingu platformy ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660)
