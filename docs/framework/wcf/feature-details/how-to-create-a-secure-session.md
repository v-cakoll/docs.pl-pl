---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
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
helpviewer_keywords: security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: cd4f91ef5389dd4b8ecb63c1148d3a86918f2d10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-secure-session"></a>Instrukcje: Tworzenie bezpiecznej sesji
Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, powiązania dostarczane przez system w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatycznie użyj bezpiecznych sesji po włączeniu zabezpieczeń wiadomości.  
  
 Domyślnie bezpiecznej sesji po serwera sieci Web, który zostanie odtworzony. Podczas ustanawiania sesji bezpiecznych, klient i usługa pamięci podręcznej klucza, który jest skojarzony z bezpieczną sesję. Jak komunikaty są wymieniane, są przekazywane tylko identyfikator, aby klucz pamięci podręcznej. Jeśli serwer sieci Web zostanie odtworzony, pamięci podręcznej odtworzeniem również, tak, aby serwer sieci Web nie może pobrać klucz pamięci podręcznej dla identyfikatora. W takim przypadku jest zwracany wyjątek powrotem do klienta. Serwer sieci Web odtwarzane przełączniki bezpiecznych sesji, które używają token kontekstu zabezpieczeń stanową (SCT). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]w ramach bezpiecznej sesji przy użyciu stanowe SCT zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Aby określić, że usługa używa bezpiecznych sesji przy użyciu jednego powiązania dostarczane przez system  
  
-   Skonfiguruj usługę do używania wiązania dostarczane przez system, które obsługuje zabezpieczenia wiadomości.  
  
     Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, gdy powiązania dostarczane przez system są skonfigurowane do korzystania z zabezpieczeń wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie używa bezpiecznych sesji. W poniższej tabeli wymieniono powiązania dostarczane przez system obsługi zabezpieczeń komunikatów i określa, czy zabezpieczenia wiadomości są domyślnego mechanizmu zabezpieczeń.  
  
    |Powiązania dostarczane przez system|Element konfiguracji|Zabezpieczenia komunikatów na domyślnie|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Nie|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Nie|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Nie|  
  
     Poniższy przykład kodu wykorzystuje konfiguracji, aby określić powiązanie o nazwie `wsHttpBinding_Calculator` używającą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje.  
  
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
  
     Poniższy przykład kodu Określa, że [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje są używane do zabezpieczania `secureCalculator` usługi.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  Bezpieczne sesje, można wyłączyć dla [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) przez ustawienie `establishSecurityContext` atrybutu `false`. Dla innych dostarczane przez system powiązań można tylko wyłączyć bezpiecznej sesji przez utworzenie niestandardowego powiązania.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Aby określić, że usługa używa bezpiecznych sesji przy użyciu wiązania niestandardowego  
  
-   Tworzenie niestandardowego powiązania, który określa, że wiadomości SOAP są chronione przez bezpiecznej sesji.  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie niestandardowego powiązania, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).  
  
     Poniższy przykład kodu wykorzystuje konfiguracji do określenia niestandardowego powiązania tej wiadomości za pomocą bezpiecznej sesji.  
  
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
  
     Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania do ładowania początkowego bezpiecznej sesji.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md)
