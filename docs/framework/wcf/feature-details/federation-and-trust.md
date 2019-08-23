---
title: Federacja i zaufanie
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 95c50ac5f402114925d3350f258f03caca4592ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948068"
---
# <a name="federation-and-trust"></a>Federacja i zaufanie
W tym temacie omówiono różne aspekty związane z aplikacjami federacyjnymi, granicami zaufania i konfiguracją oraz korzystanie z wystawionych tokenów w programie Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Usługi, usługi tokenów zabezpieczających i relacje zaufania  
 Usługi, które uwidaczniają federacyjne punkty końcowe zwykle, oczekują klientom na uwierzytelnianie przy użyciu tokenu dostarczonego przez określonego wystawcy. Należy pamiętać, że usługa jest skonfigurowana z prawidłowymi poświadczeniami dla wystawcy. w przeciwnym razie nie będzie można sprawdzić podpisów wystawionych tokenów i klient nie będzie mógł komunikować się z usługą. Aby uzyskać więcej informacji na temat konfigurowania poświadczeń wystawcy w [usłudze, zobacz How to: Skonfiguruj poświadczenia na usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobnie w przypadku używania kluczy symetrycznych klucze są szyfrowane dla usługi docelowej, dlatego należy skonfigurować usługę tokenu zabezpieczającego z prawidłowymi poświadczeniami dla usługi docelowej. w przeciwnym razie nie będzie można zaszyfrować klucza dla usługi docelowej, a następnie klient nie będzie mógł nawiązać połączenia z usługą.  
  
 Usługi WCF używają wartości <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> właściwości w [elementu SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) , aby umożliwić pochylenie zegara między klientem i usługą. W Federacji `MaxClockSkew` ustawienie ma zastosowanie do obchylania zegara między klientem a usługą tokenu zabezpieczającego, z poziomu którego klient uzyskał wystawiony token. W związku z tym usługi tokenu zabezpieczającego nie muszą naliczać się na opóźnienie naliczania zegara podczas ustawiania czasu obowiązywania i wygaśnięcia wystawionego tokenu.  
  
> [!NOTE]
> Znaczenie pochylenia zegara zwiększa się w miarę skrócenia okresu istnienia wystawionego tokenu. W większości przypadków pochylenie zegara nie jest istotnym problemem, jeśli okres istnienia tokenu wynosi 30 minut lub dłużej. Scenariusze o krótszych okresach istnienia lub o dokładnym czasie ważności tokenu należy zastanowić się, aby przechylić do konta.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federacyjne punkty końcowe i limity czasu  
 Gdy klient komunikuje się z federacyjnym punktem końcowym, musi najpierw uzyskać odpowiedni token z usługi tokenu zabezpieczającego. Jeśli usługa token zabezpieczający ujawnia federacyjny punkt końcowy, klient musi najpierw uzyskać token z wystawcy dla tego punktu końcowego. Każdy pozyskiwanie tokenu trwa, a ten czas jest uzależniony od całkowitego limitu czasu wysyłania rzeczywistej wiadomości do końcowego punktu końcowego.  
  
 Na przykład limit czasu w kanale po stronie klienta jest ustawiony na 30 sekund. Dwa wystawcy tokenów należy wywołać, aby pobrać tokeny przed wysłaniem komunikatu do końcowego punktu końcowego, a każdy z nich zajmie 15 sekund, aby wystawić token. W takim przypadku próba zakończy się niepowodzeniem i <xref:System.TimeoutException> zostanie zgłoszony. W tym celu należy ustawić <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> wartość w kanale klienta na wartość wystarczającą do uwzględnienia czasu pobrania wszystkich wystawionych tokenów. W przypadku <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> , gdy wartość nie jest określona dla właściwości, Właściwośćlubwłaściwość(lubobie)musibyćustawionanawartośćwystarczającoduża,abyuwzględnićczaspotrzebnydopobraniawszystkichwystawionychtokenów.<xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A>  
  
## <a name="token-lifetime-and-renewal"></a>Okres istnienia tokenu i odnowienie  
 Klienci WCF nie sprawdzają wystawionego tokenu podczas wykonywania początkowego żądania do usługi.  Zamiast tego WCF ufa usłudze tokenu zabezpieczającego, aby wystawić token z odpowiednimi godzinami obowiązywania i wygaśnięcia. Jeśli token jest buforowany przez klienta i ponownie używany, okres istnienia tokenu jest sprawdzany w kolejnych żądaniach, a klient automatycznie odnawia token w razie potrzeby. Aby uzyskać więcej informacji na temat buforowania tokenów, zobacz [How to: Utwórz klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)federacyjnego.  
  
 Określenie krótkich okresów istnienia, w kolejności od 30 sekund lub mniej dla wystawionych tokenów lub tokenów kontekstu zabezpieczeń, może spowodować przekroczenie limitu czasu negocjacji lub innych wyjątków zgłaszanych przez klientów programu WCF podczas żądania wystawionych tokenów lub podczas negocjowania lub odnawiania zabezpieczeń tokeny kontekstu.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Wystawione tokeny i przełączenie  
 Czy wystawiony token jest serializowany w wiadomości wysyłanej z klienta do federacyjnego punktu końcowego lub nie jest kontrolowany przez ustawienie <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> właściwości <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> klasy. Tę właściwość można ustawić na jedną z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> wartości wyliczenia, ale nie jest ona przydatna w większości scenariuszy federacyjnych. Wartości `SecurityTokenInclusionMode.Never` i`SecurityTokenInclusionMode.AlwaysToInitiator` powodują, że klient wysyła odwołanie do tokenu wystawionego przez usługę tokenu zabezpieczeń dla jednostki uzależnionej. Jeśli jednostka uzależniona nie posiada kopii wystawionego tokenu, uwierzytelnienie nie powiedzie się, ponieważ nie można rozpoznać odwołania do tokenu. WCF traktuje `SecurityTokenInclusionMode.Once` się `SecurityTokenInclusionMode.AlwaysToRecipient`jako równoważne.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Instrukcje: Tworzenie klienta federacyjnego](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Instrukcje: Konfigurowanie poświadczeń na usługa federacyjna](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Instrukcje: Utwórz WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
