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
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d592f-102">Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="d592f-102">How to: Use a Custom User Name and Password Validator</span></span>
<span data-ttu-id="d592f-103">Domyślnie, jeśli nazwa użytkownika i hasło jest używane do uwierzytelniania [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] korzysta z systemu Windows do weryfikowania nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="d592f-103">By default, when a user name and password is used for authentication, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses Windows to validate the user name and password.</span></span> <span data-ttu-id="d592f-104">Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] umożliwia użytkownika niestandardowego nazwy i hasła schematy uwierzytelniania, nazywane również *modułów sprawdzania poprawności*.</span><span class="sxs-lookup"><span data-stu-id="d592f-104">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="d592f-105">Dołączanie moduł weryfikacji nazwy i hasła użytkownika niestandardowego, Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie skonfigurować go.</span><span class="sxs-lookup"><span data-stu-id="d592f-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>  
  
 <span data-ttu-id="d592f-106">Przykładową aplikację, zobacz [modułu weryfikacji hasła nazwa użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="d592f-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>  
  
### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d592f-107">Aby utworzyć moduł weryfikacji nazwy i hasła użytkownika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d592f-107">To create a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="d592f-108">Utwórz klasę pochodną <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="d592f-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  <span data-ttu-id="d592f-109">Implementowanie schemat uwierzytelniania niestandardowego przez zastąpienie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d592f-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     <span data-ttu-id="d592f-110">Nie używaj kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="d592f-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d592f-111">Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d592f-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
     <span data-ttu-id="d592f-112">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, throw <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d592f-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="d592f-113">Aby skonfigurować usługę do używania moduł weryfikacji nazwy i hasła użytkownika niestandardowego</span><span class="sxs-lookup"><span data-stu-id="d592f-113">To configure a service to use a custom user name and password validator</span></span>  
  
1.  <span data-ttu-id="d592f-114">Skonfiguruj obiekt binding używający Zabezpieczanie komunikatów za pośrednictwem żadnych transportu lub zabezpieczenia na poziomie transportu za pośrednictwem protokołu HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="d592f-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>  
  
     <span data-ttu-id="d592f-115">Podczas korzystania z zabezpieczeń wiadomości, dodanie wiązania dostarczane przez system, taką jak [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) obsługuje zabezpieczenia wiadomości i `UserName` typ poświadczeń.</span><span class="sxs-lookup"><span data-stu-id="d592f-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>  
  
     <span data-ttu-id="d592f-116">Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), albo Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \< netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) lub [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) używający protokołu HTTP (S) i `Basic` schematu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="d592f-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d592f-117">Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszego jest używana, można użyć niestandardowego modułu weryfikacji nazwy użytkownika i hasła z zabezpieczeniami komunikatu i transportu.</span><span class="sxs-lookup"><span data-stu-id="d592f-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="d592f-118">Z [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], niestandardowego modułu weryfikacji nazwy użytkownika i hasła można używać tylko z zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d592f-118">With [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], a custom username and password validator can only be used with message security.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d592f-119">Aby uzyskać więcej informacji na temat używania \<netTcpBinding > w tym kontekście, zobacz [ \<Zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d592f-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>  
  
    1.  <span data-ttu-id="d592f-120">W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d592f-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
    2.  <span data-ttu-id="d592f-121">Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) lub [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element do sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="d592f-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d592f-122">Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania elementu, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d592f-122"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
    3.  <span data-ttu-id="d592f-123">Ustaw `mode` atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message`, `Transport`, `or``TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="d592f-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, `or``TransportWithMessageCredential`.</span></span>  
  
    4.  <span data-ttu-id="d592f-124">Ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d592f-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>  
  
         <span data-ttu-id="d592f-125">Podczas korzystania z zabezpieczeń wiadomości, ustaw `clientCredentialType` atrybutu [ \<wiadomości >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) do `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d592f-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>  
  
         <span data-ttu-id="d592f-126">Korzystając z zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S), należy ustawić `clientCredentialType` atrybutu [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<transportu >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) do `Basic`.</span><span class="sxs-lookup"><span data-stu-id="d592f-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="d592f-127">Gdy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa jest obsługiwana w Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu i <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schematem uwierzytelniania niestandardowego korzysta z podzbioru uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d592f-127">When a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="d592f-128">Wynika to z faktu w tym scenariuszu IIS wykonuje uwierzytelnianie systemu Windows starszych niż [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wywoływania niestandardowego wystawcy uwierzytelnienia.</span><span class="sxs-lookup"><span data-stu-id="d592f-128">That is because in this scenario, IIS performs Windows authentication prior to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] invoking the custom authenticator.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="d592f-129">Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania elementu, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d592f-129"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
     <span data-ttu-id="d592f-130">Poniższy przykład przedstawia kod konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="d592f-130">The following example shows the configuration code for the binding.</span></span>  
  
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
  
2.  <span data-ttu-id="d592f-131">Konfigurowanie zachowania, który określa, czy moduł weryfikacji nazwy i hasła użytkownika niestandardowego służy do sprawdzania pary nazwy i hasła użytkownika dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="d592f-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>  
  
    1.  <span data-ttu-id="d592f-132">Jako element podrzędny [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d592f-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    2.  <span data-ttu-id="d592f-133">Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d592f-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>  
  
    3.  <span data-ttu-id="d592f-134">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="d592f-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>  
  
    4.  <span data-ttu-id="d592f-135">Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d592f-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
    5.  <span data-ttu-id="d592f-136">Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="d592f-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
    6.  <span data-ttu-id="d592f-137">Ustaw `userNamePasswordValidationMode` do `Custom`.</span><span class="sxs-lookup"><span data-stu-id="d592f-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="d592f-138">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa uwierzytelniania systemu Windows zamiast użytkownika niestandardowego Walidatora nazwy i hasła.</span><span class="sxs-lookup"><span data-stu-id="d592f-138">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the custom user name and password validator.</span></span>  
  
    7.  <span data-ttu-id="d592f-139">Ustaw `customUserNamePasswordValidatorType` typ, który reprezentuje validator nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d592f-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>  
  
     <span data-ttu-id="d592f-140">W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="d592f-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d592f-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="d592f-141">Example</span></span>  
 <span data-ttu-id="d592f-142">Poniższy przykładowy kod przedstawia sposób tworzenia moduł weryfikacji nazwy i hasła użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d592f-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="d592f-143">Nie używaj kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="d592f-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="d592f-144">Zastąp kod użytkownika niestandardowego nazwy i hasła weryfikacji schematem, które mogą dotyczyć pobierania pary nazwy i hasła użytkownika z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d592f-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d592f-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d592f-145">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>  
 [<span data-ttu-id="d592f-146">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d592f-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 [<span data-ttu-id="d592f-147">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="d592f-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
