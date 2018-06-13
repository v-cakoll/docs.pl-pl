---
title: 'Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: cc768f5e5086e6eba1ccac9d969eac14e14ceb2f
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33808146"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a><span data-ttu-id="f1cf6-102">Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="f1cf6-102">How to: Create a Service that Employs a Custom Certificate Validator</span></span>
<span data-ttu-id="f1cf6-103">W tym temacie przedstawiono sposób implementacji niestandardowego modułu weryfikacji certyfikatów i sposobie konfigurowania poświadczeń klienta lub usługę, należy zastąpić domyślną logikę sprawdzania poprawności certyfikatu niestandardowego modułu weryfikacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-103">This topic shows how to implement a custom certificate validator and how to configure client or service credentials to replace the default certificate validation logic with the custom certificate validator.</span></span>  
  
 <span data-ttu-id="f1cf6-104">Jeśli certyfikat X.509 jest używany do uwierzytelniania klienta lub usługę, Windows Communication Foundation (WCF) domyślnie korzysta z magazynu certyfikatów systemu Windows i interfejsu API szyfrowania weryfikacji certyfikatu i upewnij się, że jest zaufany.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-104">If the X.509 certificate is used to authenticate a client or service, Windows Communication Foundation (WCF) by default uses the Windows certificate store and Crypto API to validate the certificate and to ensure that it is trusted.</span></span> <span data-ttu-id="f1cf6-105">Czasami certyfikatu wbudowanych funkcji sprawdzania poprawności nie jest wystarczająco i musi zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-105">Sometimes the built-in certificate validation functionality is not enough and must be changed.</span></span> <span data-ttu-id="f1cf6-106">WCF zapewnia łatwy sposób zmień logikę sprawdzania poprawności, pozwalając użytkownikom na dodawanie niestandardowego modułu weryfikacji certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-106">WCF provides an easy way to change the validation logic by allowing users to add a custom certificate validator.</span></span> <span data-ttu-id="f1cf6-107">Jeśli określono niestandardowego modułu weryfikacji certyfikatów, WCF nie korzysta z logikę weryfikacji certyfikatu wbudowanych, ale zamiast tego zależy niestandardowego modułu weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-107">If a custom certificate validator is specified, WCF does not use the built-in certificate validation logic but relies on the custom validator instead.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="f1cf6-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="f1cf6-108">Procedures</span></span>  
  
#### <a name="to-create-a-custom-certificate-validator"></a><span data-ttu-id="f1cf6-109">Aby utworzyć niestandardowego modułu weryfikacji certyfikatów</span><span class="sxs-lookup"><span data-stu-id="f1cf6-109">To create a custom certificate validator</span></span>  
  
1.  <span data-ttu-id="f1cf6-110">Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-110">Define a new class derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span>  
  
2.  <span data-ttu-id="f1cf6-111">Implementuje klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-111">Implement the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> method.</span></span> <span data-ttu-id="f1cf6-112">Certyfikat, który musi zostać zweryfikowany jest przekazywany jako argument do metody.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-112">The certificate that must be validated is passed as an argument to the method.</span></span> <span data-ttu-id="f1cf6-113">Jeśli przekazany certyfikat jest nieprawidłowa według logiki sprawdzania poprawności, ta metoda zgłasza <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-113">If the passed certificate is not valid according to the validation logic, this method throws a <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>.</span></span> <span data-ttu-id="f1cf6-114">Jeśli certyfikat jest ważny, metoda zwraca wartość do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-114">If the certificate is valid, the method returns to the caller.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f1cf6-115">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, throw <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-115">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a><span data-ttu-id="f1cf6-116">Aby określić niestandardowego modułu weryfikacji certyfikatów w konfiguracji usługi</span><span class="sxs-lookup"><span data-stu-id="f1cf6-116">To specify a custom certificate validator in service configuration</span></span>  
  
1.  <span data-ttu-id="f1cf6-117">Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-117">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="f1cf6-118">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-118">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="f1cf6-119">Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-119">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the `<behavior>` element.</span></span>  
  
4.  <span data-ttu-id="f1cf6-120">Dodaj `<clientCertificate>` elementu `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-120">Add a `<clientCertificate>` element to the `<serviceCredentials>` element.</span></span>  
  
5.  <span data-ttu-id="f1cf6-121">Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-121">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) to the `<clientCertificate>` element.</span></span>  
  
6.  <span data-ttu-id="f1cf6-122">Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-122">Set the `customCertificateValidatorType` attribute to the validator type.</span></span> <span data-ttu-id="f1cf6-123">Poniższy przykład ustawia atrybut przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-123">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
7.  <span data-ttu-id="f1cf6-124">Ustaw `certificateValidationMode` atrybutu `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-124">Set the `certificateValidationMode` attribute to `Custom`.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a><span data-ttu-id="f1cf6-125">Aby określić niestandardowego modułu weryfikacji certyfikatów na komputerze klienckim przy użyciu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f1cf6-125">To specify a custom certificate validator using configuration on the client</span></span>  
  
1.  <span data-ttu-id="f1cf6-126">Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-126">Add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element and a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element.</span></span>  
  
2.  <span data-ttu-id="f1cf6-127">Dodaj [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-127">Add an [\<endpointBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) element.</span></span>  
  
3.  <span data-ttu-id="f1cf6-128">Dodaj `<behavior>` element i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-128">Add a `<behavior>` element and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="f1cf6-129">Dodaj [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-129">Add a [\<clientCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) element.</span></span>  
  
5.  <span data-ttu-id="f1cf6-130">Dodaj [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="f1cf6-130">Add a [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).</span></span>  
  
6.  <span data-ttu-id="f1cf6-131">Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-131">Add an [\<authentication>](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) as shown on the following example.</span></span>  
  
7.  <span data-ttu-id="f1cf6-132">Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-132">Set the `customCertificateValidatorType` attribute to the validator type.</span></span>  
  
8.  <span data-ttu-id="f1cf6-133">Ustaw `certificateValidationMode` atrybutu `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-133">Set the `certificateValidationMode` attribute to `Custom`.</span></span> <span data-ttu-id="f1cf6-134">Poniższy przykład ustawia atrybut przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-134">The following example sets the attribute to the namespace and name of the type.</span></span>  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a><span data-ttu-id="f1cf6-135">Aby określić niestandardowego modułu weryfikacji certyfikatów w usłudze przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="f1cf6-135">To specify a custom certificate validator using code on the service</span></span>  
  
1.  <span data-ttu-id="f1cf6-136">Określ niestandardowego modułu weryfikacji certyfikatów na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-136">Specify the custom certificate validator on the <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> property.</span></span> <span data-ttu-id="f1cf6-137">Można uzyskać dostęp przy użyciu poświadczeń usługi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-137">You can access the service credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span>  
  
2.  <span data-ttu-id="f1cf6-138">Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-138">Set the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a><span data-ttu-id="f1cf6-139">Aby określić niestandardowego modułu weryfikacji certyfikatów na komputerze klienckim przy użyciu kodu</span><span class="sxs-lookup"><span data-stu-id="f1cf6-139">To specify a custom certificate validator using code on the client</span></span>  
  
1.  <span data-ttu-id="f1cf6-140">Określ niestandardowego modułu weryfikacji certyfikatów przy użyciu <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-140">Specify the custom certificate validator using the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> property.</span></span> <span data-ttu-id="f1cf6-141">Można uzyskać dostępu do poświadczeń klienta przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-141">You can access the client credentials using the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> property.</span></span> <span data-ttu-id="f1cf6-142">(Klasa klienta generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze pochodną <xref:System.ServiceModel.ClientBase%601> klasy.)</span><span class="sxs-lookup"><span data-stu-id="f1cf6-142">(The client class generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) always derives from the <xref:System.ServiceModel.ClientBase%601> class.)</span></span>  
  
2.  <span data-ttu-id="f1cf6-143">Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-143">Set the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> property to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1cf6-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="f1cf6-144">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f1cf6-145">Opis</span><span class="sxs-lookup"><span data-stu-id="f1cf6-145">Description</span></span>  
 <span data-ttu-id="f1cf6-146">Poniższy przykład przedstawia implementację niestandardowego modułu weryfikacji certyfikatów i ich użycia w usłudze.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-146">The following sample shows an implementation of a custom certificate validator and its usage on the service.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f1cf6-147">Kod</span><span class="sxs-lookup"><span data-stu-id="f1cf6-147">Code</span></span>  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="f1cf6-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1cf6-148">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
