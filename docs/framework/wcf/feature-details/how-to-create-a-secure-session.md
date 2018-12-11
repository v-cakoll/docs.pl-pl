---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: c0e5281d227d343d8734809b27b57d8a2bead627
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147597"
---
# <a name="how-to-create-a-secure-session"></a>Instrukcje: Tworzenie bezpiecznej sesji
Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązania powiązania dostarczane przez system w Windows Communication Foundation (WCF) automatycznie używać bezpiecznych sesji po włączeniu zabezpieczenia wiadomości.  
  
 Domyślnie bezpiecznych sesji nie przeżywa serwera sieci Web, która zostanie odtworzona. Podczas ustanawiania sesji bezpiecznego, klient i usługa pamięci podręcznej klucza, który jest skojarzony z bezpiecznej sesji. Ponieważ komunikaty są wymieniane, wymieniane są tylko identyfikator, aby klucz pamięci podręcznej. Jeśli serwer sieci Web zostanie odtworzona, pamięć podręczna jest recyklingowi, taki sposób, że serwer sieci Web nie może pobrać klucza pamięci podręcznej dla identyfikatora. Jeśli tak się stanie, wyjątek jest generowany ponownie do klienta. Bezpieczne sesje, które używają tokenu kontekstu zabezpieczeń stanową (SCT) może nie są unieważniane serwer sieci Web z odtwarzania. Aby uzyskać więcej informacji na temat w ramach bezpiecznej sesji przy użyciu stanowych SCT zobacz [jak: Utwórz kontekst zabezpieczeń tokenu dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Aby określić, że usługa używa bezpiecznej sesji przy użyciu jednej z powiązań dostarczanych przez system  
  
-   Skonfiguruj usługę do używania powiązania dostarczane przez system, które obsługuje zabezpieczenia wiadomości.  
  
     Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązania, kiedy powiązania dostarczane przez system są skonfigurowane do używania zabezpieczeń wiadomości, WCF, automatycznie używa bezpiecznych sesji. W poniższej tabeli wymieniono powiązania dostarczane przez system, które obsługują zabezpieczenia komunikatów i tego, czy zabezpieczenia wiadomości są domyślnego mechanizmu zabezpieczeń.  
  
    |Powiązania dostarczane przez system|Element konfiguracji|Zabezpieczenia komunikatów na domyślnie|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Nie|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Nie|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Nie|  
  
     Poniższy przykład kodu używa konfiguracji, aby określić powiązanie o nazwie `wsHttpBinding_Calculator` , który używa [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje.  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     Poniższy przykład kodu Określa, że [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje służą do zabezpieczania `secureCalculator` usługi.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Bezpieczne sesje mogą zostać wyłączone [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) , ustawiając `establishSecurityContext` atrybutu `false`. Dla innych powiązań dostarczanych przez system można tylko wyłączyć bezpiecznych sesji przez utworzenie niestandardowego powiązania.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Aby określić, że usługa używa bezpiecznej sesji przy użyciu niestandardowego powiązania  
  
-   Tworzenie niestandardowego powiązania, który określa, że komunikaty protokołu SOAP są chronione przez bezpiecznej sesji.  
  
     Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania, zobacz [jak: Dostosuj powiązania dostarczane przez System](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania tej wiadomości, przy użyciu bezpiecznej sesji.  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania uruchomienie bezpiecznej sesji.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md)
