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
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi
Gdy ASP.NET hostuje usługę sieci Web, można zintegrować Menedżera autoryzacji z aplikacją w celu zapewnienia autoryzacji usługi. Menedżer autoryzacji umożliwia deweloperowi aplikacji definiowanie poszczególnych operacji, które można zgrupować w celu utworzenia zadań. Administrator może następnie autoryzować role do wykonywania określonych zadań lub poszczególnych operacji. Menedżer autoryzacji udostępnia narzędzie administracyjne jako przystawkę programu Microsoft Management Console (MMC) do zarządzania rolami, zadaniami, operacjami i użytkownikami. Administratorzy konfigurują magazyn zasad Menedżera autoryzacji w pliku XML, usłudze Active Directory lub w magazynie adamowym (Active Directory Application Mode).  
  
 Menedżer autoryzacji jest zintegrowany z aplikacją, konfigurując dostawcę roli Menedżera autoryzacji ASP.NET dla aplikacji ASP.NET obsługującej usługę sieci Web. Podobnie jak inni dostawcy ról ASP.NET, dostawca roli Menedżera autoryzacji ASP.NET jest skonfigurowany przy użyciu elementu `providers`> <.  
  
 Poniższy przykład kodu jest częścią pliku konfiguracyjnego dla usługi sieci Web, która integruje Menedżera autoryzacji z aplikacją.  
  
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
  
 Aby uzyskać więcej informacji na temat integrowania dostawcy roli ASP.NET z aplikacją WCF, zobacz [Jak: Korzystanie z dostawcy roli ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji z ASP.NET, zobacz [Jak: Użyj Menedżera autoryzacji (AzMan) z ASP.NET 2.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Zobacz też

- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
