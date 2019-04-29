---
title: PNRP w projektowaniu aplikacji
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 4cd0d739e58cd252213e8d5c16d29cc612338df6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61641999"
---
# <a name="pnrp-in-application-development"></a>PNRP w projektowaniu aplikacji
W systemie Windows Vista sieci aplikacje mają dostęp do nazwy publikacji i funkcji rozpoznawania za pomocą uproszczonego PNRP interfejsu programowania aplikacji (API).  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a>Implementacja protokołu rozpoznawania nazw równorzędnych  
 Uproszczony interfejs API PNRP chmury nie są jawnie określone zarejestrować nazwą i adresami; składnik PNRP automatycznie określa odpowiedniej chmury sprzężenia i adresy do opublikowania w ramach chmury.  
  
 Bardzo uproszczone rozpoznawania nazw PNRP w Windows Vista nazw PNRP są teraz zintegrowane getaddrinfo() funkcji Windows Sockets. Aby rozpoznać nazwy adresu IPv6 za pomocą PNRP, aplikacje mogą korzystać funkcja getaddrinfo() rozpoznać name.prnp.net w pełni kwalifikowanej domeny nazwę (FQDN), w których nazwa jest nazwą elementu równorzędnego rozwiązywany. Domena pnrp.net jest domeny zastrzeżonej w Windows Vista do rozpoznawania nazw PNRP.  
  
 Przekazywanie pomiędzy aplikacjami PeerToPeer komunikatów nadal jest obsługiwany przez podstawowych architektur, takich jak PeerChannel i WCF [duże ilości danych i przesyłanie strumieniowe](https://go.microsoft.com/fwlink/?LinkID=179652).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer>
