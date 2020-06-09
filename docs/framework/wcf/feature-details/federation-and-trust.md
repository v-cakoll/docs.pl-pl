---
title: Federacja i zaufanie
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 8b924a4aeb9c667592e99d65666cd8f048d34c22
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595482"
---
# <a name="federation-and-trust"></a>Federacja i zaufanie
W tym temacie omówiono różne aspekty związane z aplikacjami federacyjnymi, granicami zaufania i konfiguracją oraz korzystanie z wystawionych tokenów w programie Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Usługi, usługi tokenów zabezpieczających i relacje zaufania  
 Usługi, które uwidaczniają federacyjne punkty końcowe zwykle, oczekują klientom na uwierzytelnianie przy użyciu tokenu dostarczonego przez określonego wystawcy. Należy pamiętać, że usługa jest skonfigurowana z prawidłowymi poświadczeniami dla wystawcy. w przeciwnym razie nie będzie można sprawdzić podpisów wystawionych tokenów i klient nie będzie mógł komunikować się z usługą. Aby uzyskać więcej informacji na temat konfigurowania poświadczeń wystawcy w usłudze, zobacz [How to: Configure Credentials in a a usługa federacyjna](how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobnie w przypadku używania kluczy symetrycznych klucze są szyfrowane dla usługi docelowej, dlatego należy skonfigurować usługę tokenu zabezpieczającego z prawidłowymi poświadczeniami dla usługi docelowej. w przeciwnym razie nie będzie można zaszyfrować klucza dla usługi docelowej, a następnie klient nie będzie mógł nawiązać połączenia z usługą.  
  
 Usługi WCF używają wartości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwości w [elementu SecurityBindingElement](../diagnostics/wmi/securitybindingelement.md) , aby umożliwić pochylenie zegara między klientem i usługą. W Federacji `MaxClockSkew` ustawienie ma zastosowanie do obchylania zegara między klientem a usługą tokenu zabezpieczającego, z poziomu którego klient uzyskał wystawiony token. W związku z tym usługi tokenu zabezpieczającego nie muszą naliczać się na opóźnienie naliczania zegara podczas ustawiania czasu obowiązywania i wygaśnięcia wystawionego tokenu.  
  
> [!NOTE]
> Znaczenie pochylenia zegara zwiększa się w miarę skrócenia okresu istnienia wystawionego tokenu. W większości przypadków pochylenie zegara nie jest istotnym problemem, jeśli okres istnienia tokenu wynosi 30 minut lub dłużej. Scenariusze o krótszych okresach istnienia lub o dokładnym czasie ważności tokenu należy zastanowić się, aby przechylić do konta.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federacyjne punkty końcowe i limity czasu  
 Gdy klient komunikuje się z federacyjnym punktem końcowym, musi najpierw uzyskać odpowiedni token z usługi tokenu zabezpieczającego. Jeśli usługa token zabezpieczający ujawnia federacyjny punkt końcowy, klient musi najpierw uzyskać token z wystawcy dla tego punktu końcowego. Każdy pozyskiwanie tokenu trwa, a ten czas jest uzależniony od całkowitego limitu czasu wysyłania rzeczywistej wiadomości do końcowego punktu końcowego.  
  
 Na przykład limit czasu w kanale po stronie klienta jest ustawiony na 30 sekund. Dwa wystawcy tokenów należy wywołać, aby pobrać tokeny przed wysłaniem komunikatu do końcowego punktu końcowego, a każdy z nich zajmie 15 sekund, aby wystawić token. W takim przypadku próba zakończy się niepowodzeniem i <xref:System.TimeoutException> zostanie zgłoszony. W tym celu należy ustawić <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> wartość w kanale klienta na wartość wystarczającą do uwzględnienia czasu pobrania wszystkich wystawionych tokenów. W przypadku, gdy wartość nie jest określona dla <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> właściwości, <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> Właściwość lub <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> Właściwość (lub obie) musi być ustawiona na wartość wystarczająco duża, aby uwzględnić czas potrzebny do pobrania wszystkich wystawionych tokenów.  
  
## <a name="token-lifetime-and-renewal"></a>Okres istnienia tokenu i odnowienie  
 Klienci WCF nie sprawdzają wystawionego tokenu podczas wykonywania początkowego żądania do usługi.  Zamiast tego WCF ufa usłudze tokenu zabezpieczającego, aby wystawić token z odpowiednimi godzinami obowiązywania i wygaśnięcia. Jeśli token jest buforowany przez klienta i ponownie używany, okres istnienia tokenu jest sprawdzany w kolejnych żądaniach, a klient automatycznie odnawia token w razie potrzeby. Aby uzyskać więcej informacji na temat buforowania tokenów, zobacz [How to: Create a Federation Client](how-to-create-a-federated-client.md).  
  
 Określenie krótkich okresów istnienia w kolejności co najmniej 30 sekund dla wystawionych tokenów lub tokenów kontekstu zabezpieczeń może spowodować przekroczenie limitu czasu negocjacji lub innych wyjątków zgłaszanych przez klientów programu WCF podczas żądania wystawionych tokenów lub podczas negocjowania lub odnawiania tokenów kontekstu zabezpieczeń.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Wystawione tokeny i przełączenie  
 Czy wystawiony token jest serializowany w wiadomości wysyłanej z klienta do federacyjnego punktu końcowego lub nie jest kontrolowany przez ustawienie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> właściwości <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Tę właściwość można ustawić na jedną z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> wartości wyliczenia, ale nie jest ona przydatna w większości scenariuszy federacyjnych. `SecurityTokenInclusionMode.Never`Wartości i `SecurityTokenInclusionMode.AlwaysToInitiator` powodują, że klient wysyła odwołanie do tokenu wystawionego przez usługę tokenu zabezpieczeń dla jednostki uzależnionej. Jeśli jednostka uzależniona nie posiada kopii wystawionego tokenu, uwierzytelnienie nie powiedzie się, ponieważ nie można rozpoznać odwołania do tokenu. WCF traktuje `SecurityTokenInclusionMode.Once` się jako równoważne `SecurityTokenInclusionMode.AlwaysToRecipient` .  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Instrukcje: tworzenie klienta federacyjnego](how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie poświadczeń usługi federacyjnej](how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: tworzenie elementu WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)
