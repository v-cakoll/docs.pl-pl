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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="3ec3f-102">Integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="3ec3f-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="3ec3f-103">Podczas hostowania usługi Windows Communication Foundation (WCF) w internetowej usłudze informacyjnej (IIS) umieszczasz plik .svc w katalogu wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="3ec3f-104">Ten plik .svc określa fabrykę hosta usługi do użycia, a także klasę, która implementuje usługę.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="3ec3f-105">Podczas składania żądań do usługi można określić plik .svc `http://contoso.com/EmployeeServce.svc`w identyfikatorze URI, na przykład: .</span><span class="sxs-lookup"><span data-stu-id="3ec3f-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="3ec3f-106">Dla programistów piszących usługi REST ten typ identyfikatora URI nie jest optymalny.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="3ec3f-107">Identyfikatory URI dla usług REST określają określony zasób i zwykle nie mają żadnych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="3ec3f-108">Funkcja <xref:System.Web.Routing> integracji umożliwia hostowania usługi WCF REST, która odpowiada na identyfikatory URI bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="3ec3f-109">Aby uzyskać więcej informacji na temat routingu, zobacz [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ec3f-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="3ec3f-110">Korzystanie z integracji z usługą System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="3ec3f-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="3ec3f-111">Aby użyć <xref:System.Web.Routing> funkcji integracji, <xref:System.ServiceModel.Activation.ServiceRoute> należy użyć klasy, aby utworzyć <xref:System.Web.Routing.RouteTable> jedną lub więcej tras i dodać je do pliku Global.asax.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="3ec3f-112">Te trasy określają względne identyfikatory URI, na które usługa odpowiada.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="3ec3f-113">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="3ec3f-114">To kieruje wszystkie żądania z względnym identyfikatorem `Service` URI, który rozpoczyna się od klientów do usługi.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="3ec3f-115">W pliku Web.config należy `System.Web.Routing.UrlRoutingModule` dodać moduł, `runAllManagedModulesForAllRequests` ustawić `true`atrybut do `UrlRoutingHandler` programu , `<system.webServer>` i dodać program obsługi do elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="3ec3f-116">To ładuje moduł i program obsługi wymagane do routingu.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="3ec3f-117">Aby uzyskać więcej informacji, zobacz [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span><span class="sxs-lookup"><span data-stu-id="3ec3f-117">For more information, see [Routing](../../../../docs/framework/wcf/feature-details/routing.md).</span></span> <span data-ttu-id="3ec3f-118">Należy również ustawić `aspNetCompatibilityEnabled` atrybut `true` w `<serviceHostingEnvironment>` elemencie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="3ec3f-119">Klasa, która implementuje usługę, musi włączyć wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3ec3f-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ec3f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ec3f-120">See also</span></span>

- [<span data-ttu-id="3ec3f-121">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="3ec3f-121">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
- <span data-ttu-id="3ec3f-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="3ec3f-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
