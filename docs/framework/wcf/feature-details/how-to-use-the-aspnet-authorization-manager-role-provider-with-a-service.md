---
title: "Porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ee51a2fa4a4ec3de04e21fdbc070cd7619b43c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a><span data-ttu-id="69a39-102">Porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą</span><span class="sxs-lookup"><span data-stu-id="69a39-102">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>
<span data-ttu-id="69a39-103">Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] obsługuje usługi sieci Web do aplikacji w celu umożliwienia autoryzacji do usługi można zintegrować Menedżera autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="69a39-103">When [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hosts a Web service, you can integrate Authorization Manager into the application to provide authorization to the service.</span></span> <span data-ttu-id="69a39-104">Menedżer autoryzacji umożliwia Deweloper aplikacji określenie poszczególnych działań, które mogą zostać zgrupowane w celu zadania formularza.</span><span class="sxs-lookup"><span data-stu-id="69a39-104">Authorization Manager enables an application developer to define individual operations, which can be grouped together to form tasks.</span></span> <span data-ttu-id="69a39-105">Administrator może następnie Autoryzuj ról do wykonywania określonych zadań lub poszczególnych działań.</span><span class="sxs-lookup"><span data-stu-id="69a39-105">An administrator can then authorize roles to perform specific tasks or individual operations.</span></span> <span data-ttu-id="69a39-106">Menedżer autoryzacji zapewnia narzędzia do administrowania jako przystawki programu Microsoft Management Console (MMC) do zarządzania rolami, zadania, operacje i użytkowników.</span><span class="sxs-lookup"><span data-stu-id="69a39-106">Authorization Manager provides an administration tool as a Microsoft Management Console (MMC) snap-in to manage roles, tasks, operations, and users.</span></span> <span data-ttu-id="69a39-107">Administratorzy skonfigurować Magazyn zasad Menedżera autoryzacji w pliku XML, usługi Active Directory, lub w magazynie tryb aplikacji usługi Active Directory (ADAM).</span><span class="sxs-lookup"><span data-stu-id="69a39-107">Administrators configure an Authorization Manager policy store in an XML file, Active Directory, or in an Active Directory Application Mode (ADAM) store.</span></span>  
  
 <span data-ttu-id="69a39-108">Menedżer autoryzacji jest zintegrowany z aplikacji przez skonfigurowanie Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, który jest hostem usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="69a39-108">Authorization Manager is Integrated into the application by configuring the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider for the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is hosting the Web service.</span></span> <span data-ttu-id="69a39-109">Takich jak inne [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli, Menedżer autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli jest konfigurowana przy użyciu <`providers`> elementu.</span><span class="sxs-lookup"><span data-stu-id="69a39-109">Like other [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role providers, the Authorization Manager [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider is configured using the <`providers`> element.</span></span>  
  
 <span data-ttu-id="69a39-110">Poniższy przykładowy kod jest częścią pliku konfiguracji dla usługi sieci Web, która jest włączenie Menedżera autoryzacji do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="69a39-110">The following code example is a portion of a configuration file for a Web service that is integrating Authorization Manager into the application.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="69a39-111">Integrowanie [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, zobacz [porady: Używanie dostawcy ról ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="69a39-111"> integrating an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="69a39-112">za pomocą programu Menedżer autoryzacji z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [porady: Korzystanie z Menedżera autoryzacji (AzMan) z programem ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span><span class="sxs-lookup"><span data-stu-id="69a39-112"> using Authorization Manager with [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], see [How to: Use Authorization Manager (AzMan) with ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69a39-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69a39-113">See Also</span></span>  
 [<span data-ttu-id="69a39-114">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="69a39-114">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
