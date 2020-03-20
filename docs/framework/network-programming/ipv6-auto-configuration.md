---
title: Automatyczna konfiguracja IPv6
ms.date: 03/30/2017
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
ms.openlocfilehash: 95d9dce36c70b8f6c6b9f963c0842305a111d436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047806"
---
# <a name="ipv6-auto-configuration"></a>Automatyczna konfiguracja IPv6
Jednym z ważnych celów dla IPv6 jest obsługa węzła Plug and Play. Oznacza to, że powinno być możliwe podłączenie węzła do sieci IPv6 i automatyczne skonfigurowanie bez interwencji człowieka.  
  
## <a name="type-of-auto-configuration"></a>Typ automatycznej konfiguracji  
 Protokół IPv6 obsługuje następujące typy konfiguracji automatycznej:  
  
- **Stanowa automatyczna konfiguracja**. Ten typ konfiguracji wymaga pewnego poziomu interwencji człowieka, ponieważ wymaga protokołu konfiguracji hosta dynamicznego dla serwera IPv6 (DHCPv6) do instalacji i administrowania węzłami. Serwer DHCPv6 przechowuje listę węzłów, do których dostarcza informacje o konfiguracji. Przechowuje również informacje o stanie, dzięki czemu serwer wie, jak długo każdy adres jest w użyciu i kiedy może być dostępny do ponownego przypisania.  
  
- **Bezstanowa automatyczna konfiguracja**. Ten typ konfiguracji jest odpowiedni dla małych organizacji i osób prywatnych. W takim przypadku każdy host określa swoje adresy na podstawie zawartości odebranych anonsów routera. Korzystając ze standardu IEEE EUI-64 do zdefiniowania części adresu identyfikatora sieci, uzasadnione jest założenie wyjątkowości adresu hosta w linku.  
  
 Niezależnie od sposobu określania adresu węzeł musi sprawdzić, czy jego potencjalny adres jest unikatowy dla łącza lokalnego. Odbywa się to poprzez wysłanie wiadomości na żądanie sąsiada na potencjalny adres. Jeśli węzeł odbiera odpowiedzi, wie, że adres jest już w użyciu i musi określić inny adres.  
  
## <a name="ipv6-mobility"></a>Mobilność IPv6  
 Rozprzestrzenianie się urządzeń mobilnych wprowadziło nowe wymagania: urządzenie musi być w stanie dowolnie zmieniać lokalizacje w Internecie IPv6 i nadal utrzymywać istniejące połączenia. Aby zapewnić tę funkcję, węzeł mobilny jest przypisany adres domowy, pod którym zawsze można uzyskać dostęp. Gdy węzeł mobilny jest w domu, łączy się z linkiem domowym i używa swojego adresu domowego. Gdy węzeł mobilny jest z dala od domu, agent macierzysty, który jest zwykle routerem, przekazuje wiadomości między węzłem mobilnym a węzłami, z którymi się komunikuje.  
  
## <a name="see-also"></a>Zobacz też

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
