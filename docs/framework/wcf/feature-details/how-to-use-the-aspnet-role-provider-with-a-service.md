---
title: 'Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 846caf59816ee23166fb382a0c36ac0fed9df151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy roli (łącznie z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa) to funkcja, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta usługi z lokacją i przypisać role do autoryzacji do celów. W przypadku tej funkcji każdy użytkownik może założyć konto w witrynie i logowania wyłącznego dostępu do lokacji i jej usługi. Dzięki temu nie trzeba zabezpieczenia systemu Windows, który wymaga od użytkowników mają konta w domenie systemu Windows. Zamiast tego użytkownik wprowadza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), można użyć lokacji i jej usługi.  
  
 Przykładową aplikację, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać więcej informacji na temat [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcji dostawcy członkostwa, zobacz [porady: Używanie dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
 Funkcja dostawcy roli używa bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Windows Communication Foundation (WCF) deweloperzy mogą wykorzystać te funkcje ze względów bezpieczeństwa. Po zintegrowaniu aplikacji WCF, użytkowników, musisz podać kombinacji nazwy i hasła użytkownika do aplikacji klienta WCF. Aby włączyć usługi WCF do użycia bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustaw jej <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwości <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>i dodaj je do kolekcji zachowań <xref:System.ServiceModel.ServiceHost> , który jest hostem usługi.  
  
### <a name="to-configure-the-role-provider"></a>Aby skonfigurować dostawcę roli  
  
1.  W pliku Web.config w obszarze <`system.web`> elementu, Dodaj <`roleManager`> element i ustaw jej `enabled` atrybutu `true`.  
  
2.  Ustaw `defaultProvider` atrybutu `SqlRoleProvider`.  
  
3.  Jako element podrzędny <`roleManager`> elementu, Dodaj <`providers`> elementu.  
  
4.  Jako element podrzędny <`providers`> elementu, Dodaj <`add`> elementu z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, i `applicationName`, jak pokazano w poniższym przykładzie.  
  
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
  
1.  W pliku Web.config, Dodaj [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2.  Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu <`system.ServiceModel`> elementu.  
  
3.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.  
  
4.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` atrybutu odpowiednią wartość.  
  
5.  Dodaj [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) do <`behavior`> elementu.  
  
6.  Ustaw `principalPermissionMode` atrybutu `UseAspNetRoles`.  
  
7.  Ustaw `roleProviderName` atrybutu `SqlRoleProvider`. W poniższym przykładzie przedstawiono fragment konfiguracji.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)  
 [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
