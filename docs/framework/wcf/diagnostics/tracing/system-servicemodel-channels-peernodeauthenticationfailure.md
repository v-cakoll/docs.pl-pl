---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 315122914ebcb3e8e4d72c8d976026a126306168
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219008"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a>System.ServiceModel.Channels.PeerNodeAuthenticationFailure
Uzgadnianie zabezpieczeń z potencjalnymi sąsiadem nie powiodło się.  
  
## <a name="description"></a>Opis  
 Ślad występuje podczas próby ustanowienia połączenia sąsiada bezpieczne. Można to zrobić ze względu na niewystarczające lub niepoprawne poświadczenia.  
  
 PeerChannel rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają modelu silna tożsamość na podstawie typu uwierzytelniania i autoryzacji, które można zaimplementować. PeerChannel zapewnia również obsługę prostej aplikacji przy użyciu hasła. Hasła mogą być wykorzystywane tylko w celu wprowadzania do sesji; one nie można przeprowadzić uwierzytelniania wiadomości. Jest to spowodowane to token symetryczny udziale, do grupy obiektów równorzędnych, jest trudne i nieodpowiednich treści na potrzeby uwierzytelniania źródła.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Upewnij się, że wszystkie sąsiadów poświadczenia odpowiednie zabezpieczenia.  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczenia kanału równorzędnego](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)
