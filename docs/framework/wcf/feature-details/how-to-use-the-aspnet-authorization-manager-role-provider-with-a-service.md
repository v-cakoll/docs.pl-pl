---
title: 'Porady: Używanie dostawcy roli Menedżera autoryzacji platformy ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: c21c1a80468bd81f2df69009afd2be86ee714250
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43386709"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Porady: Używanie dostawcy roli Menedżera autoryzacji platformy ASP.NET razem z usługą
Gdy [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hostuje usługi sieci Web, możesz zintegrować Menedżera autoryzacji aplikacji w celu umożliwienia autoryzacji w usłudze. Menedżer autoryzacji umożliwia pracę deweloperowi aplikacji do definiowania poszczególnych działań, które mogą być zgrupowane razem do formularza zadania. Administrator może następnie autoryzować ról do wykonywania określonych zadań lub poszczególnych operacji. Menedżer autoryzacji oferuje narzędzie administracyjne jako przystawkę Microsoft Management Console (MMC) do zarządzania rolami, zadania, operacje i użytkowników. Administratorzy skonfigurować Magazyn zasad Menedżera autoryzacji w pliku XML, usługi Active Directory, lub w magazynie tryb aplikacji usługi Active Directory (ADAM).  
  
 Menedżer autoryzacji jest zintegrowana aplikacja, konfigurując Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról dla [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji, który jest hostem usługi sieci Web. Jak inne [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy roli Menedżera autoryzacji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról jest konfigurowana przy użyciu <`providers`> element.  
  
 Poniższy przykład kodu jest częścią pliku konfiguracji usługi sieci Web, która jest integracja Menedżera autoryzacji do aplikacji.  
  
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
  
 Aby uzyskać więcej informacji na temat integracji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról za pomocą aplikacji WCF, zobacz [porady: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji za pomocą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [porady: Korzystanie z Menedżera autoryzacji (AzMan) za pomocą programu ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
