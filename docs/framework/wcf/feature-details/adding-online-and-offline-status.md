---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 15a963d4de0dcf1d7f0162b0a3266e17d4073ecd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147696"
---
# <a name="adding-online-and-offline-status"></a>Dodawanie stanu online i offline
W wielu przypadkach jest ważne w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stan połączenia kanał elementu równorzędnego. Te informacje można uzyskać przez wywołanie metody `GetProperty` metody na implementację <xref:System.ServiceModel.IOnlineStatus> interfejsu. Obiekt o implementację tego interfejsu można monitorować stan połączenia lub zarejestruj procedury obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i od razu wraz ze zmianami do stanu online.  
  
 W infrastrukturze kanał elementu równorzędnego klienta uznaje się być w trybie online, jeśli jest połączony co najmniej jeden innych elementów równorzędnych i w trybie offline w przeciwnym razie. Może to być szczególnie przydatne w zarówno profilowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji do użytkownika końcowego.  
  
> [!NOTE]
>  Program obsługi zdarzeń w trybie online należy najpierw upewnić się, że węzeł został otwarty przed wysłaniem komunikatów.  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
