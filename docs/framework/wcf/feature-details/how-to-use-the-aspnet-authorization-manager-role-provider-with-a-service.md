---
title: 'Instrukcje: korzystanie z dostawcy roli Menedżera autoryzacji ASP.NET z usługą'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 20955578ce4d344c2057036c0944557edf737389
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212225"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Instrukcje: korzystanie z dostawcy roli Menedżera autoryzacji ASP.NET z usługą
Gdy usługa ASP.NET hostuje usługę sieci Web, można zintegrować Menedżera autoryzacji z aplikacją w celu zapewnienia autoryzacji usługi. Menedżer autoryzacji pozwala deweloperowi aplikacji definiować poszczególne operacje, które mogą być zgrupowane razem z zadaniami formularza. Administrator może następnie autoryzować role do wykonywania określonych zadań lub poszczególnych operacji. Menedżer autoryzacji udostępnia narzędzie administracyjne jako przystawkę programu Microsoft Management Console (MMC) do zarządzania rolami, zadaniami, operacjami i użytkownikami. Administratorzy konfigurują Magazyn zasad Menedżera autoryzacji w pliku XML, Active Directory lub w sklepie Active Directory Application Mode (ADAM).  
  
 Menedżer autoryzacji jest zintegrowany z aplikacją przez skonfigurowanie dostawcy roli ASP.NET Menedżera autoryzacji dla aplikacji ASP.NET, która obsługuje usługę sieci Web. Podobnie jak w przypadku innych dostawców ról ASP.NET, dostawca roli ASP.NET Menedżera autoryzacji jest konfigurowany przy użyciu <`providers`> elementu.  
  
 Poniższy przykład kodu jest częścią pliku konfiguracji usługi sieci Web, która integruje Menedżera autoryzacji z aplikacją.  
  
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
  
 Aby uzyskać więcej informacji na temat integrowania dostawcy roli ASP.NET z aplikacją WCF, zobacz [How to: Use the ASP.NET role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji o korzystaniu z Menedżera autoryzacji z ASP.NET, zobacz [How to: use Menedżer autoryzacji (AzMan) z ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
