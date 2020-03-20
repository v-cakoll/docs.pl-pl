---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: a80b5c3b336b4fd18b347a25ceaf509baf6461b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184394"
---
# <a name="systemwebrouting-integration"></a>Integracja elementu System.Web.Routing
Podczas hostowania usługi Windows Communication Foundation (WCF) w internetowej usłudze informacyjnej (IIS) umieszczasz plik .svc w katalogu wirtualnym. Ten plik .svc określa fabrykę hosta usługi do użycia, a także klasę, która implementuje usługę. Podczas składania żądań do usługi można określić plik .svc `http://contoso.com/EmployeeServce.svc`w identyfikatorze URI, na przykład: . Dla programistów piszących usługi REST ten typ identyfikatora URI nie jest optymalny. Identyfikatory URI dla usług REST określają określony zasób i zwykle nie mają żadnych rozszerzeń. Funkcja <xref:System.Web.Routing> integracji umożliwia hostowania usługi WCF REST, która odpowiada na identyfikatory URI bez rozszerzenia. Aby uzyskać więcej informacji na temat routingu, zobacz [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Korzystanie z integracji z usługą System.Web.Routing  
 Aby użyć <xref:System.Web.Routing> funkcji integracji, <xref:System.ServiceModel.Activation.ServiceRoute> należy użyć klasy, aby utworzyć <xref:System.Web.Routing.RouteTable> jedną lub więcej tras i dodać je do pliku Global.asax. Te trasy określają względne identyfikatory URI, na które usługa odpowiada. W przykładzie poniżej pokazano, jak to zrobić.  
  
```aspx-csharp  
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
  
 To kieruje wszystkie żądania z względnym identyfikatorem `Service` URI, który rozpoczyna się od klientów do usługi.  
  
 W pliku Web.config należy `System.Web.Routing.UrlRoutingModule` dodać moduł, `runAllManagedModulesForAllRequests` ustawić `true`atrybut do `UrlRoutingHandler` programu , `<system.webServer>` i dodać program obsługi do elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 To ładuje moduł i program obsługi wymagane do routingu. Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md). Należy również ustawić `aspNetCompatibilityEnabled` atrybut `true` w `<serviceHostingEnvironment>` elemencie, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Klasa, która implementuje usługę, musi włączyć wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
