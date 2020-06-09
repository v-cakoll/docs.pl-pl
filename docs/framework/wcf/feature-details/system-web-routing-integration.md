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
# <a name="systemwebrouting-integration"></a><span data-ttu-id="301a1-102">Integracja elementu System.Web.Routing</span><span class="sxs-lookup"><span data-stu-id="301a1-102">System.Web.Routing Integration</span></span>
<span data-ttu-id="301a1-103">W przypadku hostowania usługi Windows Communication Foundation (WCF) w usłudze Internet Information Service (IIS) Umieść plik. svc w katalogu wirtualnym.</span><span class="sxs-lookup"><span data-stu-id="301a1-103">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="301a1-104">Ten plik SVC określa fabrykę hosta usługi, która ma być używana, a także klasy implementującej usługę.</span><span class="sxs-lookup"><span data-stu-id="301a1-104">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="301a1-105">Podczas wykonywania żądań do usługi należy określić plik SVC w identyfikatorze URI, na przykład: `http://contoso.com/EmployeeServce.svc` .</span><span class="sxs-lookup"><span data-stu-id="301a1-105">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="301a1-106">Dla programistów piszące usługi REST ten typ URI nie jest optymalny.</span><span class="sxs-lookup"><span data-stu-id="301a1-106">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="301a1-107">Identyfikatory URI usług REST określają konkretny zasób i zwykle nie mają żadnych rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="301a1-107">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="301a1-108"><xref:System.Web.Routing>Funkcja integracji umożliwia Hostowanie usługi REST WCF, która reaguje na identyfikatory URI bez rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="301a1-108">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="301a1-109">Aby uzyskać więcej informacji na temat routingu, zobacz [ASP.NET routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="301a1-109">For more information about routing see [ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="301a1-110">Korzystanie z integracji system. Web. Routing</span><span class="sxs-lookup"><span data-stu-id="301a1-110">Using System.Web.Routing Integration</span></span>  
 <span data-ttu-id="301a1-111">Aby użyć <xref:System.Web.Routing> funkcji integracji, należy użyć klasy w <xref:System.ServiceModel.Activation.ServiceRoute> celu utworzenia jednej lub więcej tras i dodania ich do <xref:System.Web.Routing.RouteTable> pliku Global. asax.</span><span class="sxs-lookup"><span data-stu-id="301a1-111">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="301a1-112">Te trasy określają względne identyfikatory URI, z którymi usługa reaguje.</span><span class="sxs-lookup"><span data-stu-id="301a1-112">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="301a1-113">W przykładzie poniżej pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="301a1-113">The following example shows how to do this.</span></span>  
  
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
  
 <span data-ttu-id="301a1-114">To kieruje wszystkie żądania z względnym identyfikatorem URI, który zaczyna się od klientów do `Service` usługi.</span><span class="sxs-lookup"><span data-stu-id="301a1-114">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="301a1-115">W pliku Web. config należy dodać `System.Web.Routing.UrlRoutingModule` moduł, ustawić `runAllManagedModulesForAllRequests` atrybut na `true` i dodać `UrlRoutingHandler` program obsługi do `<system.webServer>` elementu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="301a1-115">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="301a1-116">Spowoduje to załadowanie modułu i programu obsługi, który jest wymagany do routingu.</span><span class="sxs-lookup"><span data-stu-id="301a1-116">This loads a module and handler required for routing.</span></span> <span data-ttu-id="301a1-117">Aby uzyskać więcej informacji, zobacz [Routing](routing.md).</span><span class="sxs-lookup"><span data-stu-id="301a1-117">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="301a1-118">Należy również ustawić `aspNetCompatibilityEnabled` atrybut na `true` w `<serviceHostingEnvironment>` elemencie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="301a1-118">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="301a1-119">Klasa implementująca usługę musi włączać wymagania dotyczące zgodności ASP.NET, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="301a1-119">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="301a1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="301a1-120">See also</span></span>

- [<span data-ttu-id="301a1-121">Model programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="301a1-121">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="301a1-122">[Routing ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="301a1-122">[ASP.NET Routing](https://docs.microsoft.com/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
