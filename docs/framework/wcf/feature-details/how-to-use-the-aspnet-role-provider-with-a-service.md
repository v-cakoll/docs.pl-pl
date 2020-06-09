---
title: 'Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595300"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a><span data-ttu-id="603b1-102">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="603b1-102">How to: Use the ASP.NET Role Provider with a Service</span></span>

<span data-ttu-id="603b1-103">Dostawca roli ASP.NET (w połączeniu z dostawcą członkostwa ASP.NET) to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta w lokacji i przypisywanie ról do celów autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="603b1-103">The ASP.NET role provider (in conjunction with the ASP.NET membership provider) is a feature that enables ASP.NET developers to create Web sites that allow users to create an account with a site and to be assigned roles for authorization purposes.</span></span> <span data-ttu-id="603b1-104">Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z lokacją i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług.</span><span class="sxs-lookup"><span data-stu-id="603b1-104">With this feature, any user can establish an account with the site, and log in for exclusive access to the site and its services.</span></span> <span data-ttu-id="603b1-105">Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="603b1-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="603b1-106">Zamiast tego każdy użytkownik, który poda poświadczenia (kombinacja nazwy użytkownika/hasła), może korzystać z witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="603b1-106">Instead, any user who supplies their credentials (the user name/password combination) can use the site and its services.</span></span>  
  
<span data-ttu-id="603b1-107">Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="603b1-107">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="603b1-108">Aby uzyskać więcej informacji na temat funkcji ASP.NET Membership Provider, zobacz [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span><span class="sxs-lookup"><span data-stu-id="603b1-108">For more information about the ASP.NET membership provider feature, see [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).</span></span>  
  
<span data-ttu-id="603b1-109">Funkcja dostawcy roli używa bazy danych SQL Server do przechowywania informacji o użytkownikach.</span><span class="sxs-lookup"><span data-stu-id="603b1-109">The role provider feature uses a SQL Server database to store user information.</span></span> <span data-ttu-id="603b1-110">Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="603b1-110">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="603b1-111">Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="603b1-111">When integrated into a WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="603b1-112">Aby włączyć funkcję WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustawić jej <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> Właściwość na <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> , a następnie dodać wystąpienie do kolekcji zachowań <xref:System.ServiceModel.ServiceHost> , które obsługują usługę.</span><span class="sxs-lookup"><span data-stu-id="603b1-112">To enable WCF to use the database, you must create an instance of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> class, set its <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> property to <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>, and add the instance to the collection of behaviors to the <xref:System.ServiceModel.ServiceHost> that is hosting the service.</span></span>  
  
## <a name="configure-the-role-provider"></a><span data-ttu-id="603b1-113">Konfigurowanie dostawcy roli</span><span class="sxs-lookup"><span data-stu-id="603b1-113">Configure the role provider</span></span>  
  
1. <span data-ttu-id="603b1-114">W pliku Web. config w obszarze < `system.web` > Dodaj `roleManager` element < > i ustaw jego `enabled` atrybut na `true` .</span><span class="sxs-lookup"><span data-stu-id="603b1-114">In the Web.config file, under the <`system.web`> element, add a <`roleManager`> element and set its `enabled` attribute to `true`.</span></span>  
  
2. <span data-ttu-id="603b1-115">Ustaw `defaultProvider` atrybut na `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="603b1-115">Set the `defaultProvider` attribute to `SqlRoleProvider`.</span></span>  
  
3. <span data-ttu-id="603b1-116">Jako element podrzędny do <`roleManager`>, dodaj <`providers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="603b1-116">As a child to the <`roleManager`> element, add a <`providers`> element.</span></span>  
  
4. <span data-ttu-id="603b1-117">Jako element podrzędny do <`providers`>, Dodaj <`add` elementu> z następującymi atrybutami ustawionymi na odpowiednie wartości: `name` , `type` , `connectionStringName` , i `applicationName` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="603b1-117">As a child to the <`providers`> element, add an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, and `applicationName`, as shown in the following example.</span></span>  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a><span data-ttu-id="603b1-118">Konfigurowanie usługi do korzystania z dostawcy roli</span><span class="sxs-lookup"><span data-stu-id="603b1-118">Configure the service to use the role provider</span></span>  
  
1. <span data-ttu-id="603b1-119">W pliku Web. config Dodaj [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span><span class="sxs-lookup"><span data-stu-id="603b1-119">In the Web.config file, add a [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="603b1-120">Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element do `system.ServiceModel` elementu> <.</span><span class="sxs-lookup"><span data-stu-id="603b1-120">Add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element to the <`system.ServiceModel`> element.</span></span>  
  
3. <span data-ttu-id="603b1-121">Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` elementu> <.</span><span class="sxs-lookup"><span data-stu-id="603b1-121">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
4. <span data-ttu-id="603b1-122">Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="603b1-122">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
5. <span data-ttu-id="603b1-123">Dodaj [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) do `behavior` elementu> <.</span><span class="sxs-lookup"><span data-stu-id="603b1-123">Add a [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to the <`behavior`> element.</span></span>  
  
6. <span data-ttu-id="603b1-124">Ustaw `principalPermissionMode` atrybut na `UseAspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="603b1-124">Set the `principalPermissionMode` attribute to `UseAspNetRoles`.</span></span>  
  
7. <span data-ttu-id="603b1-125">Ustaw `roleProviderName` atrybut na `SqlRoleProvider` .</span><span class="sxs-lookup"><span data-stu-id="603b1-125">Set the `roleProviderName` attribute to `SqlRoleProvider`.</span></span> <span data-ttu-id="603b1-126">Poniższy przykład przedstawia fragment konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="603b1-126">The following example shows a fragment of the configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="603b1-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="603b1-127">See also</span></span>

- [<span data-ttu-id="603b1-128">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="603b1-128">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
- [<span data-ttu-id="603b1-129">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="603b1-129">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
