---
title: 'Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 009b96defdf27591ddb98afaa684745b5fcbe0d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184810"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="e75e3-102">Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi</span><span class="sxs-lookup"><span data-stu-id="e75e3-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="e75e3-103">Gdy ASP.NET hostuje usługę sieci Web, można zintegrować Menedżera autoryzacji z aplikacją w celu zapewnienia autoryzacji usługi.</span><span class="sxs-lookup"><span data-stu-id="e75e3-103">When ASP.NET hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="e75e3-104">Menedżer autoryzacji umożliwia deweloperowi aplikacji definiowanie poszczególnych operacji, które można zgrupować w celu utworzenia zadań.</span><span class="sxs-lookup"><span data-stu-id="e75e3-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="e75e3-105">Administrator może następnie autoryzować role do wykonywania określonych zadań lub poszczególnych operacji.</span><span class="sxs-lookup"><span data-stu-id="e75e3-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="e75e3-106">Menedżer autoryzacji udostępnia narzędzie administracyjne jako przystawkę programu Microsoft Management Console (MMC) do zarządzania rolami, zadaniami, operacjami i użytkownikami.</span><span class="sxs-lookup"><span data-stu-id="e75e3-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="e75e3-107">Administratorzy konfigurują magazyn zasad Menedżera autoryzacji w pliku XML, usłudze Active Directory lub w magazynie adamowym (Active Directory Application Mode).</span><span class="sxs-lookup"><span data-stu-id="e75e3-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="e75e3-108">Menedżer autoryzacji jest zintegrowany z aplikacją, konfigurując dostawcę roli Menedżera autoryzacji ASP.NET dla aplikacji ASP.NET obsługującej usługę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e75e3-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager ASP.NET role provider for the ASP.NET application that is hosting the Web service.</span></span> <span data-ttu-id="e75e3-109">Podobnie jak inni dostawcy ról ASP.NET, dostawca roli Menedżera autoryzacji ASP.NET jest skonfigurowany przy użyciu elementu `providers`> <.</span><span class="sxs-lookup"><span data-stu-id="e75e3-109">Like other ASP.NET role providers, the Authorization Manager ASP.NET role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="e75e3-110">Poniższy przykład kodu jest częścią pliku konfiguracyjnego dla usługi sieci Web, która integruje Menedżera autoryzacji z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="e75e3-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
```xml  
<system.web>  
    <roleManager enabled="true" defaultProvider="AzManRoleProvider">  
      <providers>  
        <add name="AzManRoleProvider"  
             type="System.Web.Security.AuthorizationStoreRoleProvider, System.Web, Version=2.0.0.0, Culture=neutral, publicKeyToken=b03f5f7f11d50a3a"  
             connectionStringName="AzManPolicyStoreConnectionString"
             applicationName="SecureService"/>  
      </providers>  
    </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="e75e3-111">Aby uzyskać więcej informacji na temat integrowania dostawcy roli ASP.NET z aplikacją WCF, zobacz [Jak: Korzystanie z dostawcy roli ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="e75e3-111">For more information about integrating an ASP.NET role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="e75e3-112">Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji z ASP.NET, zobacz [Jak: Użyj Menedżera autoryzacji (AzMan) z ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="e75e3-112">For more information about using Authorization Manager with ASP.NET, see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e75e3-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e75e3-113">See also</span></span>

- [<span data-ttu-id="e75e3-114">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="e75e3-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
