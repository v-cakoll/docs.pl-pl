---
title: 'Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: d71e3679f4bf395b240c330fc573d6f613d1be07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495297"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a>Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET
[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy członkostwa jest funkcją, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie użytkownika unikatowych kombinacji nazwy i hasła. Z tej funkcji każdy użytkownik można założyć konto w witrynie i zaloguj się do wyłącznego dostępu do lokacji i jej usług. Dzięki temu nie trzeba zabezpieczenia systemu Windows, który wymaga od użytkowników mają konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), można użyć lokacji i jej usługi.  
  
 Przykładową aplikację, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Informacji o używaniu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli dostawcy funkcji, zobacz [porady: Używanie dostawcy ról ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
 Funkcja członkostwa wymaga, korzystanie z bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Funkcja zawiera również metody w celu wyświetlenia monitu z pytaniem wszyscy użytkownicy, którzy pamiętasz swojego hasła.  
  
 Windows Communication Foundation (WCF) deweloperzy mogą wykorzystać te funkcje ze względów bezpieczeństwa. Po zintegrowaniu aplikacji WCF, użytkowników, musisz podać kombinacji nazwy i hasła użytkownika do aplikacji klienta WCF. Do transferu danych do usługi WCF, użyj powiązania, które obsługuje poświadczenia nazwy i hasła użytkownika, takich jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i ustawić typ poświadczeń do klienta`UserName`. W usłudze zabezpieczeń WCF uwierzytelnia użytkownika na podstawie nazwy użytkownika i hasła i przypisuje rolę określonego przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli.  
  
> [!NOTE]
>  Usługi WCF nie zawiera metody służące do wypełniania bazy danych z kombinacji nazwy i hasła użytkownika lub inne informacje o użytkowniku.  
  
### <a name="to-configure-the-membership-provider"></a>Aby skonfigurować dostawcę członkostwa  
  
1.  W pliku Web.config w obszarze <`system.web`> elementu, Utwórz <`membership`> elementu.  
  
2.  W obszarze `<membership>` elementu, Utwórz `<providers>` elementu.  
  
3.  Jako element podrzędny <`providers`> elementu, Dodaj `<clear />` element, aby opróżnić kolekcji dostawców.  
  
4.  W obszarze `<clear />` elementu, Utwórz <`add`> elementu z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, i `passwordFormat`. `name` Atrybut jest później używany jako wartość w pliku konfiguracji. Poniższy przykład ustawia ją na `SqlMembershipProvider`.  
  
     W poniższym przykładzie pokazano sekcję konfiguracyjną.  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Aby skonfigurować zabezpieczenia usługi, aby zaakceptować kombinacja nazwy i hasła użytkownika  
  
1.  W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
2.  Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązania. Aby uzyskać więcej informacji o tworzeniu elementu wiązania WCF, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
3.  Ustaw atrybut `mode` elementu `<security>` na `Message`.  
  
4.  Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName`. Określa, że pary nazwa/hasło użytkownika będzie służyć jako poświadczeń klienta.  
  
     Poniższy przykład przedstawia kod konfiguracji powiązania.  
  
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
  
1.  Jako element podrzędny `<system.serviceModel>` elementu, Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) — element  
  
2.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.  
  
3.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu odpowiednią wartość.  
  
4.  Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do <`behavior`> elementu.  
  
5.  Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.  
  
6.  Ustaw `userNamePasswordValidationMode` atrybutu `MembershipProvider`.  
  
    > [!IMPORTANT]
    >  Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, usługi WCF używa uwierzytelniania systemu Windows zamiast [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.  
  
7.  Ustaw `membershipProviderName` atrybutu nazwę dostawcy (określona podczas dodawania dostawcy w pierwszej procedurze w tym temacie). W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment do tego punktu.  
  
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
 Poniższy kod przedstawia konfigurację dla usługi, która jest używana funkcja członkostwa ASP.  
  
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
 [Instrukcje: używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
