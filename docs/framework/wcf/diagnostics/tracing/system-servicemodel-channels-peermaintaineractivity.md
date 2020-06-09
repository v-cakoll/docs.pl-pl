---
title: System.ServiceModel.Channels.PeerMaintainerActivity
ms.date: 03/30/2017
ms.assetid: ef28d086-d7fb-4e81-82e9-45a54647783b
ms.openlocfilehash: ce97eaa2ad5c9dbd5f4d6f81186960c489eb4b85
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596080"
---
# <a name="systemservicemodelchannelspeermaintaineractivity"></a>System.ServiceModel.Channels.PeerMaintainerActivity
Moduł PeerMaintainer wykonuje określoną operację (szczegóły zawarte w treści komunikatu śledzenia).  
  
## <a name="description"></a>Opis  
 Ten ślad występuje podczas różnych operacji PeerMaintainer.  
  
 PeerMaintainer jest wewnętrznym składnikiem elementu równorzędnego. Co minutę lub każde odebrane komunikaty 32 wysyła komunikat LinkUtility do jego sąsiadów z statystykami dotyczącymi liczby wymian komunikatów i liczby ich użytecznych (niezduplikowanych, nienaruszonych). Ułatwia to określenie narzędzia do łączenia określonego sąsiada. W ciągu co pięć minut element utrzymujący sprawdza kondycję połączeń sąsiadów. Jeśli liczba połączeń sąsiadów przekroczy wartość idealnej, w obszarze obsłudze są oczyszczane najmniejsze przydatne połączenia. Jeśli nie ma wystarczającej liczby połączeń, element utrzymujący uzyskuje nowe połączenia.  
  
## <a name="see-also"></a>Zobacz też

- [Śledzenie](index.md)
- [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](using-tracing-to-troubleshoot-your-application.md)
- [Administracja i Diagnostyka](../index.md)
