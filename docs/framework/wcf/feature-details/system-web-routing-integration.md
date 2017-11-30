---
title: Integracja elementu System.Web.Routing
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d1c1493e344bfe60a12ad16e3c0d257392b3545a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemwebrouting-integration"></a>Integracja elementu System.Web.Routing
Odnośnie do hostowania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] w Internetowych usług informacyjnych (IIS), umieść plików .svc w katalogu wirtualnym. Ten plik .svc określa fabryki hostów usług do użycia oraz klasy, który implementuje usługę. W przypadku wysyłania żądań do usługi można określić w pliku svc w identyfikatorze URI, na przykład: http://contoso.com/EmployeeServce.svc. Dla programistów pisanie usług REST ten typ identyfikatora URI nie jest optymalna. Identyfikatory URI dla usługi REST Określ określonego zasobu i zazwyczaj nie zainstalowano rozszerzeń. <xref:System.Web.Routing> Funkcji integracji umożliwia hostowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi REST, który odpowiada na identyfikatory URI bez rozszerzenia. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zobacz routingu [routingu platformy ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) i [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) próbki.  
  
## <a name="using-systemwebrouting-integration"></a>Przy użyciu integracja elementu System.Web.Routing  
 Aby użyć <xref:System.Web.Routing> używać funkcji integracji <xref:System.ServiceModel.Activation.ServiceRoute> klasę, aby utworzyć co najmniej jednej trasy i dodaj je do <xref:System.Web.Routing.RouteTable> w pliku Global.asax. Te trasy określić względne identyfikatory URI, które odpowiada usługi. W przykładzie poniżej pokazano, jak to zrobić.  
  
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
  
 To kieruje wszystkie żądania z względny identyfikator URI, który rozpoczyna się z klientami w celu `Service` usługi.  
  
 W pliku Web.config musisz dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawia `runAllManagedModulesForAllRequests` atrybutu `true`i Dodaj `UrlRoutingHandler` program obsługi `<system.webServer>` element, jak pokazano w poniższym przykładzie.  
  
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
  
 Spowoduje to załadowanie modułu i obsługi wymaganych dla routingu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Routingu](../../../../docs/framework/wcf/feature-details/routing.md). Należy także ustawić `aspNetCompatibilityEnabled` atrybutu `true` w `<serviceHostingEnvironment>` element, jak pokazano w poniższym przykładzie.  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 Klasa, która implementuje usługę należy włączyć wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Proces routingu platformy ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660)
