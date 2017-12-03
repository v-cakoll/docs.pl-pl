---
title: "Zabezpieczanie aplikacji kanałów równorzędnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 377c2425ff1647c43687aa0a5d9584930cb6b1c2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="securing-peer-channel-applications"></a>Zabezpieczanie aplikacji kanałów równorzędnych
Inne powiązania w obszarze, takich jak [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` zabezpieczeń włączone domyślnie i oferuje zarówno zabezpieczenia na poziomie transportu i komunikatu (lub obie). W tym temacie omówiono tych dwóch typów zabezpieczeń. Typ zabezpieczeń jest określany przez tag tryb zabezpieczeń w specyfikacji powiązania (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).  
  
## <a name="transport-based-security"></a>Zabezpieczenia na poziomie transportu  
 Kanał elementu równorzędnego obsługuje dwa rodzaje poświadczeń uwierzytelniania dla zabezpieczanie transportu, które wymagają określający `ClientCredentialSettings.Peer` właściwości skojarzonych `ChannelFactory`:  
  
-   Hasło. Klienci używają znajomość tajnego hasła do uwierzytelniania połączenia. Jeśli ten typ poświadczeń jest używany, `ClientCredentialSettings.Peer.MeshPassword` musi zawierać prawidłowe hasło i opcjonalnie `X509Certificate2` wystąpienia.  
  
-   Certyfikat. Jest używane uwierzytelnianie określonej aplikacji. Jeśli ten typ poświadczeń jest używany, należy użyć konkretną implementację <xref:System.IdentityModel.Selectors.X509CertificateValidator> w `ClientCredentialSettings.Peer.PeerAuthentication`.  
  
## <a name="message-based-security"></a>Zabezpieczenia na poziomie komunikatu  
 Korzystanie z zabezpieczeń komunikatów aplikacji można podpisywania wychodzących wiadomości, tak, aby wszystkie strony odbierania sprawdzić, czy komunikat jest wysyłany przez zaufane firmy i wiadomość nie została niepowołane osoby. Obecnie kanału równorzędnego obsługuje tylko podpisywania komunikatów poświadczeń X.509.  
  
## <a name="best-practices"></a>Najlepsze praktyki  
  
-   W tej sekcji omówiono najlepsze rozwiązania dotyczące zabezpieczania aplikacji kanałów równorzędnych.  
  
### <a name="enable-security-with-peer-channel-applications"></a>Włącz zabezpieczenie z aplikacji kanałów równorzędnych  
 Z powodu Rozproszony charakter protokoły kanału równorzędnego jest trudne do wymuszenia członkostwa siatki, poufność i ochrona prywatności w niezabezpieczonej sieci. Jest również pamiętać do zabezpieczania komunikacji między klientami i usługi rozpoznawania nazw. W obszarze rozpoznawania protokołu PNRP (Peer Name), za pomocą bezpiecznego nazwy w celu zapobiegania atakom metodą preparowania i inne typowe ataki. Zabezpieczanie usługi niestandardowego programu rozpoznawania nazw przez włączenie zabezpieczeń przy użyciu klientów połączenia do kontaktowania się z usługi rozpoznawania nazw, w tym zabezpieczeń zarówno na podstawie komunikatu i transportu.  
  
### <a name="use-the-strongest-possible-security-model"></a>Użyj modelu zabezpieczeń możliwe najwyższego poziomu  
 Na przykład jeśli każdy element członkowski siatki musi się indywidualnie identyfikację, użyj model uwierzytelniania opartego na certyfikatach. Jeśli nie jest to możliwe, uwierzytelnianie oparte na hasłach następujących zalecanych rozwiązań w celu zachowania ich zabezpieczeń. Dotyczy to również udostępnianie haseł, tylko z zaufanych stronami, przesyłania hasła przy użyciu bezpiecznego średniej, zmiana haseł często i sprawdzeniu, czy hasła są silne (co najmniej osiem znaków długości, zawierać co najmniej jedną literę w obu przypadkach cyfrę, i znak specjalny).  
  
### <a name="never-accept-self-signed-certificates"></a>Nie pobieraj certyfikaty z podpisem własnym  
 Nie pobieraj poświadczenie certyfikatu na podstawie nazw podmiotu. Należy pamiętać, że każdy użytkownik może utworzyć certyfikat, a każdy użytkownik może wybrać nazwę, która jest sprawdzana poprawność. Aby uniknąć możliwość fałszowania, sprawdzić poprawność certyfikatów opartych na wystawienie poświadczenia urzędu (zaufanych wystawców lub głównego urzędu certyfikacji).  
  
### <a name="use-message-authentication"></a>Uwierzytelnianie wiadomości  
 Sprawdź, czy komunikat pochodzi z zaufanego źródła i czy nie został zmieniony przez niepowołane komunikat podczas przesyłania za pomocą uwierzytelniania wiadomości. Bez uwierzytelniania wiadomości jest łatwe złośliwego klienta fałszowania lub naruszyć wiadomości w sieci.  
  
## <a name="peer-channel-code-examples"></a>Przykłady kodu dla kanału równorzędnego  
 [Scenariusze obejmujące kanał elementu równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia kanału równorzędnego](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
