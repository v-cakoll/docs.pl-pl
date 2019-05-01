---
title: 'Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: ebdfa8bd7d222c4f9a33b6718b215d327d589c6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62047298"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi
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
  
 Aby uzyskać więcej informacji na temat integracji [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy ról za pomocą aplikacji WCF, zobacz [jak: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji za pomocą [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], zobacz [jak: Korzystanie z Menedżera autoryzacji (AzMan) za pomocą platformy ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
