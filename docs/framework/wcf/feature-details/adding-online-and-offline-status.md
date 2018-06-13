---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: fb19614c1975c5634a81ca2f40edb145b724cd1d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488107"
---
# <a name="adding-online-and-offline-status"></a>Dodawanie stanu online i offline
W wielu przypadkach jest ważna w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stanie połączenia kanał elementu równorzędnego. Te informacje można uzyskać przez wywołanie metody `GetProperty` metody wykonania <xref:System.ServiceModel.IOnlineStatus> interfejsu. Obiekt o implementację tego interfejsu można monitorować stan połączenia lub Zarejestruj się w celu obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i reagowania natychmiast wystąpienia zmian do stanu online.  
  
 W infrastrukturze kanału równorzędnego klienta uważa się być w trybie online, jeśli jest dołączona do przynajmniej jednego równorzędnego i w trybie offline w przeciwnym razie wartość. Może to być szczególnie przydatne w zarówno debugowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji dla użytkownika końcowego.  
  
> [!NOTE]
>  Program obsługi zdarzeń w trybie online należy najpierw upewnić się czy węzeł jest otwarte przed wysłaniem komunikaty.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
