---
title: PNRP Clouds
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: d91bf1b68b8446e2700b601d818c493b8edc1b82
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54742201"
---
# <a name="pnrp-clouds"></a>PNRP Clouds
PNRP "chmura" reprezentuje zestaw węzłów, które mogą komunikować się ze sobą za pośrednictwem sieci. Termin "chmura" jest synonimem "siatki elementów równorzędnych" i "peer-to-peer grafu".  
  
 Komunikacji między węzłami powinno nigdy nie przechodzą z chmury do innego. A <xref:System.Net.PeerToPeer.Cloud> wystąpienia jest unikatowo identyfikowane przez jego nazwę, która jest uwzględniana wielkość liter. Pojedynczego elementu równorzędnego lub węzeł może być podłączony do więcej niż jednej chmury.  
  
 Chmury są ściśle powiązane interfejsy sieciowe.  Na maszynie wieloadresowych z dwóch kart sieciowych dołączonych do różnych podsieci, zostaną zwrócone trzy chmury: jeden dla każdego z adresów lokalnych łącza na interfejsu i w chmurze pojedynczy zakres globalny.  
  
 Protokół PNRP używa trzech chmury "zakresów", w których zakresie to grupa komputerów, które są w stanie odnajdować:  
  
-   Chmury globalnej odnosi się do globalnego zakresu adresów IPv6 i adresy globalne i przedstawia wszystkie komputery w cały Internet IPv6. Istnieje tylko jednej chmury globalnej.  
  
-   Chmura link-local odpowiada zakres adresów IPv6 połączenia lokalnego i adresów połączenia lokalnego. Chmura połączenia lokalnego jest jedno łącze jest zwykle taka sama, jak podsieć, podłączonych lokalnie. Może istnieć wiele chmur połączenia lokalnego.  
  
 Trzeci chmury, chmury specyficzne dla lokacji, odnosi się do witryny IPv6 zakres adresów i adresy lokacji lokalnej. Ta chmura została wycofana, mimo że nadal jest obsługiwana w PNRP.  
  
## <a name="clouds"></a>Chmury  
 Chmury PNRP są reprezentowane przez wystąpienia <xref:System.Net.PeerToPeer.Cloud> klasy. Grupy chmur użyli elementu równorzędnego są reprezentowane przez wystąpienia wyliczalny <xref:System.Net.PeerToPeer.CloudCollection> klasy. Kolekcje chmury PNRP, znany na bieżącym węźle równorzędnym można uzyskać przez wywołanie statycznego <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metody.  
  
 Poszczególne chmury mają unikatowych nazw, reprezentowany jako ciąg Unicode 256 znaków. Nazwy te, wraz z wyżej zakresu, są używane do konstruowania unikatowe wystąpień klasy chmury. Te wystąpienia mogą serializacji i odtworzone za użycie trwałego.  
  
 Po utworzeniu wystąpienia w chmurze lub uzyskane, nazwy elementów równorzędnych może być zarejestrowany go, aby utworzyć siatki elementów równorzędnych znane.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Net.PeerToPeer.Cloud>
- [Protokół PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
