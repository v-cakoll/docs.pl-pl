---
title: Zabezpieczanie aplikacji kanałów równorzędnych
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: a747923f81f4773eb58a4b7500cf4fc1c006f889
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59146250"
---
# <a name="securing-peer-channel-applications"></a>Zabezpieczanie aplikacji kanałów równorzędnych
Jak innych powiązań w obszarze [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` ma domyślnie włączona, zabezpieczeń i oferuje zarówno zabezpieczenia na poziomie transportu i komunikat (lub obie). W tym temacie omówiono te dwa rodzaje zabezpieczeń. Typ zabezpieczeń jest określony przez tag tryb zabezpieczeń w specyfikacji powiązania (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Zabezpieczenia na poziomie transportu  
 Kanał elementu równorzędnego obsługuje dwa typy poświadczeń uwierzytelniania dla zabezpieczanie transportu, które wymagają ustawienie poziomie `ClientCredentialSettings.Peer` właściwości skojarzonego `ChannelFactory`:  
  
-   Hasło. Klienci używają znajomość tajnego hasła do uwierzytelniania połączenia. Jeśli ten typ poświadczeń jest używany, `ClientCredentialSettings.Peer.MeshPassword` musi zawierać prawidłowe hasło i opcjonalnie `X509Certificate2` wystąpienia.  
  
-   certyfikat. Jest używane uwierzytelnianie określonej aplikacji. Ten typ poświadczeń jest używany, należy użyć konkretną implementację <xref:System.IdentityModel.Selectors.X509CertificateValidator> w `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Zabezpieczenia na poziomie komunikatu  
 Korzystanie z zabezpieczeń komunikatów aplikacji mogą podpisywać komunikaty wychodzące tak, aby wszystkie strony odbieranie sprawdzić, czy komunikat jest wysyłany przez zaufany i wiadomość nie została naruszona. Obecnie kanał elementu równorzędnego obsługuje tylko podpisywanie komunikatów poświadczeń X.509.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
  
-   W tej sekcji omówiono najlepsze rozwiązania dotyczące zabezpieczania aplikacji kanałów równorzędnych.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Włącz zabezpieczenia za pomocą aplikacji kanałów równorzędnych  
 Ze względu na Rozproszony charakter protokoły kanału równorzędnego trudno wymusić członkostwa siatki, poufności i ochrony prywatności w niezabezpieczonych siatki. Jest również pamiętać do zabezpieczania komunikacji między klientami i usługi rozpoznawania nazw. W obszarze rozpoznawania protokołu PNRP (Peer Name), Użyj bezpiecznego nazwy w celu uniknięcia fałszowania i innymi typowymi atakami. Zabezpieczanie usługi niestandardowym programem rozpoznawania nazw, należy włączyć zabezpieczeń przy użyciu połączenia klientów do kontaktowania się z usługi rozpoznawania nazw, w tym zarówno zabezpieczenia oparte na komunikat i do transportu.  
  
### <a name="use-the-strongest-possible-security-model"></a>Użycie najsilniejszego modelu możliwych zabezpieczeniami  
 Na przykład jeśli każdy element członkowski siatkę musi indywidualnie można zidentyfikować, należy użyć model uwierzytelniania opartego na certyfikatach. Jeśli nie jest to możliwe, uwierzytelnianie oparte na hasłach po zalecanych rozwiązań Zachowaj ich bezpieczeństwo. W tym udostępnianie haseł, tylko z zaufanym osobom lub podmiotom, przesyłanie haseł przy użyciu bezpiecznego średniej, zmienianie haseł często i zapewnienia silnego hasła (co najmniej ośmiu znaków długie, zawierają co najmniej jedną literę w obu przypadkach, cyfry oraz znaki i znaków specjalnych).  
  
### <a name="never-accept-self-signed-certificates"></a>Nie pobieraj certyfikaty z podpisem własnym  
 Nie pobieraj poświadczenie certyfikatu na podstawie nazw podmiotu. Należy pamiętać, że każdy może utworzyć certyfikat, a każda osoba może wybrać nazwę, która jest sprawdzana poprawność. Aby uniknąć możliwość fałszowania, sprawdzanie poprawności certyfikatów opartych na wystawianie poświadczenia urzędu (zaufanych wystawców lub główny urząd certyfikacji).  
  
### <a name="use-message-authentication"></a>Użyj uwierzytelniania wiadomości  
 Aby sprawdzić, czy wiadomość pochodzi z zaufanego źródła i że nikt nie ingerował komunikat podczas przesyłania, należy użyć uwierzytelniania wiadomości. Bez uwierzytelniania wiadomości jest łatwo złośliwego klienta podszywały się pod ani zmieniać informacji dotyczących komunikatów w siatce.  
  
## <a name="peer-channel-code-examples"></a>Przykłady kodu dla kanału równorzędnego  
 [Scenariusze obejmujące kanał elementu równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
