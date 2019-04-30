---
title: 'Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b7e8e4a750aadd8a84a57cdf22c01f6b91e6256c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767159"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów
W tym temacie pokazano, jak zaimplementować niestandardowego modułu weryfikacji certyfikatów i sposób konfigurowania poświadczeń klienta lub usługę w celu zastąpienia domyślnej logiki weryfikacji certyfikatu za pomocą niestandardowego modułu weryfikacji certyfikatów.  
  
 Jeśli certyfikat X.509 jest używany do uwierzytelniania klienta lub usługę, Windows Communication Foundation (WCF) domyślnie używa magazynu certyfikatów Windows i interfejsu API szyfrowania na potrzeby weryfikacji certyfikatu i upewnij się, że jest zaufana. Czasami certyfikatu wbudowanych funkcji sprawdzania poprawności nie jest wystarczająco i musi zostać zmienione. Usługi WCF zapewnia prosty sposób zmienić logikę weryfikacji, pozwalając użytkownikom na dodawanie niestandardowego modułu weryfikacji certyfikatów. Jeśli określono niestandardowego modułu weryfikacji certyfikatów, usługi WCF nie używa logikę weryfikacji certyfikatu wbudowanych, ale opiera się na niestandardowego modułu weryfikacji.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Aby utworzyć niestandardowego modułu weryfikacji certyfikatów  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Implementowanie abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Certyfikat, który można sprawdzić poprawności jest przekazywany jako argument do metody. Jeśli przekazany certyfikat jest nieprawidłowy według logiki weryfikacji, ta metoda wyrzuca <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Jeśli certyfikat jest prawidłowy, metoda zwraca do obiektu wywołującego.  
  
    > [!NOTE]
    >  Aby zostały zwrócone błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów w konfiguracji usługi  
  
1. Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu do odpowiedniej wartości.  
  
3. Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` elementu.  
  
4. Dodaj `<clientCertificate>` elementu `<serviceCredentials>` elementu.  
  
5. Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` elementu.  
  
6. Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności. W poniższym przykładzie ustawiono atrybut przestrzeni nazw i nazwę typu.  
  
7. Ustaw `certificateValidationMode` atrybutu `Custom`.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów na komputerze klienckim przy użyciu konfiguracji  
  
1. Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2. Dodaj [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu.  
  
3. Dodaj `<behavior>` element i ustaw `name` atrybutu do odpowiedniej wartości.  
  
4. Dodaj [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
5. Dodaj [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak pokazano w poniższym przykładzie.  
  
7. Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności.  
  
8. Ustaw `certificateValidationMode` atrybutu `Custom`. W poniższym przykładzie ustawiono atrybut przestrzeni nazw i nazwę typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów w usłudze przy użyciu kodu  
  
1. Określ niestandardowego modułu weryfikacji certyfikatów na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> właściwości. Możesz uzyskać dostęp przy użyciu poświadczeń usługi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów na komputerze klienckim przy użyciu kodu  
  
1. Określanie niestandardowego modułu weryfikacji certyfikatów przy użyciu <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości. Możesz uzyskać dostęp przy użyciu poświadczeń klienta <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości. (Klient klasy generowanej przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze pochodzi od klasy <xref:System.ServiceModel.ClientBase%601> klasy.)  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje implementację niestandardowego modułu weryfikacji certyfikatów i sposób jej użycia w usłudze.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
