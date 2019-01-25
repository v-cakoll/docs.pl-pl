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
ms.openlocfilehash: 9fe999c4ee27d4a78bfad185fa3bcc065d74708a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643383"
---
# <a name="how-to-specify-the-client-credential-type"></a>Instrukcje: Określanie typu poświadczeń klienta
Po ustawieniu trybu zabezpieczeń (transportu lub wiadomości), istnieje możliwość ustawienia typu poświadczeń klienta. Ta właściwość określa, jakiego typu poświadczeń klienta należy podać usługi na potrzeby uwierzytelniania. Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń (niezbędne krok przed ustawieniem typu poświadczeń klienta), zobacz [jak: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Aby ustawić typ poświadczeń klienta w kodzie  
  
1.  Utwórz wystąpienie powiązania, które będzie używane przez usługę. W tym przykładzie użyto <xref:System.ServiceModel.WSHttpBinding> powiązania.  
  
2.  Ustaw <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> właściwość do odpowiedniej wartości. W tym przykładzie użyto trybu wiadomości.  
  
3.  Ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> właściwość do odpowiedniej wartości. W tym przykładzie go do korzystania z uwierzytelniania Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Aby ustawić typ poświadczeń klienta w konfiguracji  
  
1.  Dodaj [ \<system.serviceModel >](../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element do pliku konfiguracji.  
  
2.  Dodanie elementu podrzędnego [ \<powiązania >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.  
  
3.  Dodaj odpowiednie powiązanie. W tym przykładzie użyto [ \<wsHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) elementu.  
  
4.  Dodaj [ \<powiązania >](../../../docs/framework/misc/binding.md) element i ustaw `name` atrybutu do odpowiedniej wartości. W tym przykładzie używa nazwy "SecureBinding".  
  
5.  Dodaj `<security>` powiązania. Ustaw `mode` atrybutu do odpowiedniej wartości. W tym przykładzie ustawia ją na `"Message"`.  
  
6.  Dodaj opcję `<message>` lub `<transport>` elementu, zgodnie z ustaleniami tryb zabezpieczeń. Ustaw `clientCredentialType` atrybutu do odpowiedniej wartości. W tym przykładzie użyto `"Windows"`.  
  
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
- [Zabezpieczanie usług](../../../docs/framework/wcf/securing-services.md)
- [Instrukcje: Ustawianie trybu zabezpieczeń](../../../docs/framework/wcf/how-to-set-the-security-mode.md)
