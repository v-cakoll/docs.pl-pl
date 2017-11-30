---
title: Adresowanie IPv6
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: be73fe51e6b3a52ccb2717f0216ab82b90dd9841
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ipv6-addressing"></a>Adresowanie IPv6
W Internet Protocol w wersji 6 (IPv6) adresy to 128 bitów. Jedną z przyczyn miejsca długich adresów jest dalszy dostępnych adresów do hierarchii domen routingu, które odzwierciedlać topologii sieci Internet. Kolejny powód jest mapowania adresów karty sieciowe (lub interfejsy) łączące urządzeń w sieci. IPv6 funkcjami związanego z używaniem możliwość rozpoznawania adresów na najniższym poziomie, który znajduje się na poziomie interfejsu sieciowego i zapewnia również funkcję automatycznej konfiguracji.  
  
## <a name="text-representation"></a>Reprezentacja tekstowa  
 Poniżej przedstawiono trzy konwencjonalnych form używany do reprezentowania adresów IPv6 jako ciąg tekstowy:  
  
-   **Formularz szesnastkowy dwukropek**. Jest to n:n:n:n:n:n:n:n preferowanych formularza. Każdy n oznacza szesnastkowej wartości jednego z elementów osiem 16-bitowego adresu. Na przykład: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.  
  
-   **Skompresowane formularza**. Z powodu długości adres jest często mają adresów zawierających ciąg zer. Aby uprościć zapisywania tych adresów, formularz skompresowany, w którym pojedynczego ciągłej sekwencji 0 bloki są reprezentowane przez symbol podwójnego dwukropka (:). Ten symbol może wystąpić tylko raz w adresie. Na przykład adres multiemisji `FFED:0:0:0:0:BA98:3210:4562` w postaci skompresowanej jest `FFED::BA98:3210:4562`. Adres emisji pojedynczej `3FFE:FFFF:0:0:8:800:20C4:0` w postaci skompresowanej jest `3FFE:FFFF::8:800:20C4:0`. Adres sprzężenia zwrotnego `0:0:0:0:0:0:0:1` w postaci skompresowanej jest `::`1. Adres nieokreślony `0:0:0:0:0:0:0:0` w postaci skompresowanej jest `::`.  
  
-   **Mieszane formularza**. Ten formularz łączy adresów IPv4 i IPv6. W takim przypadku format adresu to n:n:n:n:n:n:d.d.d.d, gdzie każdy n wartości szesnastkowe sześć elementów znaczących 16-bitowy adres IPv6, a każdy d reprezentuje wartość dziesiętna adres IPv4.  
  
## <a name="address-types"></a>Typy adresów  
 Bitów początkowych w adresie zdefiniować szczególne typ adresu IPv6. Pole o zmiennej długości, zawierające te bitów początkowych jest nazywany prefiks formatu (FP).  
  
 Adres IPv6 emisji pojedynczej jest podzielona na dwie części. Pierwsza część zawiera prefiks adresu, a druga część identyfikatora interfejsu. Krótkie sposobem express kombinację adres/prefiks IPv6 jest następująca: ipv6 — adres /-długość prefiksu.  
  
 Oto przykład adresu z prefiksem 64-bitowych.  
  
 `3FFE:FFFF:0:CD30:0:0:0:0/64`.  
  
 Prefiks, w tym przykładzie jest `3FFE:FFFF:0:CD30`. Adres może być także zapisane w postaci skompresowanej jako `3FFE:FFFF:0:CD30::/64`.  
  
 IPv6 definiuje następujące typy adresów:  
  
-   **Adres emisji pojedynczej**. Identyfikator jednego interfejsu. Pakiet wysyłany na ten adres jest dostarczane do określonych interfejsu. Adresy emisji pojedynczej różnią się od są adresami multiemisji przez wartość oktet. Oktet adresy multiemisji ma wartość szesnastkową FF. Wszelkie inne wartości dla tego octet identyfikuje adres emisji pojedynczej. Poniżej przedstawiono różne typy adresy emisji pojedynczej:  
  
    -   **Adresów połączenia lokalnego**. Te adresy są używane na jedno łącze i mają następujący format: FE80::*identyfikator interfejsu*. Adresów połączenia lokalnego są używane między węzłami łącze w przypadku konfiguracji adresu automatycznego odnajdowania sąsiadów lub gdy routerów nie istnieje. Adres połączenia lokalnego jest używany głównie podczas uruchamiania i system nie uzyskał jeszcze adresy większego zakresu.  
  
    -   **Adres lokacji lokalnej**. Te adresy są używane w jednej lokacji i mają następujący format: FEC0::*SubnetID*:*identyfikator interfejsu*. Adres lokacji lokalnej są używane do adresowania wewnątrz lokacji bez konieczności prefiksu globalnego.  
  
    -   **Adresy globalne emisji pojedynczej IPv6**. Te adresy mogą być używane w Internecie i mają następujący format: 010 (FP 3 bity) Identyfikatora TLA (bity 13) zastrzeżone (8 bitów) ID SLA ID NLA (24-bitowy) (16 bitów) *identyfikator interfejsu* (64-bitowy).  
  
-   **Adres multiemisji**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłach). Pakiet wysyłany na ten adres są dostarczane do wszystkich interfejsów identyfikowanych przez ten adres. Typy adresów multiemisji zastępują adresów IPv4 emisji.  
  
-   **Adres emisji dowolnej**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłach). Pakiet wysyłany na ten adres jest dostarczany do tylko jeden interfejs identyfikowanych przez ten adres. To interfejs najbliższej określonej za pomocą metryki routingu. Adresy emisji dowolnej są pobierane z przestrzeni adresowej emisji pojedynczej i nie są składniowo odróżnienia. Różnica między adresami emisji pojedynczej i emisji w zależności od konfiguracji wykonuje zaadresowane interfejs.  
  
 Ogólnie rzecz biorąc węzeł ma zawsze adres połączenia lokalnego. Może mieć adres lokacji lokalnej i co najmniej jeden adres globalnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Protokół internetowy w wersji 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [Gniazda](../../../docs/framework/network-programming/sockets.md)
