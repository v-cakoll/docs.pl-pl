---
title: 'Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET'
description: Dowiedz się, w jaki sposób dostawca członkostwa ASP.NET obsługuje witryny sieci Web, które umożliwiają użytkownikom tworzenie nazwy użytkownika i hasła w celu uzyskania dostępu bez konta domeny systemu Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246730"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET

Dostawca członkostwa ASP.NET to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł. Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z witryną i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług. Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy użytkownika/hasła), może korzystać z witryny i jej usług.

Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../samples/membership-and-role-provider.md). Aby uzyskać informacje o korzystaniu z funkcji dostawcy roli ASP.NET, zobacz [How to: Use the ASP.NET role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).

Funkcja członkostwa wymaga użycia bazy danych SQL Server do przechowywania informacji o użytkowniku. Ta funkcja zawiera również metody wyświetlania monitu z pytaniem dla użytkowników, którzy zapominali swoje hasła.

Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF. Aby przesłać dane do usługi WCF, użyj powiązania, które obsługuje poświadczenia nazwy użytkownika/hasła, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) a) i ustaw typ poświadczeń klienta na `UserName` . W usłudze zabezpieczenia WCF uwierzytelniają użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez rolę ASP.NET.

> [!NOTE]
> Funkcja WCF nie dostarcza metod do wypełniania bazy danych za pomocą kombinacji nazwy użytkownika/hasła lub innych informacji o użytkowniku.

### <a name="to-configure-the-membership-provider"></a>Aby skonfigurować dostawcę członkostwa

1. W pliku Web.config w obszarze <`system.web`> Utwórz `membership` element <>.

2. W obszarze `<membership>` elementu Utwórz `<providers>` element.

3. Jako element podrzędny do <`providers`>, Dodaj `<clear />` element, aby opróżnić kolekcję dostawców.

4. W obszarze `<clear />` elementu Utwórz <`add` element> z następującymi atrybutami ustawionymi na odpowiednie wartości:,,,,,,,, `name` `type` `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` i `passwordFormat` . Ten `name` atrybut jest używany później jako wartość w pliku konfiguracji. W poniższym przykładzie jest ustawiana wartość `SqlMembershipProvider` .

    W poniższym przykładzie przedstawiono sekcję Konfiguracja.

    ```xml
    <!-- Configure the Sql Membership Provider -->
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">
      <providers>
        <clear />
          <add
            name="SqlMembershipProvider"
            type="System.Web.Security.SqlMembershipProvider"
            connectionStringName="SqlConn"
            applicationName="MembershipAndRoleProviderSample"
            enablePasswordRetrieval="false"
            enablePasswordReset="false"
            requiresQuestionAndAnswer="false"
            requiresUniqueEmail="true"
            passwordFormat="Hashed" />
      </providers>
    </membership>
    ```

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacji nazwy użytkownika/hasła

1. W pliku konfiguracji, w obszarze [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.

2. Dodaj [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązań. Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).

3. Ustaw atrybut `mode` elementu `<security>` na `Message`.

4. Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName` . Oznacza to, że para nazwa użytkownika/hasło zostanie użyta jako poświadczenia klienta.

    Poniższy przykład pokazuje kod konfiguracji dla powiązania.

    ```xml
    <system.serviceModel>
    <bindings>
      <wsHttpBinding>
      <!-- Set up a binding that uses UserName as the client credential type -->
        <binding name="MembershipBinding">
          <security mode ="Message">
            <message clientCredentialType ="UserName"/>
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    </system.serviceModel>
    ```

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Aby skonfigurować usługę do korzystania z dostawcy członkostwa

1. Jako element podrzędny do `<system.serviceModel>` elementu, Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element

2. Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` elementu> <.

3. Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a i ustaw `name` odpowiednią wartość atrybutu.

4. Dodaj [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `behavior` elementu> <.

5. Dodaj [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>` element do elementu.

6. Ustaw `userNamePasswordValidationMode` atrybut na `MembershipProvider` .

    > [!IMPORTANT]
    > Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.

7. Ustaw `membershipProviderName` atrybut na nazwę dostawcy (określony podczas dodawania dostawcy w pierwszej procedurze w tym temacie). Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.

    ```xml
    <behaviors>
       <serviceBehaviors>
          <behavior name="MyServiceBehavior">
             <serviceCredentials>
                <userNameAuthentication
                userNamePasswordValidationMode="MembershipProvider"
                membershipProviderName="SqlMembershipProvider" />
             </serviceCredentials>
          </behavior>
       </serviceBehaviors>
    </behaviors>
    ```

## <a name="example"></a>Przykład

Poniższy kod przedstawia konfigurację usługi korzystającej z funkcji członkostwa ASP.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">
        <endpoint address="http://microsoft.com/WCFservices/Calculator"
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />
      </service>
    </services>
    <behaviors>
      <serviceBehaviors>
        <behavior name="MyServiceBehavior">
          <serviceCredentials>
            <userNameAuthentication
              userNamePasswordValidationMode="MembershipProvider"
              membershipProviderName="SqlMembershipProvider" />
          </serviceCredentials>
        </behavior>
          </serviceBehaviors>
    </behaviors>
    <bindings>
      <wsHttpBinding>
        <binding name="MembershipBinding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Dostawca członkostwa i ról](../samples/membership-and-role-provider.md)
