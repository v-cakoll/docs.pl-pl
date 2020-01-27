---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: fdc355d4560294a16f3e9c488fdaf142d2982c0d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745343"
---
# <a name="systemwebrouting-integration"></a>Integracja elementu System.Web.Routing
W przypadku hostowania usługi Windows Communication Foundation (WCF) w usłudze Internet Information Service (IIS) Umieść plik. svc w katalogu wirtualnym. Ten plik SVC określa fabrykę hosta usługi, która ma być używana, a także klasy implementującej usługę. Podczas wykonywania żądań do usługi należy określić plik SVC w identyfikatorze URI, na przykład: `http://contoso.com/EmployeeServce.svc`. Dla programistów piszące usługi REST ten typ URI nie jest optymalny. Identyfikatory URI usług REST określają konkretny zasób i zwykle nie mają żadnych rozszerzeń. Funkcja integracji <xref:System.Web.Routing> umożliwia Hostowanie usługi REST WCF, która reaguje na identyfikatory URI bez rozszerzenia. Aby uzyskać więcej informacji na temat routingu, zobacz [ASP.NET routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Korzystanie z integracji system. Web. Routing  
 Aby użyć funkcji integracji <xref:System.Web.Routing>, należy użyć klasy <xref:System.ServiceModel.Activation.ServiceRoute> do utworzenia jednej lub większej liczby tras i dodania ich do <xref:System.Web.Routing.RouteTable> w pliku Global. asax. Te trasy określają względne identyfikatory URI, z którymi usługa reaguje. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 To kieruje wszystkie żądania z względnym identyfikatorem URI, który rozpoczyna się od klientów do usługi `Service`.  
  
 W pliku Web. config należy dodać moduł `System.Web.Routing.UrlRoutingModule`, ustawić atrybut `runAllManagedModulesForAllRequests` na `true`i dodać obsługę `UrlRoutingHandler` do elementu `<system.webServer>`, jak pokazano w poniższym przykładzie.  
  
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
  
 Spowoduje to załadowanie modułu i programu obsługi, który jest wymagany do routingu. Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md). Należy również ustawić atrybut `aspNetCompatibilityEnabled`, aby `true` w elemencie `<serviceHostingEnvironment>`, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Klasa implementująca usługę musi włączać wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.  
  
```csharp 
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Zobacz także

- [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [Routing ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
