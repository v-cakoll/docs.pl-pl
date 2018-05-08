---
title: 'Porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 39103e86090ed57354efaf9c410a2733a58f06bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Porady: Używanie dostawcy ról ASP.NET Menedżera autoryzacji z usługą
Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] obsługuje usługi sieci Web do aplikacji w celu umożliwienia autoryzacji do usługi można zintegrować Menedżera autoryzacji. Menedżer autoryzacji umożliwia Deweloper aplikacji określenie poszczególnych działań, które mogą zostać zgrupowane w celu zadania formularza. Administrator może następnie Autoryzuj ról do wykonywania określonych zadań lub poszczególnych działań. Menedżer autoryzacji zapewnia narzędzia do administrowania jako przystawki programu Microsoft Management Console (MMC) do zarządzania rolami, zadania, operacje i użytkowników. Administratorzy skonfigurować Magazyn zasad Menedżera autoryzacji w pliku XML, usługi Active Directory, lub w magazynie tryb aplikacji usługi Active Directory (ADAM).  
  
 Menedżer autoryzacji jest zintegrowany z aplikacji przez skonfigurowanie Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, który jest hostem usługi sieci Web. Takich jak inne [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli, Menedżer autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli jest konfigurowana przy użyciu <`providers`> elementu.  
  
 Poniższy przykładowy kod jest częścią pliku konfiguracji dla usługi sieci Web, która jest włączenie Menedżera autoryzacji do aplikacji.  
  
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
  
 Aby uzyskać więcej informacji na temat integracji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli z aplikacją usługi WCF, zobacz [porady: Używanie dostawcy ról ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [porady: Korzystanie z Menedżera autoryzacji (AzMan) z programem ASP.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
