---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593415"
---
# <a name="how-to-create-a-secure-session"></a>Instrukcje: Tworzenie bezpiecznej sesji
Z wyjątkiem [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) powiązania, dostarczone przez system powiązania w Windows Communication Foundation (WCF) automatycznie używają bezpiecznych sesji, gdy włączono zabezpieczenia komunikatów.  
  
 Domyślnie bezpieczne sesje nie przeżyły serwera sieci Web, który jest odtwarzany ponownie. Po ustanowieniu bezpiecznej sesji klient i usługa buforują klucz skojarzony z bezpieczną sesją. Podczas wymiany komunikatów wymieniany jest tylko identyfikator klucza w pamięci podręcznej. Jeśli serwer sieci Web jest odtwarzany ponownie, pamięć podręczna jest również odtwarzana w taki sposób, że serwer sieci Web nie może pobrać klucza buforowanego identyfikatora. W takim przypadku wyjątek jest zgłaszany z powrotem do klienta. Bezpieczne sesje korzystające z tokenu stanowego kontekstu zabezpieczeń (SCT) mogą przetrwać serwer sieci Web, który jest odtwarzany. Aby uzyskać więcej informacji na temat używania stanowego SCT w bezpiecznej sesji, zobacz [How to: Create a Security Context token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>Aby określić, że usługa używa zabezpieczonych sesji przy użyciu jednego z powiązań dostarczonych przez system  
  
- Skonfiguruj usługę do korzystania z powiązania dostarczonego przez system, które obsługuje zabezpieczenia komunikatów.  
  
     Z wyjątkiem [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) powiązania, gdy powiązania dostarczone z systemem są skonfigurowane do korzystania z zabezpieczeń wiadomości, WCF automatycznie używa bezpiecznych sesji. Poniższa tabela zawiera listę powiązań dostarczonych przez system, które obsługują zabezpieczenia komunikatów i czy zabezpieczenia komunikatów są domyślnym mechanizmem zabezpieczeń.  
  
    |Powiązanie dostarczone przez system|Element konfiguracji|Zabezpieczenia komunikatów domyślnie włączone|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|Nie|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Tak|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|Nie|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|Nie|  
  
     Poniższy przykład kodu używa konfiguracji w celu określenia powiązania o nazwie `wsHttpBinding_Calculator` , który używa [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , zabezpieczeń komunikatów i zabezpieczonych sesji.  
  
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
  
     Poniższy przykład kodu określa, że [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) zabezpieczenia komunikatów i bezpieczne sesje są używane do zabezpieczenia `secureCalculator` usługi.  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > Bezpieczne sesje można wyłączyć, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ustawiając `establishSecurityContext` atrybut na `false` . W przypadku innych powiązań dostarczonych z systemem bezpieczne sesje można wyłączyć tylko przez utworzenie niestandardowego powiązania.  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>Aby określić, że usługa używa zabezpieczonych sesji przy użyciu niestandardowego powiązania  
  
- Utwórz niestandardowe powiązanie, które określa, że wiadomości protokołu SOAP są chronione przez bezpieczną sesję.  
  
     Aby uzyskać więcej informacji na temat tworzenia niestandardowego powiązania, zobacz [How to: Dostosowywanie podanego przez system powiązania](../extending/how-to-customize-a-system-provided-binding.md).  
  
     Poniższy przykład kodu używa konfiguracji do określenia niestandardowego powiązania, które wiadomości używają bezpiecznej sesji.  
  
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
  
     Poniższy przykład kodu tworzy niestandardowe powiązanie, które używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> trybu uwierzytelniania do uruchamiania bezpiecznej sesji.  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie powiązań WCF](../bindings-overview.md)
