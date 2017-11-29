---
title: "Usługa PNRP chmury"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a82e2bf1-62ab-4c2d-83f3-3217a6aead2e
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1b9769d4e3936e127407f68de81f9b5b5da4fbc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="pnrp-clouds"></a>Usługa PNRP chmury
PNRP "chmura" reprezentuje zestaw węzłów, które mogą komunikować się ze sobą za pośrednictwem sieci. Termin "chmura" jest tożsame z "siatki równorzędnej" i "peer-to-peer wykresu".  
  
 Komunikacja między węzłami nigdy nie powinien przechodzą z jednej chmury do innej. A <xref:System.Net.PeerToPeer.Cloud> wystąpienia jest unikatowo identyfikowana przez jego nazwę, która jest uwzględniana wielkość liter. Pojedynczego elementu równorzędnego lub węzeł może być połączone do więcej niż jednej chmury.  
  
 Chmury są bardzo ściśle powiązane z interfejsów sieciowych.  Na maszynie wieloadresowego z dwóch kart sieciowych, dołączone do różnych podsieci zostanie zwrócony trzy chmury: jeden dla poszczególnych adresów lokalnych łącza na interfejs i w chmurze pojedynczy zakres globalny.  
  
 Usługa PNRP używa trzech chmury "zakresy", w których zakres to grupa komputerów, które są w stanie odnajdować:  
  
-   Globalne chmury odpowiada zasięg globalny adres IPv6 i adresy globalne i reprezentuje wszystkie komputery w całej Internet IPv6. Istnieje tylko jeden chmury globalnej.  
  
-   Link-local chmury odpowiada zakres adresów IPv6 połączenia lokalnego i adresów połączenia lokalnego. Chmury połączenia lokalnego jest przeznaczony dla określonego łącza, które zwykle jest taka sama jak lokalnie dołączone podsieci. Może istnieć wiele chmur połączenia lokalnego.  
  
 Trzeci chmury, chmury specyficzne dla lokacji, odnosi się do witryny IPv6 zakres adresów i adresy lokacji lokalnej. Ta chmura jest przestarzałe, mimo że nadal jest obsługiwany w protokole PNRP.  
  
## <a name="clouds"></a>Chmury  
 Usługa PNRP chmury są reprezentowane przez wystąpienia <xref:System.Net.PeerToPeer.Cloud> klasy. Grupy chmur używane elementu równorzędnego są reprezentowane przez wystąpień wyliczenia <xref:System.Net.PeerToPeer.CloudCollection> klasy. Kolekcje chmur PNRP znane dla bieżącego elementu równorzędnego można uzyskać przez wywołanie metody statycznych <xref:System.Net.PeerToPeer.Cloud.GetAvailableClouds%2A> metody.  
  
 Poszczególne chmury mają unikatowe nazwy, reprezentowany jako ciąg Unicode 256 znaków. Te nazwy, wraz z wyżej zakresu, są używane do utworzenia unikatowych wystąpień klasy chmury. Te wystąpienia można serializować i odtworzyć trwałe użycia.  
  
 Po wystąpienia chmury jest utworzyć lub uzyskać, można zarejestrować nazwy elementów równorzędnych z go w celu utworzenia siatkę znanych elementów równorzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer.Cloud>  
 [Protokół PNRP](../../../docs/framework/network-programming/peer-name-resolution-protocol.md)
