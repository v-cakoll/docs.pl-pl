---
title: Nazwy elementów równorzędnych i identyfikatory PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: 15b74317507f69d2339a2e5e49b54ae72cda1a7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047501"
---
# <a name="peer-names-and-pnrp-ids"></a>Nazwy elementów równorzędnych i identyfikatory PNRP
Nazwa elementu równorzędnego reprezentuje punkt końcowy komunikacji, który może być komputerem, użytkownikiem, grupą, usługą lub wszystkim, co jest skojarzone z elementem równorzędnym, które można rozpoznać na adres IPv6. Protokół rozpoznawania nazw elementów równorzędnych (PNRP) przyjmuje statystycznie unikatową nazwę elementu równorzędnego do tworzenia identyfikatora PNRP, który jest używany do identyfikowania elementów członkowskich chmury.  
  
## <a name="peer-names"></a>Nazwy elementów równorzędnych  
 Nazwy elementów równorzędnych mogą być rejestrowane jako niezabezpieczone lub zabezpieczone. Niezabezpieczone nazwy to tylko ciągi tekstowe, które podlegają fałszowaniu, ponieważ każdy może zarejestrować zduplikowaną niezabezpieczoną nazwę. Nazwy niezabezpieczone są najlepiej używane w sieciach prywatnych lub w inny sposób chronionych. Zabezpieczone nazwy są chronione certyfikatem i podpisem cyfrowym. Tylko pierwotny wydawca będzie mógł udowodnić własność zabezpieczonej nazwy.  
  
 Połączenie chmury i zakresu zapewnia rozsądnie bezpieczne środowisko dla korzystać z usług ami równorzędnymi, które uczestniczą w działaniu PNRP. Jednak przy użyciu zabezpieczonej nazwy elementu równorzędnego nie zapewnia ogólnego bezpieczeństwa aplikacji sieciowej. Bezpieczeństwo aplikacji zależy od implementacji.  
  
 Zabezpieczone nazwy elementów równorzędnych są rejestrowane tylko przez ich właściciela i są chronione kryptografią klucza publicznego. Zabezpieczona nazwa elementu równorzędnego jest uważana za należącą do jednostki równorzędnej posiadającej odpowiedni klucz prywatny. Własność można udowodnić za pomocą certyfikowanego adresu równorzędnego (CPA), który jest podpisany przy użyciu klucza prywatnego. Złośliwy użytkownik nie może podwładć własności nazwy równorzędnej bez odpowiedniego klucza prywatnego.  
  
## <a name="pnrp-ids"></a>Identyfikatory PNRP  
 ![Identyfikator PNRP](./media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Identyfikatory PNRP składają się z następujących elementów:  
  
- 128 bitów wysokiego rzędu, znany jako peer-to-peer (P2P) ID, są skrótem nazwy elementu równorzędnego przypisanego do punktu końcowego. Nazwa elementu równorzędnego ma następujący format: *Authority.Classifier*. W przypadku zabezpieczonych nazw *urząd* jest skrótem bezpiecznego algorytmu mieszania 1 (SHA1) klucza publicznego nazwy elementu równorzędnego w znakach szesnastkowych. W przypadku nazw niezabezpieczonych *Urząd* jest pojedynczym znakiem "0". *Klasyfikator* jest ciągiem identyfikującym aplikację. Żaden klasyfikator nazw równorzędnych nie może być `null` większy niż 149 znaków, łącznie z terminatorem.  
  
- 128 bitów niskiego rzędu są używane dla lokalizacji usługi, która jest generowaną liczbą, która identyfikuje różne wystąpienia tego samego identyfikatora P2P w tej samej chmurze.  
  
 Ta kombinacja identyfikatora P2P i lokalizacji usługi umożliwia rejestrowanie wielu identyfikatorów PNRP z jednego komputera.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
