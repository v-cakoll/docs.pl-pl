---
title: 'Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: bb0190ff-0738-4e54-8d22-c97d343708bf
ms.openlocfilehash: b2407c293de7f11b90586f5a55bd759a4ea734aa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795678"
---
# <a name="how-to-create-a-service-that-employs-a-custom-certificate-validator"></a>Instrukcje: tworzenie usługi korzystającej z niestandardowego modułu weryfikacji certyfikatów
W tym temacie pokazano, jak zaimplementować niestandardowy moduł sprawdzania poprawności certyfikatu oraz jak skonfigurować poświadczenia klienta lub usługi w celu zastąpienia domyślnej logiki walidacji certyfikatu za pomocą niestandardowego modułu sprawdzania certyfikatu.  
  
 Jeśli certyfikat X. 509 jest używany do uwierzytelniania klienta lub usługi, Windows Communication Foundation (WCF) domyślnie używa magazynu certyfikatów systemu Windows i interfejsu API kryptografii do weryfikacji certyfikatu i upewnienia się, że jest zaufany. Czasami Wbudowana funkcja weryfikacji certyfikatu jest za mała i należy ją zmienić. Funkcja WCF zapewnia łatwy sposób zmiany logiki walidacji przez umożliwienie użytkownikom dodawania niestandardowego modułu weryfikacji certyfikatu. Jeśli jest określony niestandardowy moduł sprawdzania poprawności certyfikatu, funkcja WCF nie korzysta z wbudowanej logiki walidacji certyfikatu, ale zamiast tego używa niestandardowego modułu weryfikacji.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-certificate-validator"></a>Aby utworzyć niestandardowy moduł sprawdzania poprawności certyfikatu  
  
1. Zdefiniuj nową klasę pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.  
  
2. Zaimplementuj metodę <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> abstrakcyjną. Certyfikat, który musi zostać sprawdzony, jest przenoszona jako argument do metody. Jeśli przesłany certyfikat nie jest prawidłowy zgodnie z logiką walidacji, ta metoda zgłasza <xref:System.IdentityModel.Tokens.SecurityTokenValidationException>. Jeśli certyfikat jest prawidłowy, Metoda powraca do obiektu wywołującego.  
  
    > [!NOTE]
    > Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.  
  
 [!code-csharp[c_CustomCertificateValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#2)]
 [!code-vb[c_CustomCertificateValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#2)]  
  
#### <a name="to-specify-a-custom-certificate-validator-in-service-configuration"></a>Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu w konfiguracji usługi  
  
1. Dodaj zachowania > elementu i [ \<serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) . [ \<](../../configure-apps/file-schema/wcf/behaviors.md)  
  
2. `name` [ Dodaj\<zachowanie >](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw odpowiednią wartość atrybutu.  
  
3. Dodaj > ServiceCredentials do elementu.`<behavior>` [ \<](../../configure-apps/file-schema/wcf/servicecredentials.md)  
  
4. `<clientCertificate>` Dodaj element`<serviceCredentials>` do elementu.  
  
5. Dodaj [> uwierzytelniania do elementu. \<](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) `<clientCertificate>`  
  
6. `customCertificateValidatorType` Ustaw atrybut na typ walidacji. Poniższy przykład ustawia atrybut na przestrzeń nazw i nazwę typu.  
  
7. Ustaw atrybut na `Custom`. `certificateValidationMode`  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-configuration-on-the-client"></a>Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu konfiguracji na kliencie  
  
1. Dodaj zachowania > elementu i [ \<serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md) do [ \<elementu System. ServiceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) . [ \<](../../configure-apps/file-schema/wcf/behaviors.md)  
  
2. Dodaj element [> endpointBehaviors.\<](../../configure-apps/file-schema/wcf/endpointbehaviors.md)  
  
3. Dodaj element i ustaw odpowiednią wartość `name` atrybutu. `<behavior>`  
  
4. Dodaj element ClientCredentials >. [ \<](../../configure-apps/file-schema/wcf/clientcredentials.md)  
  
5. Dodaj > serviceCertificate. [ \<](../../configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)  
  
6. Dodaj > uwierzytelniania, jak pokazano w poniższym przykładzie. [ \<](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
7. `customCertificateValidatorType` Ustaw atrybut na typ walidacji.  
  
8. Ustaw atrybut na `Custom`. `certificateValidationMode` Poniższy przykład ustawia atrybut na przestrzeń nazw i nazwę typu.  
  
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
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-service"></a>Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu kodu w usłudze  
  
1. Określ niestandardowy moduł sprawdzania poprawności <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A> certyfikatu. Możesz uzyskać dostęp do poświadczeń usługi przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości.  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
 [!code-csharp[c_CustomCertificateValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#1)]
 [!code-vb[c_CustomCertificateValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#1)]  
  
#### <a name="to-specify-a-custom-certificate-validator-using-code-on-the-client"></a>Aby określić niestandardowy moduł sprawdzania poprawności certyfikatu przy użyciu kodu na kliencie  
  
1. Określ niestandardowy moduł sprawdzania poprawności certyfikatu przy <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> użyciu właściwości. Możesz uzyskać dostęp do poświadczeń klienta przy użyciu <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> właściwości. (Klasa klienta wygenerowana przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) zawsze pochodzi z <xref:System.ServiceModel.ClientBase%601> klasy.)  
  
2. Ustaw <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> właściwość <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom>.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład pokazuje implementację niestandardowego modułu weryfikacji certyfikatu i jego użycia w usłudze.  
  
### <a name="code"></a>Kod  
 [!code-csharp[c_CustomCertificateValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcertificatevalidator/cs/source.cs#3)]
 [!code-vb[c_CustomCertificateValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcertificatevalidator/vb/source.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.X509CertificateValidator>
