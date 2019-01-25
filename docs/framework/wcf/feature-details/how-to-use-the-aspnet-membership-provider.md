---
title: 'Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 4653a4b4ae90f391eac559210deb611e2a83d0f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634509"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy członkostwa jest funkcją, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych użytkowników kombinacji nazwy i hasła. Za pomocą tej funkcji każdy użytkownik może ustanowić konto w witrynie i logowanie za wyłączny dostęp do witryn i usług. Jest to w przeciwieństwie do zabezpieczeń Windows, która wymaga od użytkowników mają konta w domenie Windows. Zamiast tego można użyć każdemu użytkownikowi, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), lokacji i jej usługi.  
  
 Dla przykładowej aplikacji, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać informacje o korzystaniu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcję dostawcy ról, zobacz [jak: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Funkcja członkostwa wymaga, korzystanie z bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Funkcja obejmuje również metody monit z pytaniem użytkownicy, którzy zapomni swojego hasła.  
  
 Windows Communication Foundation (WCF) deweloperom korzystać z zalet tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu aplikacji WCF, użytkownicy muszą podać kombinacja nazwy i hasła użytkownika do aplikacji klienta programu WCF. Aby transferu danych do usługi WCF, należy użyć powiązania, które obsługuje poświadczenia nazwy i hasła użytkownika, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i Ustaw typ poświadczeń do klienta`UserName`. W usłudze WCF zabezpieczeń uwierzytelnia użytkownika, w oparciu o nazwę użytkownika i hasło i przypisuje rolę określonego przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli.  
  
> [!NOTE]
>  Usługi WCF nie udostępnia metody służące do wypełniania bazy danych przy użyciu kombinacji nazwy i hasła użytkownika lub inne informacje o użytkowniku.  
  
### <a name="to-configure-the-membership-provider"></a>Aby skonfigurować dostawcy członkostwa  
  
1.  W pliku Web.config w obszarze <`system.web`> element, Utwórz <`membership`> element.  
  
2.  W obszarze `<membership>` elementu, Utwórz `<providers>` elementu.  
  
3.  Jako element podrzędny <`providers`> elementu Dodawanie `<clear />` element, aby opróżnić kolekcja dostawców.  
  
4.  W obszarze `<clear />` elementu, Utwórz <`add`> element z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, i `passwordFormat`. `name` Atrybut jest używany później jako wartość w pliku konfiguracji. Poniższy przykład ustawia ją na `SqlMembershipProvider`.  
  
     Sekcja konfiguracji można znaleźć w poniższym przykładzie.  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacja nazwy i hasła użytkownika  
  
1.  W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodawanie [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
2.  Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji wiązania. Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Ustaw atrybut `mode` elementu `<security>` na `Message`.  
  
4.  Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName`. Określa, że pary nazwa/hasło użytkownika będzie służyć jako poświadczeń klienta.  
  
     Poniższy przykład pokazuje kod konfiguracji dla wiązania.  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Aby skonfigurować usługę do używania dostawcy członkostwa  
  
1.  Jako element podrzędny `<system.serviceModel>` elementu Dodawanie [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) — element  
  
2.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> element.  
  
3.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu do odpowiedniej wartości.  
  
4.  Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do <`behavior`> element.  
  
5.  Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.  
  
6.  Ustaw `userNamePasswordValidationMode` atrybutu `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, usługi WCF korzysta z uwierzytelniania Windows zamiast [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.  
  
7.  Ustaw `membershipProviderName` atrybutu Nazwa dostawcy (określone podczas dodawania dostawcy w pierwszej procedurze w tym temacie). W poniższym przykładzie przedstawiono `<serviceCredentials>` fragmentu do tego punktu.  
  
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
 Poniższy kod pokazuje konfigurację to usługa, która używa funkcji członkostwa ASP.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
