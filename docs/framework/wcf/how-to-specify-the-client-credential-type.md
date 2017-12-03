---
title: "Instrukcje: Określanie typu poświadczeń klienta"
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
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c6959ec7f2226f0d6554e9210b3ee1311871cdcf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-specify-the-client-credential-type"></a>Instrukcje: Określanie typu poświadczeń klienta
Po ustawieniu trybu zabezpieczeń (transportu lub wiadomości), istnieje możliwość ustawienia typu poświadczeń klienta. Ta właściwość określa, jaki typ poświadczenia, klient musi dostarczyć z usługą uwierzytelniania. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Ustawienie trybu zabezpieczeń (krokiem przed ustawieniem Typ poświadczeń klienta), zobacz [porady: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Aby ustawić typ poświadczeń klienta w kodzie  
  
1.  Utwórz wystąpienie powiązania, które będzie używane przez usługę. W tym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding> powiązania.  
  
2.  Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwości odpowiednią wartość. W tym przykładzie tryb wiadomości.  
  
3.  Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwości odpowiednią wartość. W tym przykładzie go do korzystania z uwierzytelniania systemu Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Aby ustawić typ poświadczeń klienta w konfiguracji  
  
1.  Dodaj [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu do pliku konfiguracji.  
  
2.  Dodanie elementu podrzędnego [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
3.  Dodaj odpowiednie powiązanie. W tym przykładzie użyto [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.  
  
4.  Dodaj [ \<powiązania >](../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu odpowiednią wartość. W tym przykładzie używane są nazwy "SecureBinding".  
  
5.  Dodaj `<security>` powiązania. Ustaw `mode` atrybutu odpowiednią wartość. W tym przykładzie ustawia ją na `"Message"`.  
  
6.  Dodaj albo `<message>` lub `<transport>` element, zgodnie z ustaleniami trybu zabezpieczeń. Ustaw `clientCredentialType` atrybutu odpowiednią wartość. W tym przykładzie użyto `"Windows"`.  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)  
 [Porady: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
