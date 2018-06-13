---
title: Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: f4ee56204d6980f412b9781868714dedb3c2675c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497493"
---
# <a name="security-considerations-for-secure-sessions"></a>Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji
Należy rozważyć następujące elementy, które mają wpływ na zabezpieczeń podczas implementowania bezpiecznej sesji. Aby uzyskać więcej informacji na temat zagadnień dotyczących zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) i [najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Bezpieczne sesje i metadane  
 Po ustanowieniu bezpiecznej sesji i <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `false`, wysyła Windows Communication Foundation (WCF) `mssp:MustNotSendCancel` potwierdzenia jako część metadanych w dokumencie Web Services Description Language (WSDL) punkt końcowy usługi. `mssp:MustNotSendCancel` Potwierdzenia informuje klientów, że usługa nie odpowiada na żądania anulowania bezpiecznej sesji. Gdy <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `true`, a następnie WCF nie Emituj `mssp:MustNotSendCancel` potwierdzenia w dokumencie WSDL. Klienci powinni wysyłać żądania anulowania do usługi, gdy nie jest już wymagany bezpiecznej sesji. Gdy klient jest generowany przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kod klienta odpowiednio reaguje na obecności lub braku `mssp:MustNotSendCancel` potwierdzenia.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Bezpieczne konwersacje i tokeny niestandardowe  
 Występują problemy z mieszanie tokeny niestandardowe i kluczy pochodnych ze względu na sposób, który jest zdefiniowany w specyfikacji WS-SecureConversation. Specyfikacja informacją, że `wsse:SecurityTokenReference` jest opcjonalny element, który odwołuje się do pochodny token: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` to opcjonalny element jest używana do określania token kontekstu zabezpieczeń, token zabezpieczający lub wspólny klucz/klucz tajny używane wyprowadzenia. Jeśli nie zostanie określony, zakłada się, że odbiorca może określić klucza wspólnego z kontekstu wiadomości. Jeśli nie można ustalić kontekstu, następnie błędów takich jak `wsc:UnknownDerivationSource` powinien być wywoływany. "  
  
 Oznacza to, że należy niestandardowy token dziedziczyć możesz powinna być zawijana, jego typ klauzuli w `SecurityTokenReference` elementu. Ma opcji, aby wyłączyć tworzenie wartości pochodnych, ale wartość domyślna to do tworzenia kluczy. Nie Zawijaj klucz, serializacji pochodny token klucza zakończy się pomyślnie, ale podjęto próbę deserializacji zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
