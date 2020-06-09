---
title: Zabezpieczanie aplikacji kanałów równorzędnych
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a77449710e9093bc8ea2d5446e6359c26a3d1c1e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589880"
---
# <a name="securing-peer-channel-applications"></a>Zabezpieczanie aplikacji kanałów równorzędnych
Podobnie jak w przypadku innych powiązań w ramach programu WinFX, `NetPeerTcpBinding` zabezpieczenia są domyślnie włączone i oferują zarówno zabezpieczenia oparte na transportach, jak i w obu tych przypadkach. W tym temacie omówiono te dwa typy zabezpieczeń. Typ zabezpieczeń jest określany przez tag trybu zabezpieczeń w specyfikacji powiązania ( <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A> `Mode` ).  
  
## <a name="transport-based-security"></a>Zabezpieczenia oparte na transportach  
 Kanał równorzędny obsługuje dwa typy poświadczeń uwierzytelniania do zabezpieczania transportu, z których oba wymagają ustawienia `ClientCredentialSettings.Peer` Właściwości skojarzonej z `ChannelFactory` :  
  
- Hasło. Klienci używają informacji o haśle tajnym do uwierzytelniania połączeń. Gdy jest używany ten typ poświadczeń, `ClientCredentialSettings.Peer.MeshPassword` musi ono mieć prawidłowe hasło i opcjonalnie `X509Certificate2` wystąpienie.  
  
- Certyfikatu. Używane jest uwierzytelnianie konkretnej aplikacji. Gdy jest używany ten typ poświadczeń, należy użyć konkretnej implementacji programu <xref:System.IdentityModel.Selectors.X509CertificateValidator> w programie `ClientCredentialSettings.Peer.PeerAuthentication` .  
  
## <a name="message-based-security"></a>Zabezpieczenia oparte na komunikatach  
 Przy użyciu zabezpieczeń komunikatów aplikacja może podpisywać wiadomości wychodzące, tak aby wszystkie strony przyjmujące mogły sprawdzić, czy wiadomość jest wysyłana przez zaufaną stronę i czy wiadomość nie została naruszona. Obecnie kanał równorzędny obsługuje tylko podpisywanie komunikatów z poświadczeniami X. 509.  
  
## <a name="best-practices"></a>Najlepsze rozwiązania  
  
- W tej sekcji omówiono najlepsze rozwiązania dotyczące zabezpieczania aplikacji kanału równorzędnego.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Włącz zabezpieczenia za pomocą aplikacji kanału równorzędnego  
 Ze względu na rozproszony charakter protokołów kanałów równorzędnych trudno jest wymusić członkostwo w sieci, poufność i prywatność w niezabezpieczonej sieci. Należy również pamiętać o zabezpieczeniu komunikacji między klientami a usługą rozpoznawania nazw. W obszarze Protokół rozpoznawania nazw równorzędnych (PNRP) używaj bezpiecznych nazw, aby uniknąć fałszowania i innych typowych ataków. Zabezpiecz niestandardową usługę programu rozpoznawania nazw, włączając zabezpieczenia na klientach połączenia używane do kontaktowania się z usługą rozpoznawania nazw, w tym zabezpieczeniami komunikatów i opartych na transportach.  
  
### <a name="use-the-strongest-possible-security-model"></a>Korzystanie z najsilniejszego możliwego modelu zabezpieczeń  
 Na przykład, jeśli każdy element członkowski siatki musi być zidentyfikowany indywidualnie, użyj modelu uwierzytelniania opartego na certyfikatach. Jeśli nie jest to możliwe, należy użyć uwierzytelniania opartego na hasłach zgodnie z bieżącymi zaleceniami, aby zapewnić ich bezpieczeństwo. Dotyczy to również udostępniania haseł tylko zaufanym podmiotom, przesyłania haseł przy użyciu bezpiecznego nośnika, często zmieniających się haseł i zapewniania silnych haseł (co najmniej osiem znaków).  
  
### <a name="never-accept-self-signed-certificates"></a>Nigdy nie Akceptuj certyfikatów z podpisem własnym  
 Nigdy nie Akceptuj poświadczenie certyfikatu na podstawie nazw podmiotów. Należy pamiętać, że każdy może utworzyć certyfikat, a każdy może wybrać nazwę, która jest sprawdzana. Aby uniknąć możliwości fałszowania, należy sprawdzić poprawność certyfikatów na podstawie poświadczeń urzędu wystawiającego certyfikaty (zaufanego wystawcy lub głównego urzędu certyfikacji).  
  
### <a name="use-message-authentication"></a>Użyj uwierzytelniania komunikatów  
 Użyj uwierzytelniania wiadomości, aby sprawdzić, czy wiadomość pochodzi z zaufanego źródła i czy nikt nie został naruszony przez komunikat podczas przesyłania. Bez uwierzytelniania wiadomości, złośliwy klient może łatwo sfałszować lub naruszać komunikaty w sieci.  
  
## <a name="peer-channel-code-examples"></a>Przykłady kodu kanału równorzędnego  
 [Scenariusze obejmujące kanał elementu równorzędnego](peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia kanału równorzędnego](peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](building-a-peer-channel-application.md)
