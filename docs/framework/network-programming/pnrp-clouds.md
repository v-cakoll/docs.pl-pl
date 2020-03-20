---
title: Chmury PNRP
ms.date: 03/30/2017
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
ms.openlocfilehash: dd27e61fe1f648dcaf4ee4dd5f5119d33913c63a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047372"
---
# <a name="pnrp-clouds"></a>Chmury PNRP
PnRP "chmura" reprezentuje zestaw węzłów, które mogą komunikować się ze sobą za pośrednictwem sieci. Termin "chmura" jest synonimem "siatki równorzędnej" i "wykres peer-to-peer".  
  
 Komunikacja między węzłami nigdy nie powinna przechodzić z jednej chmury do drugiej. Wystąpienie <xref:System.Net.PeerToPeer.Cloud> jest jednoznacznie identyfikowane przez jego nazwę, która jest rozróżniana wielkość liter. Jeden element równorzędny lub węzeł może być połączony z więcej niż jedną chmurą.  
  
 Chmury są bardzo ściśle powiązane z interfejsami sieciowymi.  Na komputerze wielorodzinnym z dwiema kartami sieciowymi dołączonymi do różnych podsieci zostaną zwrócone trzy chmury: po jednym dla każdego połączenia adresów lokalnych na interfejs i jednej globalnej chmury zakresu.  
  
 PNRP używa trzech "zakresów" w chmurze, w których zakres jest grupowanie komputerów, które są w stanie znaleźć siebie nawzajem:  
  
- Chmura globalna odpowiada globalnemu zakresowi adresów IPv6 i adresom globalnym i reprezentuje wszystkie komputery w całym Internecie IPv6. Istnieje tylko jedna globalna chmura.  
  
- Chmura lokalna łącza odpowiada zakresowi adresu IPv6 i adresom lokalnym łącza. Chmura lokalna łącza jest dla określonego łącza, które jest zazwyczaj takie same jak lokalnie dołączone podsieci. Może istnieć wiele chmur lokalnych łączy.  
  
 Trzecia chmura, chmura specyficzna dla lokacji, odpowiada zakresowi adresu IPv6 witryny i adresom lokalnym lokacji. Ta chmura została przestarzała, chociaż nadal jest obsługiwana w PNRP.  
  
## <a name="clouds"></a>Chmury  
 Chmury PNRP są reprezentowane przez <xref:System.Net.PeerToPeer.Cloud> wystąpienia klasy. Grupy chmur używane peer są reprezentowane przez wystąpienia klasy <xref:System.Net.PeerToPeer.CloudCollection> wyliczalne. Kolekcje chmur PNRP znane bieżącemu elementowi równorzędnej można uzyskać, wywołując metodę statyczną. <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A>  
  
 Poszczególne chmury mają unikatowe nazwy, reprezentowane jako 256-znakowy ciąg Unicode. Te nazwy, wraz z wyżej wymienionym zakresem, są używane do konstruowania unikatowych wystąpień cloud klasy. Te wystąpienia mogą być serializowane i rekonstruowane dla trwałego użycia.  
  
 Po utworzeniu lub uzyskaniu wystąpienia w chmurze można zarejestrować nazwy elementów równorzędnych, aby utworzyć siatkę znanych elementów równorzędnych.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer.Cloud>
- [Protokół PNRP](peer-name-resolution-protocol.md)
