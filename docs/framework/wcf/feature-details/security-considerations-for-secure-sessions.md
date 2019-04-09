---
title: Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: d2244ba42b1cf95f77424d32a19ebe11dd3a2a45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148710"
---
# <a name="security-considerations-for-secure-sessions"></a>Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji
Należy rozważyć następujące elementy, które dotyczą zabezpieczeń podczas implementowania bezpiecznej sesji. Aby uzyskać więcej informacji na temat zagadnień dotyczących zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) i [najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Bezpieczne sesje i metadane  
 Po ustanowieniu bezpiecznej sesji i <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `false`, Windows Communication Foundation (WCF) wysyła `mssp:MustNotSendCancel` potwierdzenie jako część metadane Web Services Description Language (WSDL) dokumentu w celu punkt końcowy usługi. `mssp:MustNotSendCancel` Potwierdzenie informuje klientów, usługa nie odpowiada na żądania anulowania bezpiecznej sesji. Gdy <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `true`, a następnie WCF nie emituje `mssp:MustNotSendCancel` potwierdzenia w dokumencie WSDL. Klienci powinni wysłać żądanie anulowania do usługi, gdy nie jest już wymagany bezpiecznej sesji. Gdy klient jest generowana z użyciem [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kod klienta odpowiednio reaguje na obecność lub Brak `mssp:MustNotSendCancel` potwierdzenia.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Bezpieczne konwersacje i tokeny niestandardowe  
 Występują problemy z mieszanie tokeny niestandardowe i kluczy pochodnych ze względu na sposób, który jest zdefiniowany w specyfikacji WS-SecureConversation. Specyfikacja twierdzi, że `wsse:SecurityTokenReference` jest elementem opcjonalnym, który odwołuje się do pochodny token: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` Ten opcjonalny element jest używany do określenia tokenu kontekstu zabezpieczeń, token zabezpieczający lub udostępnionych kluczy/wpisów tajnych używany do tworzenia elementów pochodnych. Jeśli nie zostanie określony, zakłada się, odbiorcy określić klucz współużytkowany z kontekstu wiadomości. Jeśli nie można ustalić kontekstu, następnie błędów, takich jak `wsc:UnknownDerivationSource` powinien być wywoływany. "  
  
 Oznacza to, że chcącym niestandardowy token pochodzić powinna opakować typ klauzuli w `SecurityTokenReference` elementu. Istnieje możliwość wyłączyć pochodnym, ale wartość domyślna to do tworzenia kluczy. Jeśli nie opakuj klucz, serializacji pochodny token klucza zakończy się pomyślnie, ale zgłasza wyjątek, próba deserializacji go.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
