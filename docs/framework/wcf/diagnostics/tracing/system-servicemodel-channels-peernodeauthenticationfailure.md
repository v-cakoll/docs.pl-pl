---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b09d7fc476d5eed7f7c534fdde46cb18eeac30d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Uzgadnianie zabezpieczeń z potencjalnych sąsiada zakończyła się niepowodzeniem.  
  
## <a name="description"></a>Opis  
 Ślad występuje podczas próby ustanowienia połączenia z elementem sąsiednim bezpieczne. Może to nastąpić z powodu niewystarczających lub nieprawidłowe poświadczenia.  
  
 PeerChannel rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają oparty na typie uwierzytelniania i autoryzacji, które można wdrożyć modelu silnej tożsamości. PeerChannel także zapewnia obsługę proste aplikacje przy użyciu hasła. Hasła mogą być wykorzystywane tylko w celu wprowadzania z sesją; Nie można ich używany do uwierzytelniania wiadomości. Jest to spowodowane tokenu symetrycznego, który udział grupy elementów równorzędnych jest trudne i nieodpowiednie do użycia na potrzeby uwierzytelniania źródła.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Sprawdź, czy wszystkie sąsiadów mają poświadczenia odpowiednich ustawień zabezpieczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia kanału równorzędnego](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i Diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
