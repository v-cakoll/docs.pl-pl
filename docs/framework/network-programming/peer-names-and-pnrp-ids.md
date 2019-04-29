---
title: Nazwy elementów równorzędnych i identyfikatory PNRP
ms.date: 03/30/2017
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
ms.openlocfilehash: e7e92519bede478a5e26a88a56236f987c93c441
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642132"
---
# <a name="peer-names-and-pnrp-ids"></a>Nazwy elementów równorzędnych i identyfikatory PNRP
Nazwa elementu równorzędnego reprezentuje punkt końcowy do komunikacji, który może być komputera, użytkownika, grupy, usługi lub jakikolwiek skojarzone z węzłem równorzędnym, która może zostać rozpoznana jako adres IPv6. Rozpoznawanie protokołu PNRP (Peer Name) zajmuje statystycznie unikatowy nazwa elementu równorzędnego dla tworzenia identyfikatora PNRP, który jest używany do identyfikowania elementów członkowskich w chmurze.  
  
## <a name="peer-names"></a>Nazwy elementów równorzędnych  
 Nazwy elementów równorzędnych może zostać zarejestrowana jako niezabezpieczone lub zabezpieczone. Niezabezpieczony nazwy są tylko ciągi tekstowe, które podlegają fałszowania, ponieważ każda osoba można zarejestrować zduplikowanej nazwy niezabezpieczona. Niezabezpieczony nazwy najlepiej sprawdzają się w chronionych sieciach prywatnych lub w inny sposób. Zabezpieczone nazwy są chronione przy użyciu certyfikatu i podpisu cyfrowego. Oryginalny wydawca będą mogli udowodnić własność zabezpieczona nazwa.  
  
 Kombinacja chmury i zakres udostępnia stosowne bezpieczne środowisko dla elementów równorzędnych, które uczestniczą w działaniu PNRP. Przy użyciu nazwy elementu równorzędnego zabezpieczonej zapewnia jednak ogólnego stanu zabezpieczeń aplikacji sieciowych. Zabezpieczenia aplikacji są zależne od implementacji.  
  
 Nazwy elementów równorzędnych zabezpieczonej rejestrować tylko przez właściciela i są chronione za pomocą kryptografii klucza publicznego. Nazwy elementu równorzędnego bezpiecznego, jest traktowane jako należące do jednostki elementów równorzędnych o odpowiedniego klucza prywatnego. Własność można udowodnić za pośrednictwem adresu certyfikowanych elementu równorzędnego (CPA), który jest podpisany przy użyciu klucza prywatnego. Złośliwy użytkownik nie forge własności nazwy elementu równorzędnego bez odpowiedniego klucza prywatnego.  
  
## <a name="pnrp-ids"></a>Identyfikatory PNRP  
 ![PNRP ID](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Identyfikatory PNRP składają się z następujących czynności:  
  
- Wyższego rzędu 128 bitów — znane jako identyfikator (P2P) peer-to-peer, to skrót nazwy elementu równorzędnego przypisana do punktu końcowego. Nazwa elementu równorzędnego ma następujący format: *Authority.Classifier*. Zabezpieczone nazw *urząd* jest skrótu Secure Hash Algorithm 1 (SHA1) klucza publicznego o nazwie elementu równorzędnego w znaków szesnastkowych. Niezabezpieczony nazw *urząd* jest pojedynczy znak "0". *Klasyfikator* jest ciągiem, który identyfikuje aplikację. Nie klasyfikatora nazwy elementów równorzędnych może być większa niż 149 znaków, łącznie z `null` terminator.  
  
- 128 bitów niskiego rzędu są używane do znalezienia usługi, która jest wygenerowany numer, który identyfikuje różnymi wystąpieniami tego samego Identyfikatora P2P w tej samej chmurze.  
  
 Ta kombinacja Identyfikatora P2P i lokalizacji usługi umożliwia wielu identyfikatory PNRP do zarejestrowania się z jednego komputera.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer.PeerName>
- <xref:System.Net.PeerToPeer>
