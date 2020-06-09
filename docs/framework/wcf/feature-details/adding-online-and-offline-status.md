---
title: Dodawanie stanu online i offline
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: da170bbc22d04dcbf5f7cd4ac084a004bb4b026e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597686"
---
# <a name="adding-online-and-offline-status"></a>Dodawanie stanu online i offline
W wielu przypadkach ważne jest, aby aplikacja monitorowała szczegółowe informacje o stanie połączenia kanału równorzędnego. Te informacje można uzyskać, wywołując `GetProperty` metodę dla implementacji <xref:System.ServiceModel.IOnlineStatus> interfejsu. Obiekt z implementacją tego interfejsu może monitorować stan połączenia lub rejestr dla programów obsługi zdarzeń, takich jak i i `OnOnline` `OnOffline` reagować natychmiast po wystąpieniu zmian stanu online.  
  
 W infrastrukturze kanału równorzędnego klient jest traktowany jako w trybie online, jeśli jest połączony z co najmniej jednym innym węzłem równorzędnym i w przeciwnym razie w trybie offline. Może to być szczególnie przydatne w przypadku debugowania aplikacji tworzących lub wyświetlania szczegółowych informacji dla użytkownika końcowego.  
  
> [!NOTE]
> Procedura obsługi zdarzeń online powinna najpierw upewnić się, że węzeł jest otwarty przed wysłaniem jakichkolwiek komunikatów.  
  
## <a name="see-also"></a>Zobacz też

- [Tworzenie aplikacji kanału równorzędnego](building-a-peer-channel-application.md)
