---
title: 'Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą'
ms.date: 03/30/2017
ms.assetid: 88d33a81-8ac7-48de-978c-5c5b1257951e
ms.openlocfilehash: 45eeda046e877b4379d7d0e5edd90fac305f5e44
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595300"
---
# <a name="how-to-use-the-aspnet-role-provider-with-a-service"></a>Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą

Dostawca roli ASP.NET (w połączeniu z dostawcą członkostwa ASP.NET) to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie konta w lokacji i przypisywanie ról do celów autoryzacji. Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z lokacją i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług. Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który poda poświadczenia (kombinacja nazwy użytkownika/hasła), może korzystać z witryny i jej usług.  
  
Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../samples/membership-and-role-provider.md). Aby uzyskać więcej informacji na temat funkcji ASP.NET Membership Provider, zobacz [How to: Use the ASP.NET Membership Provider](how-to-use-the-aspnet-membership-provider.md).  
  
Funkcja dostawcy roli używa bazy danych SQL Server do przechowywania informacji o użytkownikach. Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF. Aby włączyć funkcję WCF do korzystania z bazy danych, należy utworzyć wystąpienie <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> klasy, ustawić jej <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> Właściwość na <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> , a następnie dodać wystąpienie do kolekcji zachowań <xref:System.ServiceModel.ServiceHost> , które obsługują usługę.  
  
## <a name="configure-the-role-provider"></a>Konfigurowanie dostawcy roli  
  
1. W pliku Web. config w obszarze < `system.web` > Dodaj `roleManager` element < > i ustaw jego `enabled` atrybut na `true` .  
  
2. Ustaw `defaultProvider` atrybut na `SqlRoleProvider` .  
  
3. Jako element podrzędny do <`roleManager`>, dodaj <`providers`> elementu.  
  
4. Jako element podrzędny do <`providers`>, Dodaj <`add` elementu> z następującymi atrybutami ustawionymi na odpowiednie wartości: `name` , `type` , `connectionStringName` , i `applicationName` , jak pokazano w poniższym przykładzie.  
  
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
  
1. W pliku Web. config Dodaj [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element.  
  
2. Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element do `system.ServiceModel` elementu> <.  
  
3. Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` elementu> <.  
  
4. Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element i ustaw `name` odpowiednią wartość atrybutu.  
  
5. Dodaj [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) do `behavior` elementu> <.  
  
6. Ustaw `principalPermissionMode` atrybut na `UseAspNetRoles` .  
  
7. Ustaw `roleProviderName` atrybut na `SqlRoleProvider` . Poniższy przykład przedstawia fragment konfiguracji.  
  
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

- [Dostawca członkostwa i ról](../samples/membership-and-role-provider.md)
- [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](how-to-use-the-aspnet-membership-provider.md)
