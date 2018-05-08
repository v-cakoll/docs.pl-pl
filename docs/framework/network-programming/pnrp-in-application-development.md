---
title: Usługa PNRP w aplikacjach
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b085604d7d20eb9222507b4820be219ffeae4726
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pnrp-in-application-development"></a>Usługa PNRP w aplikacjach
W systemie Windows Vista sieci aplikacje mają dostęp do nazwy publikacji i funkcji rozpoznawania za pomocą uproszczonego PNRP interfejsu programowania aplikacji (API).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementacja protokołu rozpoznawania nazw równorzędnych  
 Z uproszczony interfejs API PNRP chmury nie są jawnie określone zarejestrować z nazwą i adresami; składnik PNRP automatycznie określa odpowiednich chmur sprzężenia i adresów do publikowania w ramach chmury.  
  
 Bardzo uproszczonego rozpoznawania nazw PNRP w systemie Windows Vista nazw PNRP są teraz zintegrowane getaddrinfo() funkcji Windows Sockets. Aby rozwiązać nazwę na adres IPv6 przy użyciu usługi PNRP, umożliwia aplikacjom funkcja getaddrinfo() rozwiązać name.prnp.net pełni kwalifikowanej domeny nazwę (FQDN), w których nazwa jest rozwiązywany nazwa elementu równorzędnego. Domena pnrp.net jest domeną zastrzeżonego w systemie Windows Vista do rozpoznawania nazw PNRP.  
  
 Przekazywanie między aplikacjami PeerToPeer komunikat nadal jest obsługiwany przez podstawowej architektury, takie jak PeerChannel i WCF [duże ilości danych i przesyłania strumieniowego](http://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer>
