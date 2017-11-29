---
title: "Nazwy elementów równorzędnych i identyfikatory PNRP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afa538e8-948f-4a98-aa9f-305134004115
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c5b4bcf0a7a7d23dd54fad36b341e3ed241975b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="peer-names-and-pnrp-ids"></a>Nazwy elementów równorzędnych i identyfikatory PNRP
Nazwa elementu równorzędnego reprezentuje punkt końcowy komunikacji, który może być komputera, użytkownika, grupy, usługi lub niczego skojarzony z węzłem równorzędnym, które zostały rozpoznane jako adres IPv6. Rozpoznawania protokołu PNRP (Peer Name) ma statystycznie unikatowa nazwa elementu równorzędnego w celu utworzenia identyfikatora PNRP, który służy do identyfikowania członków chmury.  
  
## <a name="peer-names"></a>Nazwy elementów równorzędnych  
 Nazwy elementów równorzędnych może być zarejestrowany jako niezabezpieczone lub zabezpieczone. Niezabezpieczona nazwy są po prostu ciągów tekstowych, które podlegają podszywanie się, ponieważ każdy użytkownik może zarejestrować zduplikowanej nazwy niezabezpieczona. Nazwy niezabezpieczona najlepiej są używane w sieci chronionej prywatnych lub w inny sposób. Nazwy zabezpieczonych są chronione przy użyciu certyfikat i podpis cyfrowy. Oryginalny wydawca będzie można zweryfikować własność zabezpieczona nazwa.  
  
 Kombinacja chmury i zakres stanowi rozsądny sposób bezpieczne środowisko dla elementów równorzędnych, które uczestniczą w działaniu usługi PNRP. Przy użyciu nazwy elementu równorzędnego zabezpieczonych zapewnia jednak ogólne bezpieczeństwo aplikacji sieciowych. Zabezpieczenia aplikacji są zależne od implementacji.  
  
 Nazwy elementów równorzędnych zabezpieczonych rejestrować tylko przez właściciela i są chronione z kluczem publicznym. Nazwa elementu równorzędnego zabezpieczonych jest traktowany jako należących do jednostki elementu równorzędnego o odpowiedni klucz prywatny. Własność można udowodnić, za pomocą adresu certyfikowanych elementu równorzędnego (CPA), który jest podpisany przy użyciu klucza prywatnego. Złośliwy użytkownik nie forge własność nazwy elementu równorzędnego bez odpowiedniego klucza prywatnego.  
  
## <a name="pnrp-ids"></a>Identyfikatory PNRP  
 ![Identyfikator PNRP](../../../docs/framework/network-programming/media/fdc9e8a0-4a1c-488d-a019-bc3a1973220c.gif "fdc9e8a0-4a1c-488d-a019-bc3a1973220c")  
  
 Identyfikatory PNRP składają się z następujących czynności:  
  
-   Znaczących 128 bitów — znane jako identyfikator (P2P) peer-to-peer, są skrót nazwy elementu równorzędnego przypisana do punktu końcowego. Nazwa elementu równorzędnego ma następujący format: *Authority.Classifier*. Dla nazwy zabezpieczonych *urzędu* jest skrótu Secure Hash Algorithm 1 (SHA1) klucz publiczny nazwa elementu równorzędnego w znaki szesnastkowe. Niezabezpieczona nazw *urzędu* jest pojedynczy znak "0". *Klasyfikator* jest ciągiem, który identyfikuje aplikację. Nie klasyfikatora nazwa elementu równorzędnego może być większa niż 149 znaków, łącznie z `null` terminator.  
  
-   128 bitów znaczącymi bitami są używane do lokalizacji usługi, która jest wygenerowany liczba, która identyfikuje różnych wystąpień tego samego identyfikatora P2P w tej samej chmury.  
  
 Ta kombinacja Identyfikatora P2P i lokalizację usługi umożliwia wielu identyfikatorów PNRP rejestrowana z jednego komputera.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer.PeerName>  
 <xref:System.Net.PeerToPeer>
