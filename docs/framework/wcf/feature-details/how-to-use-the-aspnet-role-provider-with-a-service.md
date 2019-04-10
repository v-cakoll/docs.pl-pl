---
title: 'Instrukcje: używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 20ffd1bb51bc2d6ac106927f805c7349c12059c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209089"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="980cf-102">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="980cf-102">How to: Use the ASP.NET Role Provider with a Service</span></span>
<span data-ttu-id="980cf-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy ról (w połączeniu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa) to funkcja, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta usługi z lokacją i mieć przypisane role, do autoryzacji do celów.</span><span class="sxs-lookup"><span data-stu-id="980cf-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider (in conjunction with the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider) is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="980cf-104">Dzięki tej funkcji każdy użytkownik może ustanowić konto w witrynie i logowania wyłącznego dostępu do lokacji i usług.</span><span class="sxs-lookup"><span data-stu-id="980cf-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="980cf-105">Jest to w przeciwieństwie do zabezpieczeń Windows, która wymaga od użytkowników mają konta w domenie Windows.</span><span class="sxs-lookup"><span data-stu-id="980cf-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="980cf-106">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), można użyć witryny i jego usług.</span><span class="sxs-lookup"><span data-stu-id="980cf-106">Instead, any user who supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="980cf-107">Dla przykładowej aplikacji, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="980cf-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="980cf-108">Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcję dostawcy członkostwa, zobacz [jak: Użycie dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="980cf-108">For more information about the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
 <span data-ttu-id="980cf-109">Funkcja dostawcy roli używa bazy danych programu SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="980cf-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="980cf-110">Windows Communication Foundation (WCF) deweloperom korzystać z zalet tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="980cf-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="980cf-111">Po zintegrowaniu aplikacji WCF, użytkownicy muszą podać kombinacja nazwy i hasła użytkownika do aplikacji klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="980cf-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="980cf-112">Aby włączyć usługi WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustaw jego <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>i dodaj je do kolekcji zachowań <xref:System.ServiceModel.ServiceHost> , który jest hostem usługi.</span><span class="sxs-lookup"><span data-stu-id="980cf-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
### <a name="to-configure-the-role-provider"></a><span data-ttu-id="980cf-113">Aby skonfigurować dostawcę roli</span><span class="sxs-lookup"><span data-stu-id="980cf-113">To configure the role provider</span></span>  
  
1.  <span data-ttu-id="980cf-114">W pliku Web.config w obszarze <`system.web`> elementu Dodawanie <`roleManager`> element i ustaw jego `enabled` atrybutu `true`.</span><span class="sxs-lookup"><span data-stu-id="980cf-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2.  <span data-ttu-id="980cf-115">Ustaw `defaultProvider` atrybutu `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="980cf-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3.  <span data-ttu-id="980cf-116">Jako element podrzędny <`roleManager`> elementu Dodawanie <`providers`> element.</span><span class="sxs-lookup"><span data-stu-id="980cf-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4.  <span data-ttu-id="980cf-117">Jako element podrzędny <`providers`> elementu Dodawanie <`add`> element z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, i `applicationName`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="980cf-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Role Provider. -->  
    <roleManager enabled ="true"   
     defaultProvider ="SqlRoleProvider" >  
       <providers>  
         <add name ="SqlRoleProvider"   
           type="System.Web.Security.SqlRoleProvider"   
           connectionStringName="SqlConn"   
           applicationName="MembershipAndRoleProviderSample"/>  
       </providers>  
    </roleManager>  
    ```  
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="980cf-118">Aby skonfigurować usługę Używanie dostawcy ról</span><span class="sxs-lookup"><span data-stu-id="980cf-118">To configure the service to use the role provider</span></span>  
  
1.  <span data-ttu-id="980cf-119">W pliku Web.config, Dodaj [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="980cf-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="980cf-120">Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu <`system.ServiceModel`> element.</span><span class="sxs-lookup"><span data-stu-id="980cf-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3.  <span data-ttu-id="980cf-121">Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="980cf-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4.  <span data-ttu-id="980cf-122">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="980cf-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5.  <span data-ttu-id="980cf-123">Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="980cf-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6.  <span data-ttu-id="980cf-124">Ustaw `principalPermissionMode` atrybutu `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="980cf-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7.  <span data-ttu-id="980cf-125">Ustaw `roleProviderName` atrybutu `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="980cf-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="980cf-126">Poniższy przykład przedstawia fragment konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="980cf-126">The following example shows a fragment of the configuration.</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
      <behavior name="CalculatorServiceBehavior">  
       <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                             roleProviderName ="SqlRoleProvider" />  
      </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="980cf-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="980cf-127">See also</span></span>

- [<span data-ttu-id="980cf-128">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="980cf-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="980cf-129">Instrukcje: używanie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="980cf-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
