---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577308"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Uzgadnianie zabezpieczeń z potencjalnym sąsiadem nie powiodło się.  
  
## <a name="description"></a>Opis  
 Ten ślad występuje podczas próby nawiązania bezpiecznego połączenia sąsiada. Przyczyną może być niewystarczające lub nieprawidłowe poświadczenia.  
  
 PeerChannel rozpoznaje pojedynczy typ tokenu dla silnej identyfikacji, certyfikaty X. 509, które zapewniają silny model tożsamości na podstawie typu uwierzytelniania i autoryzacji, które mogą być implementowane. PeerChannel zapewnia również obsługę prostych aplikacji przy użyciu haseł. Haseł można używać tylko w celu zezwalania na wpis w sesji; nie można ich używać do uwierzytelniania wiadomości. Jest to spowodowane tym, że symetryczny token, który jest używany przez grupę elementów równorzędnych, jest trudny i nieodpowiedni do uwierzytelniania źródłowego.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Upewnij się, że wszystkie sąsiedzi mają odpowiednie poświadczenia zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia kanału równorzędnego](../../feature-details/peer-channel-security.md)
- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
