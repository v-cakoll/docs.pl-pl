---
title: 'Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2d06c2aa-d0d7-4e5e-ad7e-77416aa1c10b
ms.openlocfilehash: 10d6db63368ee55040f85f922b9483982e8ff264
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596971"
---
# <a name="how-to-secure-a-service-with-an-x509-certificate"></a>Instrukcje: Zabezpieczanie usługi za pomocą certyfikatu X.509
Zabezpieczanie usługi za pomocą certyfikatu X. 509 jest podstawową techniką, która jest używana w większości powiązań w Windows Communication Foundation (WCF). W tym temacie przedstawiono kroki konfigurowania usługi samodzielnej przy użyciu certyfikatu X. 509.  
  
 Warunek wstępny jest prawidłowym certyfikatem, którego można użyć do uwierzytelnienia serwera. Certyfikat musi zostać wystawiony dla serwera przez zaufany urząd certyfikacji. Jeśli certyfikat jest nieprawidłowy, każdy klient próbujący skorzystać z usługi nie będzie ufać usłudze i w związku z tym nie zostanie nawiązane żadne połączenie. Aby uzyskać więcej informacji o korzystaniu z certyfikatów, zobacz [Praca z certyfikatami](working-with-certificates.md).  
  
### <a name="to-configure-a-service-with-a-certificate-using-code"></a>Aby skonfigurować usługę z certyfikatem przy użyciu kodu  
  
1. Utwórz kontrakt usługi i zaimplementowaną usługę. Aby uzyskać więcej informacji, zobacz [projektowanie i implementowanie usług](../designing-and-implementing-services.md).  
  
2. Utwórz wystąpienie <xref:System.ServiceModel.WSHttpBinding> klasy i ustaw jego tryb zabezpieczeń na <xref:System.ServiceModel.SecurityMode.Message> , jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#1)]
     [!code-vb[C_SecureWithCertificate#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#1)]  
  
3. Utwórz dwie <xref:System.Type> zmienne, jeden dla typu kontraktu i zaimplementowany kontrakt, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#2)]
     [!code-vb[C_SecureWithCertificate#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#2)]  
  
4. Utwórz wystąpienie <xref:System.Uri> klasy dla adresu podstawowego usługi. Ponieważ `WSHttpBinding` korzysta z transportu HTTP, Uniform Resource Identifier (URI) musi rozpoczynać się od tego schematu lub Windows Communication Foundation (WCF) zgłosi wyjątek, gdy usługa zostanie otwarta.  
  
     [!code-csharp[C_SecureWithCertificate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#3)]
     [!code-vb[C_SecureWithCertificate#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#3)]  
  
5. Utwórz nowe wystąpienie <xref:System.ServiceModel.ServiceHost> klasy z zaimplementowaną zmienną typu kontraktu i identyfikatorem URI.  
  
     [!code-csharp[C_SecureWithCertificate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#4)]
     [!code-vb[C_SecureWithCertificate#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#4)]  
  
6. Dodaj <xref:System.ServiceModel.Description.ServiceEndpoint> do usługi za pomocą <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> metody. Przekaż kontrakt, powiązanie i adres punktu końcowego do konstruktora, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[C_SecureWithCertificate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#5)]
     [!code-vb[C_SecureWithCertificate#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#5)]  
  
7. Opcjonalny. Aby pobrać metadane z usługi, należy utworzyć nowy <xref:System.ServiceModel.Description.ServiceMetadataBehavior> obiekt i ustawić <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> Właściwość na `true` .  
  
     [!code-csharp[C_SecureWithCertificate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#6)]
     [!code-vb[C_SecureWithCertificate#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#6)]  
  
8. Użyj <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metody <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> klasy, aby dodać prawidłowy certyfikat do usługi. Metoda może korzystać z jednej z kilku metod w celu znalezienia certyfikatu. W tym przykładzie zastosowano <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> Wyliczenie. Wyliczenie określa, że podana wartość jest nazwą jednostki, w której został wystawiony certyfikat.  
  
     [!code-csharp[C_SecureWithCertificate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#7)]
     [!code-vb[C_SecureWithCertificate#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#7)]  
  
9. Wywołaj <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> metodę, aby rozpocząć nasłuchiwanie usługi. Jeśli tworzysz aplikację konsolową, wywołaj metodę, <xref:System.Console.ReadLine%2A> Aby zachować stan nasłuchiwania.  
  
     [!code-csharp[C_SecureWithCertificate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#8)]
     [!code-vb[C_SecureWithCertificate#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> metodę w celu skonfigurowania usługi przy użyciu certyfikatu X. 509.  
  
 [!code-csharp[C_SecureWithCertificate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securewithcertificate/cs/source.cs#9)]
 [!code-vb[C_SecureWithCertificate#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securewithcertificate/vb/source.vb#9)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Do skompilowania kodu wymagane są następujące przestrzenie nazw:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
- <xref:System.Web.Services.Description>  
  
- <xref:System.Security.Cryptography.X509Certificates>  
  
- <xref:System.Runtime.Serialization>  
  
## <a name="see-also"></a>Zobacz też

- [Praca z certyfikatami](working-with-certificates.md)
