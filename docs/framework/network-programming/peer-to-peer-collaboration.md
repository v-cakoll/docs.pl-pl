---
title: "Współpraca peer-to-Peer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 607fadad19d4fe69800798583a14d7fd9082ff23
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peer-to-peer-collaboration"></a>Współpraca peer-to-Peer
Sieci peer-to-peer jest użycie stosunkowo zaawansowanych komputerów (komputery osobiste), znajdujące się na krawędzi Internetu dla więcej niż tylko opartą na kliencie zadań. Nowoczesne komputer (komputer) ma bardzo szybko procesora, pamięci przeważająca i dużych dysków twardych, które są jest w pełni wykorzystywane podczas wykonywania typowych zadań przetwarzania danych, takie jak wiadomości e-mail i przeglądania sieci Web. Nowoczesne PC łatwo może działać jako klienta i serwera (element równorzędny) dla różnych typów aplikacji.  
  
-   Infrastruktura współpracy Peer-to-Peer jest uproszczoną implementację infrastrukturę Peer-to-Peer Microsoft Windows, która wykorzystuje osoby w pobliżu mnie usługi systemu Windows Vista i nowszych platformach. Najlepiej jest używana dla aplikacji z obsługą równorzędnej w obrębie podsieci dla którego osoby w pobliżu mnie usługa działa, chociaż może obsłużyć, punkty końcowe internet lub także kontakty. Zawiera typowe Menedżera skontaktuj się z używanym przez Live Messenger i innych aplikacji obsługujących Live ustalenie, skontaktuj się z pomocą punktów końcowych, dostępności i obecności.  
  
-  
  
## <a name="collaboration-applications"></a>Współpraca aplikacji  
 Aplikacji typowe współpracy peer-to-peer składa się z następujących czynności:  
  
-   Określa tożsamość elementu równorzędnego chcący hosting sesji współpracy, elementu równorzędnego  
  
-   Żądanie do hosta sesji jest wysyłane, aplikacja, i węzła równorzędnego hosta zgadza się zarządzanie działania współpracy.  
  
-   Host zaprasza kontakty w podsieci (w tym żądającego) do sesji.  
  
-   Wszystkie elementy równorzędne, którzy będą współpracować może dodać hosta do ich menedżerów kontaktu.  
  
-   Większość elementów równorzędnych będzie wysyłać odpowiedzi zaproszenia, czy akceptowane lub odrzucone do elementu równorzędnego hosta w odpowiednim czasie.  
  
-   Wszystkie elementy równorzędne, którzy będą współpracować spowoduje subskrypcji dla elementu równorzędnego hosta.  
  
-   Podczas elementów równorzędnych są wykonywane ich działanie początkowej współpracy, peer hosta dodać jego kontaktów Menedżerze zdalnych elementów równorzędnych. Również przetwarza wszystkie odpowiedzi zaproszenia, aby określić kto zaakceptowane, która została odrzucona, a który nie ma odpowiedzi.  Może anulować zaproszenia do tych osób, które nie zostały odebrane lub wykonywanie niektórych innych działań.  
  
-   W tym momencie równorzędnej hosta można rozpocząć sesję współpracy z wszystkie elementy równorzędne zaproszonych lub zarejestrować aplikację przy użyciu infrastruktury współpracy.  P2p aplikacje korzystają z infrastruktury współpracy Peer-to-Peer i <xref:System.Net.PeerToPeer.Collaboration> przestrzeni nazw do koordynowania komunikacji gry, biuletyny konferencji i inne aplikacje niekorzystającą obecności.  
  
-  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpieczenia sieci peer-to-Peer  
 W domenie usługi Active Directory kontrolery domeny świadczyły usługi uwierzytelniania przy użyciu protokołu Kerberos. W środowisku bez serwera równorzędnego elementów równorzędnych podać własne uwierzytelniania. Dla Peer-to-Peer Networking dowolny węzeł może działać jako urząd certyfikacji, usuwanie wymaganie certyfikatu głównego w magazynie zaufanych głównych każdy komputer. Uwierzytelnianie jest realizowane przy użyciu certyfikatów z podpisem własnym, sformatowane jako certyfikatów X.509. Są to certyfikaty, które są tworzone przez każdy komputer, który generuje pary kluczy publicznych klucza i prywatnego i certyfikatu, który jest podpisany przy użyciu klucza prywatnego. Certyfikat z podpisem własnym służy do uwierzytelniania i zawierają informacje dotyczące jednostki elementu równorzędnego. Uwierzytelnianie X.509 uwierzytelniania sieci równorzędnej, opiera się na łańcuch certyfikatów śledzenia do klucza publicznego, który jest zaufany.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer.Collaboration>  
 [Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
