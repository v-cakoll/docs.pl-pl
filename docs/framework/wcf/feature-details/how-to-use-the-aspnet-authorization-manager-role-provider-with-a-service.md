---
title: 'Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi'
ms.date: 03/30/2017
ms.assetid: f21deb81-91ef-49ef-94d6-494785143271
ms.openlocfilehash: 778af929b4cfc96ce0683d304be5f8fb87a0e47b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880202"
---
# <a name="how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service"></a>Instrukcje: używanie dostawcy roli menedżera autoryzacji platformy ASP.NET za pomocą usługi
Gdy program ASP.NET udostępnia usługi sieci Web, można zintegrować Menedżera autoryzacji aplikacji w celu umożliwienia autoryzacji w usłudze. Menedżer autoryzacji umożliwia pracę deweloperowi aplikacji do definiowania poszczególnych działań, które mogą być zgrupowane razem do formularza zadania. Administrator może następnie autoryzować ról do wykonywania określonych zadań lub poszczególnych operacji. Menedżer autoryzacji oferuje narzędzie administracyjne jako przystawkę Microsoft Management Console (MMC) do zarządzania rolami, zadania, operacje i użytkowników. Administratorzy skonfigurować Magazyn zasad Menedżera autoryzacji w pliku XML, usługi Active Directory, lub w magazynie tryb aplikacji usługi Active Directory (ADAM).  
  
 Menedżer autoryzacji jest zintegrowana aplikacja, konfigurując dostawcy roli Menedżera autoryzacji platformy ASP.NET dla aplikacji ASP.NET, który jest hostem usługi sieci Web. Podobnie jak inne dostawców ról ASP.NET dostawcy roli Menedżera autoryzacji platformy ASP.NET jest konfigurowana przy użyciu <`providers`> element.  
  
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
  
 Aby uzyskać więcej informacji na temat integracji dostawcy ról ASP.NET z aplikacji WCF zobacz [jak: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md). Aby uzyskać więcej informacji na temat korzystania z Menedżera autoryzacji programu ASP.NET, zobacz [jak: Korzystanie z Menedżera autoryzacji (AzMan) za pomocą platformy ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=71303).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
