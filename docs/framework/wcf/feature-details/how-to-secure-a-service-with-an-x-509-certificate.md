---
title: 'Instrukcje: zabezpieczanie usługi za pomocą certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 75c7a0e50301ce80d51b9b2a10ed650a1600ec79
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300089"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Instrukcje: zabezpieczanie usługi za pomocą certyfikatu X.509
Zabezpieczanie usługi za pomocą certyfikatu X.509 to podstawowa technika, używanego przez większość powiązania w Windows Communication Foundation (WCF). W tym temacie przedstawiono kroki konfigurowania samodzielnie hostowanej usłudze przy użyciu certyfikatu X.509.  
  
 Warunkiem wstępnym jest prawidłowy certyfikat, który może służyć do uwierzytelniania serwera. Certyfikat musi być wystawiony na serwer przez zaufany urząd certyfikacji. Jeśli certyfikat nie jest prawidłowy, dowolny klient próbuje użyć usługi nie będzie zaufany usługi, a w związku z tym połączenie nie zostanie ustanowione. Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Aby skonfigurować usługę przy użyciu certyfikatu przy użyciu kodu  
  
1. Tworzenie kontraktu usługi i wdrożonych usług. Aby uzyskać więcej informacji, zobacz [projektowanie i Implementowanie usług](../../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
2. Utwórz wystąpienie obiektu <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń <xref:System.ServiceModel.SecurityMode.Message>, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. Utworzyć dwa <xref:System.Type> zmienne, jedną dla typu kontraktu i zaimplementowano kontraktu, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. Utwórz wystąpienie obiektu <xref:System.Uri> klasy dla podstawowego adresu usługi. Ponieważ `WSHttpBinding` używa transportu HTTP, jednolity identyfikator zasobów (URI) musi rozpoczynać się od tego schematu lub usług Windows Communication Foundation (WCF) spowoduje zgłoszenie wyjątku, gdy usługa jest otwarty.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. Utwórz nowe wystąpienie klasy <xref:System.ServiceModel.ServiceHost> klasy za pomocą zmiennej typu zaimplementowano umowy i identyfikator URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> do usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Przekaż kontraktu, powiązania i adresu punktu końcowego do konstruktora, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. Opcjonalna. Aby pobrać metadane z usługi, Utwórz nową <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiektu i ustaw <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> właściwość `true`.  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby dodać ważnego certyfikatu do usługi. Metoda może używać jednej z kilku metod można znaleźć certyfikatu. W tym przykładzie użyto <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> wyliczenia. Wyliczanie Określa, czy podana wartość jest nazwą jednostki, który został wystawiony certyfikat.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby rozpocząć nasłuchiwania usługi. Jeśli tworzysz aplikację konsolową w języku, należy wywołać <xref:System.Console.ReadLine%2A> metodę, aby zachować usługę w stanie nasłuchiwania.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodę, aby skonfigurować usługę za pomocą certyfikatu X.509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Następujące przestrzenie nazw są wymagane, aby skompilować kod:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
-   <xref:System.Web.Services.Description>  
  
-   <xref:System.Security.Cryptography.X509Certificates>  
  
-   <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Zobacz także

- [Praca z certyfikatami](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
