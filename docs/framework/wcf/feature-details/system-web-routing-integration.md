---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 059f14c94bb7502a2e4f4616ca2c5e6ac5273afa
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600740"
---
# <a name="systemwebrouting-integration"></a>Integracja elementu System.Web.Routing
W przypadku hostowania usługi Windows Communication Foundation (WCF) w usłudze Internet Information Service (IIS) Umieść plik. svc w katalogu wirtualnym. Ten plik SVC określa fabrykę hosta usługi, która ma być używana, a także klasy implementującej usługę. Podczas wykonywania żądań do usługi należy określić plik SVC w identyfikatorze URI, na przykład: `http://contoso.com/EmployeeServce.svc` . Dla programistów piszące usługi REST ten typ URI nie jest optymalny. Identyfikatory URI usług REST określają konkretny zasób i zwykle nie mają żadnych rozszerzeń. <xref:System.Web.Routing>Funkcja integracji umożliwia Hostowanie usługi REST WCF, która reaguje na identyfikatory URI bez rozszerzenia. Aby uzyskać więcej informacji na temat routingu, zobacz [ASP.NET routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).  
  
## <a name="using-systemwebrouting-integration"></a>Korzystanie z integracji system. Web. Routing  
 Aby użyć <xref:System.Web.Routing> funkcji integracji, należy użyć klasy w <xref:System.ServiceModel.Activation.ServiceRoute> celu utworzenia jednej lub więcej tras i dodania ich do <xref:System.Web.Routing.RouteTable> pliku Global. asax. Te trasy określają względne identyfikatory URI, z którymi usługa reaguje. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 To kieruje wszystkie żądania z względnym identyfikatorem URI, który zaczyna się od klientów do `Service` usługi.  
  
 W pliku Web. config należy dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawić `runAllManagedModulesForAllRequests` atrybut na `true` i dodać `UrlRoutingHandler` program obsługi do `<system.webServer>` elementu, jak pokazano w poniższym przykładzie.  
  
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
  
 Spowoduje to załadowanie modułu i programu obsługi, który jest wymagany do routingu. Aby uzyskać więcej informacji, zobacz [Routing](routing.md). Należy również ustawić `aspNetCompatibilityEnabled` atrybut na `true` w `<serviceHostingEnvironment>` elemencie, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Model programowania protokołu HTTP sieci Web w programie WCF](wcf-web-http-programming-model.md)
- [Routing ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))
