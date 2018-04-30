---
title: Federacja i zaufanie
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8ccd395f96f3e7af0ce7afe9938c0295d5778914
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="federation-and-trust"></a>Federacja i zaufanie
W tym temacie opisano różne aspekty związane z aplikacji federacyjnych, granice zaufania i Konfiguracja i użycie wystawionych tokenów w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="services-security-token-services-and-trust"></a>Usługi, usługi tokenu zabezpieczeń i zaufania  
 Usługi, które zwykle ekspozycji punktów końcowych, federacyjnych oczekiwać klientów do uwierzytelniania za pomocą dostarczonych przez konkretnego wystawcę tokenu. Należy pamiętać, że usługa jest skonfigurowana przy użyciu poprawnych poświadczeń wystawcy; w przeciwnym razie nie będzie możliwe do weryfikowania podpisów za pośrednictwem wystawionych tokenów, a klient będzie mogła nawiązać połączenia z usługą. Aby uzyskać więcej informacji na temat konfigurowania poświadczeń wystawcy dla usługi, zobacz [porady: Konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobnie przy użyciu kluczy symetrycznych, kluczy szyfrowania dla usługi docelowej, należy skonfigurować usługę tokenu zabezpieczającego z prawidłowymi poświadczeniami dla usługi docelowej; w przeciwnym razie będzie nie można zaszyfrować klucza dla usługi docelowej, a następnie ponownie, klient będzie mogła nawiązać połączenia z usługą.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi używają wartości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwość [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) umożliwiające zegara pochylenia między klientem a usługą. W Federacji `MaxClockSkew` ustawienie dotyczy pochyla zegara między zarówno klient, jak i usługi tokenu zabezpieczeń, z którym klient uzyskał wystawionego tokenu. W związku z tym usługi tokenu zabezpieczeń nie muszą wprowadzać dodatki niedokładność zegara, ustawiając czas wejścia w życie i wygaśnięcia wystawionego tokenu.  
  
> [!NOTE]
>  Ważność zegara zwiększa skraca czas istnienia wystawionego tokenu. W większości przypadków niedokładność zegara nie jest znaczny problem, jeśli okres istnienia tokenu jest 30 minut lub dłużej. Scenariusze z krótsze okresy istnienia lub których okres ważności dokładnego tokenu jest ważna należy tak zaprojektować uwzględnienie zegara pochylenia.  
  
## <a name="federated-endpoints-and-time-outs"></a>Punkty końcowe federacyjnych i limity czasu  
 Gdy klient komunikuje się z punktem końcowym federacyjnych, go najpierw uzyskać odpowiednią tokenu z usługi tokenu zabezpieczającego. Jeśli usługa tokenu zabezpieczającego przedstawia federacyjnych punktu końcowego, klient najpierw uzyskać tokenu od wystawcy dla tego punktu końcowego. Każdy token nabycia czas, i mogą ulec ogólny limit czasu dla wysyłania komunikatu rzeczywiste do końcowego punktu końcowego tego czasu.  
  
 Na przykład limit czasu kanału po stronie klienta wynosi 30 sekund. Dwa wystawców tokenów muszą zostać wywołane pobranie tokenów przed wysłaniem wiadomości do końcowego punktu końcowego, a każdy trwa 15 sekund wystawianie tokenów. W takim przypadku nie powiedzie się i <xref:System.TimeoutException> jest generowany. W związku z tym należy ustawić <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> wartość kanału klienta do wartości wystarczająco duży, by uwzględnić czas, w celu pobrania wszystkich wystawionych tokenów. W przypadku, gdy nie określono wartości dla <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> właściwość <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> właściwości lub <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> właściwości (lub obie) musi być ustawiona na wartość wystarczająco duży, aby uwzględnić czas potrzebny na pobranie wszystkich wystawionych tokenów.  
  
## <a name="token-lifetime-and-renewal"></a>Okres istnienia tokenu i odnawiania  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klienci nie zaznaczaj wystawiony token początkowej żądaniu skierowanym do usługi.  Zamiast [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relacje zaufania usługi tokenu zabezpieczającego wystawianie tokenów z właściwym czasie aktywacji i ważności. Jeśli token jest buforowana przez klienta i użyć ponownie, okres istnienia tokenu jest zaznaczony na kolejnych żądań i w razie potrzeby klient automatycznie odnawia tokenu. Aby uzyskać więcej informacji na temat buforowania tokenu, zobacz [porady: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Określenie krótkich okresów istnienia, w kolejności wynoszącą 30 sekund lub mniej wystawione tokeny lub tokenów kontekstów zabezpieczeń, może spowodować negocjacji przekroczeń limitu czasu lub inne wyjątki zgłaszane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów podczas żądania wystawione tokeny lub podczas negocjowania lub Odnawianie tokenów kontekstów zabezpieczeń.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Wystawione tokeny i InclusionMode  
 Określa, czy wystawionego tokenu jest serializowany w wiadomości wysłanych z klienta do punktu końcowego federacyjnych lub nie jest kontrolowany przez ustawienie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> właściwość <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Ta właściwość może należeć do jednej z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> wartości wyliczenia, ale nie jest przydatne w scenariuszach obejmujących Federację najbardziej. `SecurityTokenInclusionMode.Never` i `SecurityTokenInclusionMode.AlwaysToInitiator` wartości spowoduje to klientowi wysłanie odwołania do tokenu wystawiony przez usługę tokenu zabezpieczającego do jednostki uzależnionej. O ile uzależnionej posiada kopię wystawionego tokenu uwierzytelniania zakończy się niepowodzeniem, ponieważ nie można rozpoznać odwołania do tokenu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] traktuje `SecurityTokenInclusionMode.Once` jako równoważne `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>  
 [Instrukcje: tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Instrukcje: konfigurowanie poświadczeń usługi federacyjnej](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Instrukcje: tworzenie elementu WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
