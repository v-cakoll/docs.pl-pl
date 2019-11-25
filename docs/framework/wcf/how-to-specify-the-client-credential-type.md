---
title: 'Instrukcje: Określanie typu poświadczeń klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: df18f89ee18bfa33ecc0aced617d168c805e3515
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138579"
---
# <a name="how-to-specify-the-client-credential-type"></a>Instrukcje: Określanie typu poświadczeń klienta
Po ustawieniu trybu zabezpieczeń (transport lub wiadomość) można ustawić typ poświadczeń klienta. Ta właściwość określa typ poświadczeń, które klient musi przekazać do usługi w celu uwierzytelnienia. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń (wymaganego kroku przed ustawieniem typu poświadczeń klienta), zobacz [How to: Set a Security Mode](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Aby ustawić typ poświadczeń klienta w kodzie  
  
1. Utwórz wystąpienie powiązania, które będzie używane przez usługę. Ten przykład używa powiązania <xref:System.ServiceModel.WSHttpBinding>.  
  
2. Ustaw właściwość <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> na odpowiednią wartość. W tym przykładzie jest stosowany tryb wiadomości.  
  
3. Ustaw właściwość <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na odpowiednią wartość. Ten przykład służy do ustawiania uwierzytelniania systemu Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Aby ustawić typ poświadczeń klienta w konfiguracji  
  
1. Dodaj element [\<system. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) do pliku konfiguracji.  
  
2. Jako element podrzędny Dodaj element [\<powiązania >](../configure-apps/file-schema/wcf/bindings.md) .  
  
3. Dodaj odpowiednie powiązanie. W tym przykładzie używa elementu [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .  
  
4. Dodaj element [> powiązania\<](../configure-apps/file-schema/wcf/bindings.md) i ustaw odpowiednią wartość atrybutu `name`. Ten przykład używa nazwy "SecureBinding".  
  
5. Dodaj powiązanie `<security>`. Ustaw dla atrybutu `mode` odpowiednią wartość. Ten przykład ustawia go na `"Message"`.  
  
6. Dodaj element `<message>` lub `<transport>`, zgodnie z trybem zabezpieczeń. Ustaw dla atrybutu `clientCredentialType` odpowiednią wartość. Ten przykład używa `"Windows"`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług](securing-services.md)
- [Instrukcje: ustawianie trybu zabezpieczeń](how-to-set-the-security-mode.md)
