---
title: "Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: be460249ed877b2f67f2d153c2aea4a3cc4d2b37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-secure-sessions"></a>Zagadnienia dotyczące zabezpieczeń bezpiecznych sesji
Należy rozważyć następujące elementy, które mają wpływ na zabezpieczeń podczas implementowania bezpiecznej sesji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]zagadnienia dotyczące zabezpieczeń, zobacz [zagadnienia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md) i [najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Bezpieczne sesje i metadane  
 Po ustanowieniu bezpiecznej sesji i <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `false`, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] wysyła `mssp:MustNotSendCancel` potwierdzenia jako część metadanych w dokumencie Web Services Description Language (WSDL) dla punktu końcowego usługi. `mssp:MustNotSendCancel` Potwierdzenia informuje klientów, że usługa nie odpowiada na żądania anulowania bezpiecznej sesji. Gdy <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> właściwość jest ustawiona na `true`, następnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie Emituj `mssp:MustNotSendCancel` potwierdzenia w dokumencie WSDL. Klienci powinni wysyłać żądania anulowania do usługi, gdy nie jest już wymagany bezpiecznej sesji. Gdy klient jest generowany przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), kod klienta odpowiednio reaguje na obecności lub braku `mssp:MustNotSendCancel` potwierdzenia.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Bezpieczne konwersacje i tokeny niestandardowe  
 Występują problemy z mieszanie tokeny niestandardowe i kluczy pochodnych ze względu na sposób, który jest zdefiniowany w specyfikacji WS-SecureConversation. Specyfikacja informacją, że `wsse:SecurityTokenReference` jest opcjonalny element, który odwołuje się do pochodny token: "`/wsc:DerivedKeyToken/wsse:SecurityTokenReference` to opcjonalny element jest używana do określania token kontekstu zabezpieczeń, token zabezpieczający lub wspólny klucz/klucz tajny używane wyprowadzenia. Jeśli nie zostanie określony, zakłada się, że odbiorca może określić klucza wspólnego z kontekstu wiadomości. Jeśli nie można ustalić kontekstu, następnie błędów takich jak `wsc:UnknownDerivationSource` powinien być wywoływany. "  
  
 Oznacza to, że należy niestandardowy token dziedziczyć możesz powinna być zawijana, jego typ klauzuli w `SecurityTokenReference` elementu. Ma opcji, aby wyłączyć tworzenie wartości pochodnych, ale wartość domyślna to do tworzenia kluczy. Nie Zawijaj klucz, serializacji pochodny token klucza zakończy się pomyślnie, ale podjęto próbę deserializacji zgłasza wyjątek.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: wyłączanie bezpiecznej sesji przy użyciu klasy WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 [Zagadnienia dotyczące bezpieczeństwa](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Najlepsze rozwiązania dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md)
