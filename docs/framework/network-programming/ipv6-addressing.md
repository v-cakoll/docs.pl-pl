---
title: Adresowanie IPv6
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: c922c2bc7908803f2215cd4dac108cc3c523ce28
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647315"
---
# <a name="ipv6-addressing"></a>Adresowanie IPv6
W przypadku protokołu internetowego w wersji 6 (IPv6) adresy są długości 128 bitów. Jednym z powodów takich duża przestrzeń adresowa jest pozwalające na dalszy podział dostępnych adresów w hierarchii domen routingu, które odzwierciedlają topologii sieci Internet. Kolejny powód jest mapowania adresów karty sieciowe (lub interfejsy) łączące urządzenia w sieci. Protokół IPv6 funkcji nieprzerwaną pracę możliwość rozpoznania adresów na najniższym poziomie, znajduje się na poziomie interfejsu sieciowego, która ma również funkcji automatycznej konfiguracji.  
  
## <a name="text-representation"></a>Tekst reprezentujący  
 Poniżej przedstawiono trzy formy konwencjonalne używana do reprezentowania adresy IPv6 jako ciąg tekstowy:  
  
- **Formularz szesnastkowe dwukropek**. Jest to n:n:n:n:n:n:n:n preferowaną formę. Każdy n oznacza wartość szesnastkową jednego z ośmiu elementów 16-bitowych w adresie. Na przykład: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
- **Skompresowane formularza**. Ze względu na długość adresu jest często mają adresów zawierających ciąg zer. Aby uprościć zapisywania tych adresów, należy użyć skompresowaną formą, w których pojedynczego ciągu ciągłych bloków 0 są reprezentowane przez symbol dwoma dwukropkami (::). Ten symbol może wystąpić tylko raz w adresie. Na przykład adres multiemisji `FFED:0:0:0:0:BA98:3210:4562` jest skompresowaną formą `FFED::BA98:3210:4562`. Adres emisji pojedynczej `3FFE:FFFF:0:0:8:800:20C4:0` jest skompresowaną formą `3FFE:FFFF::8:800:20C4:0`. Adres sprzężenia zwrotnego `0:0:0:0:0:0:0:1` jest skompresowaną formą `::`1. Nieokreślony adres `0:0:0:0:0:0:0:0` jest skompresowaną formą `::`.  
  
- **Mieszane formularza**. Ten formularz łączy adresów IPv4 i IPv6. W tym przypadku format adresu jest n:n:n:n:n:n:d.d.d.d, gdzie każdy n wartości szesnastkowych sześciu elementów wyższego rzędu 16-bitowy adres IPv6, a każdy d reprezentuje wartość dziesiętna adres IPv4.  
  
## <a name="address-types"></a>Typy adresów  
 Wiodący bitów w adresie zdefiniować określonego typu adresu IPv6. Pole o zmiennej długości, zawierające te bitów początkowych nosi nazwę formatu prefiksu (FP).  
  
 Adres IPv6 emisji pojedynczej jest podzielona na dwie części. Pierwsza część zawiera prefiks adresu, a druga część identyfikatora interfejsu. Zwięzły sposób wyrażania kombinację adresu/prefiks IPv6 jest następująca: ipv6 — adres/długością prefiksu.  
  
 Oto przykład adresu z prefiksem 64-bitowych.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Prefiks, w tym przykładzie jest `3FFE:FFFF:0:CD30`. Adres można również będą zapisywane w postaci skompresowanej jako `3FFE:FFFF:0:CD30::/64`.  
  
 Protokół IPv6 definiuje następujące typy adresów:  
  
- **Adres emisji pojedynczej**. Identyfikator jednego interfejsu. Pakiet wysyłane na ten adres jest przekazywana do interfejsie zidentyfikowany. Adresy emisji pojedynczej różnią się od są adresami multiemisji przez wartość octet wyższego rzędu. Oktet adresy multiemisji z wartością szesnastkowe FF. Dowolna inna wartość do tego oktetu identyfikuje adresu emisji pojedynczej. Poniżej przedstawiono różne rodzaje adresy emisji pojedynczej:  
  
    - **Adresów połączenia lokalnego**. Te adresy są używane na jedno łącze i mają następujący format: FE80::*InterfaceID*. Adresów lokalnych łącza są używane między węzłami w link do konfiguracji adres automatycznego odnajdowania sąsiadów lub w przypadku routerów nie istnieje. Adres połączenia lokalnego jest używany głównie podczas uruchamiania i system nie uzyskał jeszcze adresów o większym zakresie.  
  
    - **Adresy lokacji lokalnej**. Te adresy są używane w jednej lokacji i mają następujący format: FEC0::*SubnetID*:*InterfaceID*. Adresy lokacji lokalnej są używane na potrzeby adresowania wewnątrz witryny bez konieczności stosowania prefiksu globalnego.  
  
    - **Adresy globalne emisji pojedynczej protokołu IPv6**. Te adresy mogą być używane w Internecie i ma następujący format: 010 (FP 3 bity) identyfikator TLA (13-bitowy) zarezerwowany (8 bitów), identyfikator umowy SLA ID NLA (24 bity) (16 bitów) *InterfaceID* (64-bitowy).  
  
- **Adres multiemisji**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłach). Pakiet wysyłane na ten adres jest dostarczane do wszystkich interfejsów, które są identyfikowane za pomocą adresu. Typy adresów multiemisji zastępują adresów IPv4 emisji.  
  
- **Adres emisji dowolnej**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłach). Pakiet wysyłane na ten adres jest przekazywana do tylko jeden interfejs identyfikowanych przez ten adres. Jest to interfejs najbliższej identyfikowane za pomocą metryk routingu. Adresy emisji dowolnej są pobierane z przestrzeni adresowej emisji pojedynczej i są nie do odróżnienia składniowo. Interfejs zaadresowane wykonuje rozróżnienie między adresy emisji pojedynczej i emisji dowolnej, w zależności od jego konfiguracji.  
  
 Ogólnie rzecz biorąc węzeł ma zawsze adres połączenia lokalnego. Może mieć adres lokacji lokalnej i co najmniej jeden adres globalnego.  
  
## <a name="see-also"></a>Zobacz także

- [Protokół IPv6](../../../docs/framework/network-programming/internet-protocol-version-6.md)
- [Gniazda](../../../docs/framework/network-programming/sockets.md)
