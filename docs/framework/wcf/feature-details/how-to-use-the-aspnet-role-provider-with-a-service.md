---
title: 'Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184768"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="09178-102">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="09178-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="09178-103">Dostawca roli ASP.NET (w połączeniu z dostawcą członkostwa ASP.NET) jest funkcją, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta w witrynie i przypisywanie ról do celów autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="09178-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="09178-104">Dzięki tej funkcji każdy użytkownik może założyć konto w witrynie i zalogować się, aby uzyskać wyłączny dostęp do witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="09178-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="09178-105">Jest to w przeciwieństwie do zabezpieczeń systemu Windows, który wymaga od użytkowników, aby mieć konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="09178-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="09178-106">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwa użytkownika/hasło) może korzystać z witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="09178-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="09178-107">Aby zapoznać się z przykładową aplikacją, zobacz [Członkostwo i Dostawca roli](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="09178-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="09178-108">Aby uzyskać więcej informacji na temat funkcji dostawcy członkostwa ASP.NET, zobacz [Jak: Korzystanie z ASP.NET Dostawcy członkostwa](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="09178-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="09178-109">Funkcja dostawcy roli używa bazy danych programu SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="09178-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="09178-110">Deweloperzy programu Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="09178-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="09178-111">Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika/hasła do aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="09178-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="09178-112">Aby włączyć WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustawić jego <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwość , <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>i dodać wystąpienie do kolekcji zachowań do <xref:System.ServiceModel.ServiceHost> usługi, która jest hostująca usługę.</span><span class="sxs-lookup"><span data-stu-id="09178-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="09178-113">Konfigurowanie dostawcy roli</span><span class="sxs-lookup"><span data-stu-id="09178-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="09178-114">W pliku Web.config w obszarze <`system.web`> element dodaj element `roleManager` <> i ustaw jego `enabled` atrybut na `true`.</span><span class="sxs-lookup"><span data-stu-id="09178-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="09178-115">Ustaw `defaultProvider` atrybut na `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="09178-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="09178-116">Jako element podrzędny <`roleManager`> dodaj element `providers` <>.</span><span class="sxs-lookup"><span data-stu-id="09178-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="09178-117">Jako element podrzędny do `providers` <> element dodaj `add` <> element z następującymi atrybutami ustawionymi `name` `type`na odpowiednie wartości: , , `connectionStringName`i `applicationName`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09178-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="09178-118">Konfigurowanie usługi do korzystania z dostawcy roli</span><span class="sxs-lookup"><span data-stu-id="09178-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="09178-119">W pliku Web.config dodaj element [ \<system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="09178-119">In the Web.config file, add a [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="09178-120">Dodaj element [ \<>zachowań](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) do elementu `system.ServiceModel` <>.</span><span class="sxs-lookup"><span data-stu-id="09178-120">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="09178-121">Dodaj [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.</span><span class="sxs-lookup"><span data-stu-id="09178-121">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="09178-122">Dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` atrybut na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="09178-122">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="09178-123">Dodaj [ \<>>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) `behavior`> <.</span><span class="sxs-lookup"><span data-stu-id="09178-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="09178-124">Ustaw `principalPermissionMode` atrybut na `UseAspNetRoles`.</span><span class="sxs-lookup"><span data-stu-id="09178-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="09178-125">Ustaw `roleProviderName` atrybut na `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="09178-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="09178-126">W poniższym przykładzie przedstawiono fragment konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09178-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="09178-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09178-127">See also</span></span>

- [<span data-ttu-id="09178-128">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="09178-128">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [<span data-ttu-id="09178-129">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="09178-129">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
