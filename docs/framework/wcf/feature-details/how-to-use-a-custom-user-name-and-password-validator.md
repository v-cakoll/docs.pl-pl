---
title: "Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee138c52c8cdd63137bf3c468ebbdd064d60d443
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła
Domyślnie, jeśli nazwa użytkownika i hasło jest używane do uwierzytelniania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] korzysta z systemu Windows do weryfikowania nazwy użytkownika i hasła. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia użytkownika niestandardowego nazwy i hasła schematy uwierzytelniania, nazywane również *modułów sprawdzania poprawności*. Dołączanie moduł weryfikacji nazwy i hasła użytkownika niestandardowego, Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie skonfigurować go.  
  
 Przykładową aplikację, zobacz [modułu weryfikacji hasła nazwa użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a>Aby utworzyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego  
  
1.  Utwórz klasę pochodną <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  Implementowanie schemat uwierzytelniania niestandardowego przez zastąpienie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     Nie używaj kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym. Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.  
  
     Aby przywrócić błędy uwierzytelniania z powrotem do klienta, throw <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Aby skonfigurować usługę do używania moduł weryfikacji nazwy i hasła użytkownika niestandardowego  
  
1.  Skonfiguruj obiekt binding używający Zabezpieczanie komunikatów za pośrednictwem żadnych transportu lub zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTP (S).  
  
     Podczas korzystania z zabezpieczeń wiadomości, dodanie wiązania dostarczane przez system, taką jak [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) obsługuje zabezpieczenia wiadomości i `UserName` typ poświadczeń.  
  
     Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), albo Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) używający protokołu HTTP (S) i `Basic` schematu uwierzytelniania.  
  
    > [!NOTE]
    >  Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszego jest używana, można użyć niestandardowego modułu weryfikacji nazwy użytkownika i hasła z zabezpieczeniami komunikatu i transportu. Z [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], niestandardowego modułu weryfikacji nazwy użytkownika i hasła można używać tylko z zabezpieczeń wiadomości.  
  
    > [!TIP]
    >  Aby uzyskać więcej informacji na temat używania \<netTcpBinding > w tym kontekście, zobacz [ \<Zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)  
  
    1.  W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
    2.  Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element do sekcji powiązania. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania elementu, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
    3.  Ustaw `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message`, `Transport`, `or``TransportWithMessageCredential`.  
  
    4.  Ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).  
  
         Podczas korzystania z zabezpieczeń wiadomości, ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) do `UserName`.  
  
         Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), należy ustawić `clientCredentialType` atrybutu [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) do `Basic`.  
  
        > [!NOTE]
        >  Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana w Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu i <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schematem uwierzytelniania niestandardowego korzysta z podzbioru uwierzytelniania systemu Windows. Wynika to z faktu w tym scenariuszu IIS wykonuje uwierzytelnianie systemu Windows starszych niż [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywoływania niestandardowego wystawcy uwierzytelnienia.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania elementu, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
     Poniższy przykład przedstawia kod konfiguracji powiązania.  
  
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
  
2.  Konfigurowanie zachowania, który określa, czy moduł weryfikacji nazwy i hasła użytkownika niestandardowego służy do sprawdzania pary nazwy i hasła użytkownika dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.  
  
    1.  Jako element podrzędny [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    2.  Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.  
  
    3.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` atrybutu odpowiednią wartość.  
  
    4.  Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.  
  
    5.  Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).  
  
    6.  Ustaw `userNamePasswordValidationMode` do `Custom`.  
  
        > [!IMPORTANT]
        >  Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa uwierzytelniania systemu Windows zamiast użytkownika niestandardowego Walidatora nazwy i hasła.  
  
    7.  Ustaw `customUserNamePasswordValidatorType` typ, który reprezentuje validator nazwy i hasła użytkownika.  
  
     W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment do tego punktu.  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykładowy kod przedstawia sposób tworzenia moduł weryfikacji nazwy i hasła użytkownika. Nie używaj kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym. Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
