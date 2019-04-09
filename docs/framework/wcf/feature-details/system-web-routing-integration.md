---
title: Integracja elementu System.Web.Routing
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 3d5c3d7586189e0939fd52bc2b5feac51ae00613
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097515"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="9b39d-102">Integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="9b39d-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="9b39d-103">W przypadku hostowania usługi Windows Communication Foundation (WCF) w Internet Information Service (IIS) możesz umieścić plik .svc w katalogu wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="9b39d-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="9b39d-104">Ten plik .svc określa fabryki hostów usług do użycia oraz klasy, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="9b39d-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="9b39d-105">W przypadku wysyłania żądań do usługi można określić plików .svc w identyfikatorze URI, na przykład: `http://contoso.com/EmployeeServce.svc`.</span><span class="sxs-lookup"><span data-stu-id="9b39d-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="9b39d-106">Programistom pisanie usług REST tego rodzaju identyfikatora URI nie jest optymalne.</span><span class="sxs-lookup"><span data-stu-id="9b39d-106">For programmers writing REST services this type of URI is not optimal.</span></span> <span data-ttu-id="9b39d-107">Identyfikatory URI dla usługi REST Określ określonego zasobu i zwykle nie mają żadnych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="9b39d-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="9b39d-108"><xref:System.Web.Routing> Funkcji integracji umożliwia hostowanie usługi WCF REST reagującego na identyfikatory URI bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9b39d-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="9b39d-109">Aby uzyskać więcej informacji o routingu, zobacz [routingu ASP.NET](https://go.microsoft.com/fwlink/?LinkId=184660).</span><span class="sxs-lookup"><span data-stu-id="9b39d-109">For more information about routing see [ASP.NET Routing](https://go.microsoft.com/fwlink/?LinkId=184660).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="9b39d-110">Za pomocą integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="9b39d-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="9b39d-111">Aby użyć <xref:System.Web.Routing> używać funkcji integracji <xref:System.ServiceModel.Activation.ServiceRoute> klasy, aby utworzyć jeden lub więcej tras i dodać je do <xref:System.Web.Routing.RouteTable> w pliku Global.asax.</span><span class="sxs-lookup"><span data-stu-id="9b39d-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="9b39d-112">Te trasy Określ względne identyfikatory URI, które odpowiada usługa.</span><span class="sxs-lookup"><span data-stu-id="9b39d-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="9b39d-113">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="9b39d-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="9b39d-114">Kierowane wszystkie żądania z względny identyfikator URI rozpoczynający się ze swoimi klientami, aby `Service` usługi.</span><span class="sxs-lookup"><span data-stu-id="9b39d-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="9b39d-115">W pliku Web.config musisz dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawia `runAllManagedModulesForAllRequests` atrybutu `true`i Dodaj `UrlRoutingHandler` program obsługi `<system.webServer>` elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b39d-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="9b39d-116">Spowoduje to załadowanie modułu i obsługi wymagane do routingu.</span><span class="sxs-lookup"><span data-stu-id="9b39d-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="9b39d-117">Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="9b39d-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="9b39d-118">Należy także ustawić `aspNetCompatibilityEnabled` atrybutu `true` w `<serviceHostingEnvironment>` elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b39d-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="9b39d-119">Klasa, która implementuje usługę należy włączyć wymagania dotyczące zgodności platformy ASP.NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b39d-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```  
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b39d-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b39d-120">See also</span></span>

- [<span data-ttu-id="9b39d-121">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="9b39d-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="9b39d-122">Routingu platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9b39d-122">ASP.NET Routing</span></span>](https://go.microsoft.com/fwlink/?LinkId=184660)
