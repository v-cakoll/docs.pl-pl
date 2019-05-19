---
title: 'Instrukcje: używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: f989252c7dd9b2ccdce8331e7cdd987042230ded
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880231"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Instrukcje: używanie dostawcy ról ASP.NET razem z usługą
Dostawcy ról ASP.NET (w połączeniu z dostawcy członkostwa platformy ASP.NET) to funkcja, która umożliwia deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta usługi z lokacją i mieć przypisane role na potrzeby autoryzacji programu ASP.NET. Dzięki tej funkcji każdy użytkownik może ustanowić konto w witrynie i logowania wyłącznego dostępu do lokacji i usług. Jest to w przeciwieństwie do zabezpieczeń Windows, która wymaga od użytkowników mają konta w domenie Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), można użyć witryny i jego usług.  
  
 Dla przykładowej aplikacji, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać więcej informacji na temat funkcji dostawcy członkostwa ASP.NET, zobacz [jak: Użycie dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Funkcja dostawcy roli używa bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Windows Communication Foundation (WCF) deweloperom korzystać z zalet tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu aplikacji WCF, użytkownicy muszą podać kombinacja nazwy i hasła użytkownika do aplikacji klienta programu WCF. Aby włączyć usługi WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustaw jego <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>i dodaj je do kolekcji zachowań <xref:System.ServiceModel.ServiceHost> , który jest hostem usługi.  
  
### <a name="to-configure-the-role-provider"></a>Aby skonfigurować dostawcę roli  
  
1. W pliku Web.config w obszarze <`system.web`> elementu Dodawanie <`roleManager`> element i ustaw jego `enabled` atrybutu `true`.  
  
2. Ustaw `defaultProvider` atrybutu `SqlRoleProvider`.  
  
3. Jako element podrzędny <`roleManager`> elementu Dodawanie <`providers`> element.  
  
4. Jako element podrzędny <`providers`> elementu Dodawanie <`add`> element z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, i `applicationName`, jak pokazano w poniższym przykładzie.  
  
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
  
### <a name="to-configure-the-service-to-use-the-role-provider"></a>Aby skonfigurować usługę Używanie dostawcy ról  
  
1. W pliku Web.config, Dodaj [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu <`system.ServiceModel`> element.  
  
3. Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> element.  
  
4. Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` atrybutu do odpowiedniej wartości.  
  
5. Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do <`behavior`> element.  
  
6. Ustaw `principalPermissionMode` atrybutu `UseAspNetRoles`.  
  
7. Ustaw `roleProviderName` atrybutu `SqlRoleProvider`. Poniższy przykład przedstawia fragment konfiguracji.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
