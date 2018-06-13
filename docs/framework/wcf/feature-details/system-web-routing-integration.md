---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 5bd405d66dcad597bbe6f452703d25372fdb7682
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498026"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="f4e90-102">Integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="f4e90-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="f4e90-103">Odnośnie do hostowania usługi Windows Communication Foundation (WCF) w Internet Information Service (IIS) należy umieścić plik .svc w katalogu wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="f4e90-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="f4e90-104">Ten plik .svc określa fabryki hostów usług do użycia oraz klasy, który implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="f4e90-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="f4e90-105">W przypadku wysyłania żądań do usługi można określić w pliku svc w identyfikatorze URI, na przykład: http://contoso.com/EmployeeServce.svc.</span><span class="sxs-lookup"><span data-stu-id="f4e90-105">When making requests to the service you specify the .svc file in the URI, for example: http://contoso.com/EmployeeServce.svc.</span></span> <span data-ttu-id="f4e90-106">Dla programistów pisanie usług REST ten typ identyfikatora URI nie jest optymalna.</span><span class="sxs-lookup"><span data-stu-id="f4e90-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="f4e90-107">Identyfikatory URI dla usługi REST Określ określonego zasobu i zazwyczaj nie zainstalowano rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="f4e90-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="f4e90-108"><xref:System.Web.Routing> Funkcji integracji umożliwia hostowanie usługi WCF REST, która odpowiada na identyfikatory URI bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f4e90-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="f4e90-109">Aby uzyskać więcej informacji o routingu, zobacz [routingu platformy ASP.NET](http://go.microsoft.com/fwlink/?LinkId=184660) i [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="f4e90-109">For more information about routing see [ASP.NET Routing](http://go.microsoft.com/fwlink/?LinkId=184660) and the [AspNetRouteIntegration](../../../../docs/framework/wcf/samples/aspnetrouteintegration.md) sample.</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="f4e90-110">Przy użyciu integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="f4e90-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="f4e90-111">Aby użyć <xref:System.Web.Routing> używać funkcji integracji <xref:System.ServiceModel.Activation.ServiceRoute> klasę, aby utworzyć co najmniej jednej trasy i dodaj je do <xref:System.Web.Routing.RouteTable> w pliku Global.asax.</span><span class="sxs-lookup"><span data-stu-id="f4e90-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="f4e90-112">Te trasy określić względne identyfikatory URI, które odpowiada usługi.</span><span class="sxs-lookup"><span data-stu-id="f4e90-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="f4e90-113">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="f4e90-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="f4e90-114">To kieruje wszystkie żądania z względny identyfikator URI, który rozpoczyna się z klientami w celu `Service` usługi.</span><span class="sxs-lookup"><span data-stu-id="f4e90-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="f4e90-115">W pliku Web.config musisz dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawia `runAllManagedModulesForAllRequests` atrybutu `true`i Dodaj `UrlRoutingHandler` program obsługi `<system.webServer>` element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4e90-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f4e90-116">Spowoduje to załadowanie modułu i obsługi wymaganych dla routingu.</span><span class="sxs-lookup"><span data-stu-id="f4e90-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="f4e90-117">Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="f4e90-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="f4e90-118">Należy także ustawić `aspNetCompatibilityEnabled` atrybutu `true` w `<serviceHostingEnvironment>` element, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4e90-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="f4e90-119">Klasa, która implementuje usługę należy włączyć wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f4e90-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="f4e90-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4e90-120">See Also</span></span>  
 [<span data-ttu-id="f4e90-121">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="f4e90-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="f4e90-122">Proces routingu platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f4e90-122">ASP.NET Routing</span></span>](http://go.microsoft.com/fwlink/?LinkId=184660)
