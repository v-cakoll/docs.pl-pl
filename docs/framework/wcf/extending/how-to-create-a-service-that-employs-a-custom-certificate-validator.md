---
title: "Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów"
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
helpviewer_keywords: WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0a48801b1d4674b81a0e4b54a80b69d026ce2af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów
W tym temacie przedstawiono sposób implementacji niestandardowego modułu weryfikacji certyfikatów i sposobie konfigurowania poświadczeń klienta lub usługę, należy zastąpić domyślną logikę sprawdzania poprawności certyfikatu niestandardowego modułu weryfikacji certyfikatów.  
  
 Jeśli certyfikat X.509 jest używany do uwierzytelniania klienta lub usługę, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] domyślnie używa magazynu certyfikatów systemu Windows i interfejsu API szyfrowania do weryfikacji certyfikatu i upewnij się, że jest zaufany. Czasami certyfikatu wbudowanych funkcji sprawdzania poprawności nie jest wystarczająco i musi zostać zmienione. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zapewnia łatwy sposób zmień logikę sprawdzania poprawności, pozwalając użytkownikom na dodawanie niestandardowego modułu weryfikacji certyfikatów. Jeśli określono niestandardowego modułu weryfikacji certyfikatów, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie korzysta z logikę weryfikacji certyfikatu wbudowanych, ale zamiast tego zależy niestandardowego modułu weryfikacji.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Aby utworzyć niestandardowego modułu weryfikacji certyfikatów  
  
1.  Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2.  Implementuje klasy abstrakcyjnej <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> metody. Certyfikat, który musi zostać zweryfikowany jest przekazywany jako argument do metody. Jeśli przekazany certyfikat jest nieprawidłowa według logiki sprawdzania poprawności, ta metoda zgłasza <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Jeśli certyfikat jest ważny, metoda zwraca wartość do obiektu wywołującego.  
  
    > [!NOTE]
    >  Aby przywrócić błędy uwierzytelniania z powrotem do klienta, throw <xref:System.ServiceModel.FaultException> w <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metody.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów w konfiguracji usługi  
  
1.  Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2.  Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu odpowiednią wartość.  
  
3.  Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` elementu.  
  
4.  Dodaj `<clientCertificate>` elementu `<serviceCredentials>` elementu.  
  
5.  Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` elementu.  
  
6.  Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności. Poniższy przykład ustawia atrybut przestrzeni nazw i nazwę typu.  
  
7.  Ustaw `certificateValidationMode` atrybutu `Custom`.  
  
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
  
1.  Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu i [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu.  
  
2.  Dodaj [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) elementu.  
  
3.  Dodaj `<behavior>` element i ustaw `name` atrybutu odpowiednią wartość.  
  
4.  Dodaj [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elementu.  
  
5.  Dodaj [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6.  Dodaj [ \<uwierzytelniania >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak pokazano w poniższym przykładzie.  
  
7.  Ustaw `customCertificateValidatorType` atrybutu typu modułu sprawdzania poprawności.  
  
8.  Ustaw `certificateValidationMode` atrybutu `Custom`. Poniższy przykład ustawia atrybut przestrzeni nazw i nazwę typu.  
  
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
  
1.  Określ niestandardowego modułu weryfikacji certyfikatów na <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> właściwości. Można uzyskać dostęp przy użyciu poświadczeń usługi <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
2.  Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Aby określić niestandardowego modułu weryfikacji certyfikatów na komputerze klienckim przy użyciu kodu  
  
1.  Określ niestandardowego modułu weryfikacji certyfikatów przy użyciu <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> właściwości. Można uzyskać dostępu do poświadczeń klienta przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości. (Klasa klienta generowane przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze pochodną <xref:System.ServiceModel.ClientBase%601> klasy.)  
  
2.  Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwości <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład przedstawia implementację niestandardowego modułu weryfikacji certyfikatów i ich użycia w usłudze.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>
