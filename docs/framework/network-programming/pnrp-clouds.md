---
title: Chmury PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: dd27e61fe1f648dcaf4ee4dd5f5119d33913c63a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047372"
---
# <a name="pnrp-clouds"></a>Chmury PNRP
"Chmura" w protokole PNRP reprezentuje zestaw węzłów, które mogą komunikować się ze sobą za pomocą sieci. Termin "Chmura" jest równoznaczny z "siatką równorzędną" i "wykresem równorzędnym".  
  
 Komunikacja między węzłami nigdy nie powinna przekraczać jednej chmury do innej. <xref:System.Net.PeerToPeer.Cloud> Wystąpienie jest jednoznacznie identyfikowane przez jego nazwę, w której rozróżniana jest wielkość liter. Pojedynczy element równorzędny lub węzeł może być połączony z więcej niż jedną chmurą.  
  
 Chmury są ściśle powiązane z interfejsami sieciowymi.  W przypadku maszyn wieloadresowych z dwiema kartami sieciowymi podłączonymi do różnych podsieci zostaną zwrócone trzy chmury: jedna dla każdego z adresów lokalnych w interfejsie i w jednej chmurze zakresu globalnego.  
  
 Protokół PNRP używa trzech zakresów w chmurze, w których zakres jest grupą komputerów, które mogą się znajdować nawzajem:  
  
- Chmura globalna odnosi się do globalnego zakresu adresów IPv6 i adresów globalnych oraz reprezentuje wszystkie komputery w całym internetowym protokole IPv6. Istnieje tylko jedna chmura globalna.  
  
- Chmura lokalna łącza odnosi się do zakresu adresów IPv6 i adresów lokalnych łącza. Chmura lokalna linku dotyczy określonego linku, który jest zwykle taki sam, jak w przypadku lokalnie dołączonej podsieci. Może istnieć wiele chmur z linkiem lokalnym.  
  
 Trzecia Chmura, w której dana lokacja jest zgodna z zakresem adresów IPv6 lokacji i adresami lokalnymi lokacji. Ta chmura jest przestarzała, chociaż nadal jest obsługiwana w protokole PNRP.  
  
## <a name="clouds"></a>Chmury  
 Chmury PNRP są reprezentowane przez wystąpienia <xref:System.Net.PeerToPeer.Cloud> klasy. Grupy chmur używane przez element równorzędny są reprezentowane przez wystąpienia klasy wyliczalnej <xref:System.Net.PeerToPeer.CloudCollection> . Kolekcje chmur protokołu PNRP znane do bieżącego elementu równorzędnego można uzyskać przez wywołanie metody statycznej <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> .  
  
 Poszczególne chmury mają unikatowe nazwy reprezentowane przez 256 znak Unicode. Te nazwy, wraz z powyższym zakresem, służą do konstruowania unikatowych wystąpień klasy chmury. Te wystąpienia można serializować i odtworzyć na potrzeby trwałego użycia.  
  
 Po utworzeniu lub uzyskaniu wystąpienia w chmurze nazwy elementów równorzędnych mogą być zarejestrowane w celu utworzenia siatki znanych elementów równorzędnych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer.Cloud>
- [Protokół PNRP](peer-name-resolution-protocol.md)
