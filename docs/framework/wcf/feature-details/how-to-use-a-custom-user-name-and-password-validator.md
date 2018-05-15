---
title: 'Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 8580219181af8fd28bcc99c60bd1e681ffbdad54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="215c8-102">Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="215c8-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="215c8-103">Domyślnie gdy nazwa użytkownika i hasło jest używane do uwierzytelniania, Windows Communication Foundation (WCF) używa do weryfikowania nazwy użytkownika i hasła systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="215c8-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="215c8-104">Jednak WCF umożliwia użytkownika niestandardowego nazwy i hasła schematy uwierzytelniania, nazywane również *modułów sprawdzania poprawności*.</span><span class="sxs-lookup"><span data-stu-id="215c8-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="215c8-105">Dołączanie moduł weryfikacji nazwy i hasła użytkownika niestandardowego, Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="215c8-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="215c8-106">Przykładową aplikację, zobacz [modułu weryfikacji hasła nazwa użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="215c8-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="215c8-107">Aby utworzyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="215c8-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="215c8-108">Utwórz klasę pochodną <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="215c8-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="215c8-109">Implementowanie schemat uwierzytelniania niestandardowego przez zastąpienie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="215c8-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="215c8-110">Nie używaj kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="215c8-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="215c8-111">Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="215c8-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="215c8-112">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, throw <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="215c8-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="215c8-113">Aby skonfigurować usługę do używania moduł weryfikacji nazwy i hasła użytkownika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="215c8-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="215c8-114">Skonfiguruj obiekt binding używający Zabezpieczanie komunikatów za pośrednictwem żadnych transportu lub zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="215c8-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="215c8-115">Podczas korzystania z zabezpieczeń wiadomości, dodanie wiązania dostarczane przez system, taką jak [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) obsługuje zabezpieczenia wiadomości i `UserName` typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="215c8-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="215c8-116">Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), albo Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) używający protokołu HTTP (S) i `Basic` schematu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="215c8-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="215c8-117">Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszego jest używana, można użyć niestandardowego modułu weryfikacji nazwy użytkownika i hasła z zabezpieczeniami komunikatu i transportu.</span><span class="sxs-lookup"><span data-stu-id="215c8-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="215c8-118">Z [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], niestandardowego modułu weryfikacji nazwy użytkownika i hasła można używać tylko z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="215c8-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="215c8-119">Aby uzyskać więcej informacji na temat używania \<netTcpBinding > w tym kontekście, zobacz [ \<Zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="215c8-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="215c8-120">W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="215c8-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="215c8-121">Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element do sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="215c8-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="215c8-122">Aby uzyskać więcej informacji o tworzeniu elementu wiązania WCF, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="215c8-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="215c8-123">Ustaw `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="215c8-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="215c8-124">Ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="215c8-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="215c8-125">Podczas korzystania z zabezpieczeń wiadomości, ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) do `UserName`.</span><span class="sxs-lookup"><span data-stu-id="215c8-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="215c8-126">Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), należy ustawić `clientCredentialType` atrybutu [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) do `Basic`.</span><span class="sxs-lookup"><span data-stu-id="215c8-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="215c8-127">Gdy usługa WCF jest hostowana w Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu i <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schematem uwierzytelniania niestandardowego korzysta z podzbioru uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="215c8-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="215c8-128">To, ponieważ w tym scenariuszu IIS wykonuje uwierzytelnianie systemu Windows przed WCF, wywoływania niestandardowych wystawcy uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="215c8-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>  
  
     <span data-ttu-id="215c8-129">Aby uzyskać więcej informacji o tworzeniu elementu wiązania WCF, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="215c8-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="215c8-130">Poniższy przykład przedstawia kod konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="215c8-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2.  <span data-ttu-id="215c8-131">Konfigurowanie zachowania, który określa, czy moduł weryfikacji nazwy i hasła użytkownika niestandardowego służy do sprawdzania pary nazwy i hasła użytkownika dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="215c8-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="215c8-132">Jako element podrzędny [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="215c8-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="215c8-133">Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="215c8-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="215c8-134">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="215c8-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="215c8-135">Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="215c8-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="215c8-136">Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="215c8-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="215c8-137">Ustaw `userNamePasswordValidationMode` do `Custom`.</span><span class="sxs-lookup"><span data-stu-id="215c8-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="215c8-138">Jeśli `userNamePasswordValidationMode` nie jest ustawiona, usługi WCF używa uwierzytelniania systemu Windows zamiast użytkownika niestandardowego Walidatora nazwy i hasła.</span><span class="sxs-lookup"><span data-stu-id="215c8-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="215c8-139">Ustaw `customUserNamePasswordValidatorType` typ, który reprezentuje validator nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="215c8-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="215c8-140">W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="215c8-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="215c8-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="215c8-141">Example</span></span>  
 <span data-ttu-id="215c8-142">Poniższy przykładowy kod przedstawia sposób tworzenia moduł weryfikacji nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="215c8-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="215c8-143">Nie używaj kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="215c8-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="215c8-144">Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="215c8-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="215c8-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="215c8-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="215c8-146">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="215c8-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="215c8-147">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="215c8-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
