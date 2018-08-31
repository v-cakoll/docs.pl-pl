---
title: 'Porady: Używanie dostawcy roli Menedżera autoryzacji platformy ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331712"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="f047a-102">Porady: Używanie dostawcy roli Menedżera autoryzacji platformy ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="f047a-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="f047a-103">Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje usługi sieci Web, możesz zintegrować Menedżera autoryzacji aplikacji w celu umożliwienia autoryzacji w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f047a-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="f047a-104">Menedżer autoryzacji umożliwia pracę deweloperowi aplikacji do definiowania poszczególnych działań, które mogą być zgrupowane razem do formularza zadania.</span><span class="sxs-lookup"><span data-stu-id="f047a-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="f047a-105">Administrator może następnie autoryzować ról do wykonywania określonych zadań lub poszczególnych operacji.</span><span class="sxs-lookup"><span data-stu-id="f047a-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="f047a-106">Menedżer autoryzacji oferuje narzędzie administracyjne jako przystawkę Microsoft Management Console (MMC) do zarządzania rolami, zadania, operacje i użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f047a-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="f047a-107">Administratorzy skonfigurować Magazyn zasad Menedżera autoryzacji w pliku XML, usługi Active Directory, lub w magazynie tryb aplikacji usługi Active Directory (ADAM).</span><span class="sxs-lookup"><span data-stu-id="f047a-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="f047a-108">Menedżer autoryzacji jest zintegrowana aplikacja, konfigurując Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, który jest hostem usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f047a-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="f047a-109">Jak inne [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról jest konfigurowana przy użyciu <`providers`> element.</span><span class="sxs-lookup"><span data-stu-id="f047a-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="f047a-110">Poniższy przykład kodu jest częścią pliku konfiguracji usługi sieci Web, która jest integracja Menedżera autoryzacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f047a-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 <span data-ttu-id="f047a-111">Aby uzyskać więcej informacji na temat integracji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról za pomocą aplikacji WCF, zobacz [porady: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="f047a-111">For more information about integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a WCF application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> <span data-ttu-id="f047a-112">Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji za pomocą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [porady: Korzystanie z Menedżera autoryzacji (AzMan) za pomocą programu ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="f047a-112">For more information about using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f047a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f047a-113">See Also</span></span>  
 [<span data-ttu-id="f047a-114">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="f047a-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
