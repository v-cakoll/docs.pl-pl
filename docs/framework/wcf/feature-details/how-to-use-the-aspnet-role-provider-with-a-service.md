---
title: 'Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: ddfedeb2491998f64ab241ceba303d50d0714351
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184768"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą

Dostawca roli ASP.NET (w połączeniu z dostawcą członkostwa ASP.NET) jest funkcją, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta w witrynie i przypisywanie ról do celów autoryzacji. Dzięki tej funkcji każdy użytkownik może założyć konto w witrynie i zalogować się, aby uzyskać wyłączny dostęp do witryny i jej usług. Jest to w przeciwieństwie do zabezpieczeń systemu Windows, który wymaga od użytkowników, aby mieć konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwa użytkownika/hasło) może korzystać z witryny i jej usług.  
  
Aby zapoznać się z przykładową aplikacją, zobacz [Członkostwo i Dostawca roli](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać więcej informacji na temat funkcji dostawcy członkostwa ASP.NET, zobacz [Jak: Korzystanie z ASP.NET Dostawcy członkostwa](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
Funkcja dostawcy roli używa bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Deweloperzy programu Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika/hasła do aplikacji klienckiej WCF. Aby włączyć WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustawić jego <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> właściwość , <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles>i dodać wystąpienie do kolekcji zachowań do <xref:System.ServiceModel.ServiceHost> usługi, która jest hostująca usługę.  
  
## <a name="configure-the-role-provider"></a>Konfigurowanie dostawcy roli  
  
1. W pliku Web.config w obszarze <`system.web`> element dodaj element `roleManager` <> i ustaw jego `enabled` atrybut na `true`.  
  
2. Ustaw `defaultProvider` atrybut na `SqlRoleProvider`.  
  
3. Jako element podrzędny <`roleManager`> dodaj element `providers` <>.  
  
4. Jako element podrzędny do `providers` <> element dodaj `add` <> element z następującymi atrybutami ustawionymi `name` `type`na odpowiednie wartości: , , `connectionStringName`i `applicationName`, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="configure-the-service-to-use-the-role-provider"></a>Konfigurowanie usługi do korzystania z dostawcy roli  
  
1. W pliku Web.config dodaj element [ \<system.serviceModel>.](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Dodaj element [ \<>zachowań](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) do elementu `system.ServiceModel` <>.  
  
3. Dodaj [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.  
  
4. Dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` atrybut na odpowiednią wartość.  
  
5. Dodaj [ \<>>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) `behavior`> <.  
  
6. Ustaw `principalPermissionMode` atrybut na `UseAspNetRoles`.  
  
7. Ustaw `roleProviderName` atrybut na `SqlRoleProvider`. W poniższym przykładzie przedstawiono fragment konfiguracji.  
  
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

- [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
- [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
