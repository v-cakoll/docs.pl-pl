---
title: 'Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: 156d661fd5602333fae8066f3062b442a1df19af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951707"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="e03fa-102">Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="e03fa-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="e03fa-103">W tym temacie pokazano, jak zaimplementować niestandardowy moduł sprawdzania poprawności certyfikatu oraz jak skonfigurować poświadczenia klienta lub usługi w celu zastąpienia domyślnej logiki walidacji certyfikatu za pomocą niestandardowego modułu sprawdzania certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="e03fa-104">Jeśli certyfikat X. 509 jest używany do uwierzytelniania klienta lub usługi, Windows Communication Foundation (WCF) domyślnie używa magazynu certyfikatów systemu Windows i interfejsu API kryptografii do weryfikacji certyfikatu i upewnienia się, że jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="e03fa-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="e03fa-105">Czasami Wbudowana funkcja weryfikacji certyfikatu jest za mała i należy ją zmienić.</span><span class="sxs-lookup"><span data-stu-id="e03fa-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="e03fa-106">Funkcja WCF zapewnia łatwy sposób zmiany logiki walidacji przez umożliwienie użytkownikom dodawania niestandardowego modułu weryfikacji certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="e03fa-107">Jeśli jest określony niestandardowy moduł sprawdzania poprawności certyfikatu, funkcja WCF nie korzysta z wbudowanej logiki walidacji certyfikatu, ale zamiast tego używa niestandardowego modułu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="e03fa-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="e03fa-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="e03fa-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="e03fa-109">Aby utworzyć niestandardowy moduł sprawdzania poprawności certyfikatu</span><span class="sxs-lookup"><span data-stu-id="e03fa-109">To create a custom certificate validator</span></span>  
  
1. <span data-ttu-id="e03fa-110">Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="e03fa-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2. <span data-ttu-id="e03fa-111">Zaimplementuj metodę <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="e03fa-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="e03fa-112">Certyfikat, który musi zostać sprawdzony, jest przenoszona jako argument do metody.</span><span class="sxs-lookup"><span data-stu-id="e03fa-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="e03fa-113">Jeśli przesłany certyfikat nie jest prawidłowy zgodnie z logiką walidacji, ta metoda zgłasza <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="e03fa-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="e03fa-114">Jeśli certyfikat jest prawidłowy, Metoda powraca do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="e03fa-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e03fa-115">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="e03fa-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="e03fa-116">Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu w konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="e03fa-116">To specify a custom certificate validator in service configuration</span></span>  
  
1. <span data-ttu-id="e03fa-117">Dodaj zachowania > elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) . [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="e03fa-118">`name` [ Dodaj\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="e03fa-119">Dodaj > ServiceCredentials do elementu.`<behavior>` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4. <span data-ttu-id="e03fa-120">`<clientCertificate>` Dodaj element`<serviceCredentials>` do elementu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5. <span data-ttu-id="e03fa-121">Dodaj [> uwierzytelniania do elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>`</span><span class="sxs-lookup"><span data-stu-id="e03fa-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6. <span data-ttu-id="e03fa-122">`customCertificateValidatorType` Ustaw atrybut na typ walidacji.</span><span class="sxs-lookup"><span data-stu-id="e03fa-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="e03fa-123">Poniższy przykład ustawia atrybut na przestrzeń nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7. <span data-ttu-id="e03fa-124">Ustaw atrybut na `Custom`. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="e03fa-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <serviceBehaviors>  
        <behavior name="ServiceBehavior">  
         <serviceCredentials>  
          <clientCertificate>  
          <authentication certificateValidationMode="Custom" customCertificateValidatorType="Samples.MyValidator, service" />  
          </clientCertificate>  
         </serviceCredentials>  
        </behavior>  
       </serviceBehaviors>  
      </behaviors>  
    </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="e03fa-125">Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu konfiguracji na kliencie</span><span class="sxs-lookup"><span data-stu-id="e03fa-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1. <span data-ttu-id="e03fa-126">Dodaj zachowania > elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) . [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2. <span data-ttu-id="e03fa-127">Dodaj element [> endpointBehaviors.\<](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3. <span data-ttu-id="e03fa-128">Dodaj element i ustaw odpowiednią wartość `name` atrybutu. `<behavior>`</span><span class="sxs-lookup"><span data-stu-id="e03fa-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="e03fa-129">Dodaj element ClientCredentials >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5. <span data-ttu-id="e03fa-130">Dodaj > serviceCertificate. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6. <span data-ttu-id="e03fa-131">Dodaj > uwierzytelniania, jak pokazano w poniższym przykładzie. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)</span><span class="sxs-lookup"><span data-stu-id="e03fa-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7. <span data-ttu-id="e03fa-132">`customCertificateValidatorType` Ustaw atrybut na typ walidacji.</span><span class="sxs-lookup"><span data-stu-id="e03fa-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8. <span data-ttu-id="e03fa-133">Ustaw atrybut na `Custom`. `certificateValidationMode`</span><span class="sxs-lookup"><span data-stu-id="e03fa-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="e03fa-134">Poniższy przykład ustawia atrybut na przestrzeń nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
       <endpointBehaviors>  
        <behavior name="clientBehavior">  
         <clientCredentials>  
          <serviceCertificate>  
           <authentication certificateValidationMode="Custom"   
                  customCertificateValidatorType=  
             "Samples.CustomX509CertificateValidator, client"/>  
          </serviceCertificate>  
         </clientCredentials>  
        </behavior>  
       </endpointBehaviors>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="e03fa-135">Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu kodu w usłudze</span><span class="sxs-lookup"><span data-stu-id="e03fa-135">To specify a custom certificate validator using code on the service</span></span>  
  
1. <span data-ttu-id="e03fa-136">Określ niestandardowy moduł sprawdzania poprawności <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="e03fa-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="e03fa-137">Możesz uzyskać dostęp do poświadczeń usługi przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e03fa-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2. <span data-ttu-id="e03fa-138">Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e03fa-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="e03fa-139">Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu kodu na kliencie</span><span class="sxs-lookup"><span data-stu-id="e03fa-139">To specify a custom certificate validator using code on the client</span></span>  
  
1. <span data-ttu-id="e03fa-140">Określ niestandardowy moduł sprawdzania poprawności certyfikatu przy <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="e03fa-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="e03fa-141">Możesz uzyskać dostęp do poświadczeń klienta przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="e03fa-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="e03fa-142">(Klasa klienta wygenerowana przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze pochodzi z <xref:System.ServiceModel.ClientBase%601> klasy.)</span><span class="sxs-lookup"><span data-stu-id="e03fa-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2. <span data-ttu-id="e03fa-143">Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="e03fa-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e03fa-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e03fa-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e03fa-145">Opis</span><span class="sxs-lookup"><span data-stu-id="e03fa-145">Description</span></span>  
 <span data-ttu-id="e03fa-146">Poniższy przykład pokazuje implementację niestandardowego modułu weryfikacji certyfikatu i jego użycia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e03fa-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e03fa-147">Kod</span><span class="sxs-lookup"><span data-stu-id="e03fa-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="e03fa-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e03fa-148">See also</span></span>

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
