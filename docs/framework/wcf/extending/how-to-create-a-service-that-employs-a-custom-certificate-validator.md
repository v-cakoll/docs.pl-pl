---
title: 'Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: af1bb9b2ff793f6e6854c1b253dd445a35a5076f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185576"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Instrukcje: Tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów
W tym temacie pokazano, jak zaimplementować niestandardowy walidator certyfikatów i jak skonfigurować poświadczenia klienta lub usługi, aby zastąpić domyślną logikę sprawdzania poprawności certyfikatu niestandardowym.  
  
 Jeśli certyfikat X.509 jest używany do uwierzytelniania klienta lub usługi, Windows Communication Foundation (WCF) domyślnie używa magazynu certyfikatów systemu Windows i interfejsu API Crypto do sprawdzania poprawności certyfikatu i zapewnienia jego zaufania. Czasami wbudowana funkcja sprawdzania poprawności certyfikatu nie jest wystarczająca i należy ją zmienić. WCF zapewnia łatwy sposób, aby zmienić logikę sprawdzania poprawności, umożliwiając użytkownikom dodać niestandardowy walidator certyfikatów. Jeśli określono niestandardowy walidator certyfikatów, WCF nie używa wbudowanej logiki sprawdzania poprawności certyfikatu, ale zamiast tego opiera się na niestandardowym walidatorze.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Aby utworzyć niestandardowy walidator certyfikatów  
  
1. Zdefiniuj nową <xref:System.IdentityModel.Selectors.X509CertificateValidator>klasę pochodną .  
  
2. Zaimplementuj metodę abstrakcyjną. <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> Certyfikat, który musi zostać zweryfikowany, jest przekazywany jako argument do metody. Jeśli przekazany certyfikat nie jest prawidłowy zgodnie z logiką sprawdzania poprawności, ta metoda zgłasza <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Jeśli certyfikat jest prawidłowy, metoda zwraca do wywołującego.  
  
    > [!NOTE]
    > Aby przywrócić błędy uwierzytelniania do klienta, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> należy wrzucić metodę. <xref:System.ServiceModel.FaultException>  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Aby określić niestandardowy walidator certyfikatów w konfiguracji usługi  
  
1. Dodaj [ \<zachowanie>](../../configure-apps/file-schema/wcf/behaviors.md) element i [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Dodaj [ \<zachowanie>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybut na odpowiednią wartość.  
  
3. Dodaj [ \<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `<behavior>` elementu.  
  
4. Dodaj `<clientCertificate>` element do `<serviceCredentials>` elementu.  
  
5. Dodaj [ \<>uwierzytelniania](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) do `<clientCertificate>` elementu.  
  
6. Ustaw `customCertificateValidatorType` atrybut na typ walidatora. Poniższy przykład ustawia atrybut do obszaru nazw i nazwy typu.  
  
7. Ustaw `certificateValidationMode` atrybut na `Custom`.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Aby określić niestandardowy walidator certyfikatów przy użyciu konfiguracji na kliencie  
  
1. Dodaj [ \<zachowanie>](../../configure-apps/file-schema/wcf/behaviors.md) element i [ \<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu system.serviceModel>.](../../configure-apps/file-schema/wcf/system-servicemodel.md)  
  
2. Dodaj [ \<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) element.  
  
3. Dodaj `<behavior>` element i `name` ustaw atrybut na odpowiednią wartość.  
  
4. Dodaj [ \<element>clientCredentials.](../../configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. Dodaj [ \<>serviceCertificate ](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md).  
  
6. Dodaj [ \<>uwierzytelniania,](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) jak pokazano w poniższym przykładzie.  
  
7. Ustaw `customCertificateValidatorType` atrybut na typ walidatora.  
  
8. Ustaw `certificateValidationMode` atrybut na `Custom`. Poniższy przykład ustawia atrybut do obszaru nazw i nazwy typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Aby określić niestandardowy walidator certyfikatów przy użyciu kodu w usłudze  
  
1. Określ niestandardowy walidator certyfikatu <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> we właściwości. Można uzyskać dostęp do poświadczeń usługi za pomocą <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Aby określić niestandardowy walidator certyfikatów przy użyciu kodu na kliencie  
  
1. Określ niestandardowy walidator certyfikatu <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> przy użyciu właściwości. Można uzyskać dostęp do poświadczeń klienta przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości. (Klasa klienta generowana przez [narzędzie narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze wywodzi się z <xref:System.ServiceModel.ClientBase%601> klasy.  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>na .  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono implementację niestandardowego walidatora certyfikatów i jego użycie w usłudze.  
  
### <a name="code"></a>Code  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
