---
title: Federacja i zaufanie
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 4e1529db6cc52b6b8cc8881d2b2a35a754b4b311
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225342"
---
# <a name="federation-and-trust"></a>Federacja i zaufanie
W tym temacie omówiono różne aspekty związane z aplikacji federacyjnych, granice zaufania i konfiguracji i użytkowania wystawione tokeny w Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Usługi, usługach tokenów zabezpieczeń i zaufania  
 Usługi, które uwidaczniają federacyjne punkty końcowe zwykle oczekiwać klientom uwierzytelnianie przy użyciu tokenu przekazanego przez określonego wystawcę. Jest ważne, że usługa jest skonfigurowana z prawidłowymi poświadczeniami dla wystawcy; w przeciwnym razie nie będzie w stanie do weryfikowania podpisów za pośrednictwem wystawione tokeny i klient będzie mógł komunikować się z usługą. Aby uzyskać więcej informacji na temat konfigurowania poświadczeń wystawcy na usługę zobacz [jak: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobnie podczas korzystania z kluczy symetrycznych klucze pozostają zaszyfrowane dla usługi docelowej, dlatego należy skonfigurować usługę tokenu zabezpieczającego z prawidłowymi poświadczeniami dla usługi docelowej; w przeciwnym razie będzie nie można zaszyfrować klucza dla usługi docelowej, a następnie ponownie, klient będzie mógł komunikować się z usługą.  
  
 Usługi WCF, użyj wartości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) umożliwiające zegara niesymetryczność między klientem a usługą. W Federacji `MaxClockSkew` ustawienie ma zastosowanie do pochyla zegara, między klienta i usługi tokenu zabezpieczeń, z którym klient uzyskał wystawiony token. W związku z tym usługach tokenów zabezpieczeń nie muszą wprowadzać przestrzeganie przesunięcia czasowego zegara podczas ustawiania czasu aktywacji i wygaśnięcia wystawiony token.  
  
> [!NOTE]
>  Ważność zegara zwiększa się podczas skraca czas istnienia wystawionego tokenu. W większości przypadków przesunięcia czasowego zegara nie stanowi problemu istotne, jeśli czas życia tokenu jest 30 minut lub dłużej. Scenariusze obejmujące usługę krótsze okresy istnienia lub których okres ważności dokładnie tokenu jest ważna, powinny zostać tak zaprojektowane, uwzględnienie zegara pochylenia.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federacyjne punkty końcowe oraz przekroczeń limitu czasu  
 Gdy klient komunikuje się z punktem końcowym federacyjnego, go najpierw uzyskać odpowiedni token z usługi tokenu zabezpieczającego. Jeśli usługa tokenu zabezpieczającego udostępnia federacyjny punkt końcowy, klient najpierw należy uzyskać token od wystawcy dla tego punktu końcowego. Każdy uzyskanie tokenu jest czasochłonne i czasu ulec ogólny limit czasu wysyłania komunikat rzeczywiste ostatnim punktem końcowym.  
  
 Na przykład limit czasu na kanale po stronie klienta jest ustawiona na 30 sekund. Dwa wystawcy tokenów muszą zostać wywołane do pobierania tokenów przed wysłaniem wiadomości do końcowego punktu końcowego, a każda trwa 15 sekund na wystawienie tokena. W tym przypadku nie powiedzie się i <xref:System.TimeoutException> zgłaszany. W związku z tym, należy ustawić <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> wartość kanału klienta z wartością wystarczająco duży, aby uwzględnić czas poświęcony na pobieranie wszystkich wystawionych tokenów. W przypadku, gdy nie określono wartości dla <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> właściwości <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> właściwości lub <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> właściwości (lub obie) należy ustawić na wartość wystarczająco duży, aby uwzględnić czas poświęcony na pobieranie wszystkich wystawionych tokenów.  
  
## <a name="token-lifetime-and-renewal"></a>Okres istnienia tokenu i odnawiania  
 Klienci WCF nie sprawdzają wystawiony token podczas nawiązywania początkowego żądania do usługi.  Zamiast WCF ufa usługę tokenu zabezpieczającego wystawianie tokenów odpowiedni czas wejścia w życie i wygaśnięcia. Jeśli token jest buforowane przez klienta, a następnie ponownie, okres istnienia tokenu jest zaznaczone dla kolejnych żądań, a klient automatycznie odnawia token Jeśli to konieczne. Aby uzyskać więcej informacji na temat buforowania tokenu, zobacz [jak: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Określanie krótkie okresy istnienia, rzędu kilku 30 sekund lub mniej, wystawione tokeny lub tokeny kontekstu zabezpieczeń, może spowodować negocjacji przekroczeń limitu czasu lub inne wyjątki zgłaszane przez klientów usługi WCF, gdy żądanie wystawionych tokenów lub podczas negocjowania lub odnawianie zabezpieczeń tokeny kontekstu.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Wystawione tokeny i InclusionMode  
 Wystawiony token jest serializowana we wiadomości wysłane przez klienta do punktu końcowego federacyjnego czy nie jest kontrolowane przez ustawienie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> właściwość <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Tę właściwość można ustawić na jedną z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> wartości wyliczenia, ale nie jest użyteczny w scenariuszach obejmujących Federację najbardziej. `SecurityTokenInclusionMode.Never` i `SecurityTokenInclusionMode.AlwaysToInitiator` wartości spowoduje to klientowi wysłanie odwołania do tokenu wystawionego przez usługę tokenu zabezpieczającego do jednostki uzależnionej. Chyba że uzależnionej posiada kopię wystawionych tokenów, uwierzytelnianie zakończy się niepowodzeniem, ponieważ nie można rozpoznać odwołania do tokenu. Traktuje WCF `SecurityTokenInclusionMode.Once` za równoważny `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
