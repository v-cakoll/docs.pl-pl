---
title: 'Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 593e3e97ad7e5ae65447d8618caacf22f762f9b4
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960063"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła
Domyślnie gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa Windows do weryfikowania nazwy użytkownika i hasła. Jednak WCF umożliwia niestandardowych użytkownika nazwy i hasła schematy uwierzytelniania, znany także jako *moduły weryfikacji*. Aby dołączyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego, należy utworzyć klasę, która pochodzi od klasy <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie skonfigurować go.  
  
 Dla przykładowej aplikacji, zobacz [modułu weryfikacji hasła nazwy użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Aby utworzyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego  
  
1. Utwórz klasę, która pochodzi od klasy <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2. Implementowanie schemat uwierzytelniania niestandardowego przez zastąpienie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     W poniższym przykładzie, który zastępuje nie należy używać kodu <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym. Zastąp kod przy użyciu usługi użytkownika niestandardowego nazwy i hasła sprawdzania poprawności schematu, które mogą wiązać z pobieraniem pary nazwy i hasła użytkownika z bazy danych.  
  
     Aby zostały zwrócone błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Aby skonfigurować usługę do używania weryfikacji nazwy i hasła użytkownika niestandardowego  
  
1. Konfigurowanie powiązania, który używa Zabezpieczanie komunikatów za pośrednictwem dowolnego transportu lub zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTP (S).  
  
     Korzystając z zabezpieczeń wiadomości, dodać jedno z powiązań dostarczanych przez system, takie jak [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) obsługuje zabezpieczenia wiadomości i `UserName` typ poświadczeń.  
  
     Korzystając z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S), są dodawane [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , który używa protokołu HTTP (S) i `Basic` schematu uwierzytelniania.  
  
    > [!NOTE]
    >  Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszej jest używany, można użyć niestandardowego modułu weryfikacji nazwy użytkownika i hasła za pomocą zabezpieczeń transportu i wiadomości. Za pomocą WinFX niestandardowego modułu weryfikacji nazwy użytkownika i hasła należy używać tylko z zabezpieczeń komunikatów.  
  
    > [!TIP]
    >  Aby uzyskać więcej informacji na temat korzystania z \<netTcpBinding > w tym kontekście, zobacz [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1. W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodawanie [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
    2. Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element w sekcji wiązania. Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3. Ustaw `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message`, `Transport`, lub `TransportWithMessageCredential`.  
  
    4. Ustaw `clientCredentialType` atrybutu [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Korzystając z zabezpieczeń komunikatów, ustaw `clientCredentialType` atrybutu [ \<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) do `UserName`.  
  
         Korzystając z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S), ustaw `clientCredentialType` atrybutu [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) do `Basic`.  
  
        > [!NOTE]
        >  Gdy usługa WCF jest hostowana w Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu i <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schemat uwierzytelniania niestandardowego korzysta z podzbioru uwierzytelniania Windows. To, ponieważ w tym scenariuszu IIS przeprowadza uwierzytelnianie Windows przed WCF, wywoływania niestandardowych wystawcy uwierzytelnienia.  
  
     Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     Poniższy przykład pokazuje kod konfiguracji dla wiązania.  
  
    ```xml  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2. Konfigurowanie zachowania, który określa, czy moduł weryfikacji nazwy i hasła użytkownika niestandardowego jest używana do zweryfikowania pary nazwy i hasła użytkownika dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.  
  
    1. Jako element podrzędny [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodawanie [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    2. Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    3. Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` atrybutu do odpowiedniej wartości.  
  
    4. Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
    5. Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6. Ustaw `userNamePasswordValidationMode` do `Custom`.  
  
        > [!IMPORTANT]
        >  Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, usługi WCF korzysta z uwierzytelniania Windows zamiast użytkownika niestandardowego Walidatora nazwy i hasła.  
  
    7. Ustaw `customUserNamePasswordValidatorType` do typu, który reprezentuje użytkownika niestandardowego weryfikacji nazwy i hasła.  
  
     W poniższym przykładzie przedstawiono `<serviceCredentials>` fragmentu do tego punktu.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego. Nie należy używać kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym. Zastąp kod przy użyciu usługi użytkownika niestandardowego nazwy i hasła sprawdzania poprawności schematu, które mogą wiązać z pobieraniem pary nazwy i hasła użytkownika z bazy danych.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
