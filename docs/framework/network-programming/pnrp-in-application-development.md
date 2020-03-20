---
title: PNRP w projektowaniu aplikacji
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: f9a408fbd7fbbb77c0fd5208926f4b06fcf23b38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428206"
---
# <a name="pnrp-in-application-development"></a>PNRP w projektowaniu aplikacji
W systemie Windows Vista aplikacje sieciowe mogą uzyskiwać dostęp do funkcji publikowania nazw i rozpoznawania nazw za pośrednictwem uproszczonego interfejsu programowania aplikacji PNRP (API).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementowanie protokołu rozpoznawania nazw elementów równorzędnych  
 Za pomocą uproszczonego interfejsu API PNRP chmury nie są jawnie określone w celu zarejestrowania nazwy i adresów; Składnik PNRP automatycznie określa odpowiednie chmury do przyłączenia i adresy do opublikowania w chmurach.  
  
 W przypadku wysoce uproszczonej rozpoznawania nazw PNRP w systemie Windows Vista nazwy PNRP są teraz zintegrowane z funkcją getaddrinfo() Windows Sockets. Aby użyć protokołu PNRP do rozpoznania nazwy adresu IPv6, aplikacje mogą użyć funkcji getaddrinfo() do rozpoznawania name.prnp.net w pełni kwalifikowanej nazwy domeny (FQDN), w której nazwa jest rozpoznawana. Domena pnrp.net jest domeną zastrzeżoną w systemie Windows Vista dla rozpoznawania nazw PNRP.  
  
 Przekazywanie wiadomości między aplikacjami PeerToPeer jest nadal obsługiwane przez podstawowe architektury, takie jak PeerChannel i WCF [Large Data i Streaming](../wcf/feature-details/large-data-and-streaming.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer>
