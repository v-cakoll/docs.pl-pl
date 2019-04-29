---
title: Współpraca równorzędna
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 91e9179fc426934e78a1e0223c9bffafe5efbef1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642038"
---
# <a name="peer-to-peer-collaboration"></a>Peer-to-peer współpracy

Sieci peer-to-peer to wykorzystania stosunkowo zaawansowanych komputerów (komputery osobiste), znajdujące się na granicy Internetu dla zadań obliczeniowej więcej niż tylko opartego na kliencie. Nowoczesne komputer osobisty (PC) ma bardzo szybki procesor, pamięć ogromna i dużych dysków twardych, które są w pełni wykorzystywane podczas wykonywania typowych zadań obliczeniowych, takich jak wiadomości e-mail i przeglądania sieci Web. Nowoczesnych PC łatwo może działać jako klient i serwer (element równorzędny) dla wielu typów aplikacji.  
  
Infrastruktura współpracy Peer-to-Peer jest uproszczone wdrożenia infrastruktury Peer-to-Peer Microsoft Windows, który wykorzystuje osoby w pobliżu mnie usługi w systemach Windows Vista i nowszych platform. Najlepiej jest używana dla aplikacji z obsługą elementów równorzędnych w obrębie podsieci dla którego osoby w pobliżu mi usługa działa, chociaż może obsłużyć, punkty końcowe w Internecie lub także kontaktów. Zawiera typowe skontaktuj się z kierownika któremu jest używany przez Live Messenger i innych aplikacji obsługujących na żywo, aby określić, skontaktuj się z punktami końcowymi, dostępności i obecności.  
  
## <a name="collaboration-applications"></a>Aplikacje współpracy

 Aplikacja typowych współpracy peer-to-peer składa się z następujących czynności:  
  
- Elementu równorzędnego określa tożsamość elementu równorzędnego, kto jest zainteresowany hostingu sesji współpracy  
  
- Do obsługi sesji zostaje wysłane żądanie licencjonowania, jakiś sposób, i elementu równorzędnego hosta wyraża zgodę na zarządzanie działania współpracy.  
  
- Host zaprasza kontaktów w podsieci (w tym obiekt żądający) do sesji.  
  
- Wszystkich elementów równorzędnych, którzy chcą współpracy może dodać hosta do ich menedżerów skontaktuj się z pomocą.  
  
- Większość elementów równorzędnych będzie wysyłać odpowiedzi na zaproszenie zaakceptowane lub odrzucone, powrót do elementu równorzędnego hosta w odpowiednim czasie.  
  
- Wszystkie elementy równorzędne, którzy będą współpracować spowoduje subskrypcji na węźle równorzędnym hosta.  
  
- Podczas elementów równorzędnych wykonują czynności ich początkową współpracy, peer hosta mogą dodawać zdalnych elementów równorzędnych do swojego menedżera kontaktu. Również przetwarza wszystkie odpowiedzi zaproszenia, aby określić, kto zaakceptował, który została odrzucona, a który nie ma odpowiedzi.  Może spowodować anulowanie zaproszeń do tych, którzy nie ma odpowiedzi lub wykonywanie niektórych innych działań.  
  
- W tym momencie równorzędnej hosta można uruchomić sesję współpracy z wszystkich elementów równorzędnych zaproszonego lub zarejestrować aplikację za pomocą infrastruktury współpracy.  P2p aplikacje korzystają z infrastruktury współpracy Peer-to-Peer i <xref:System.Net.PeerToPeer.Collaboration> przestrzeni nazw na potrzeby koordynowania komunikacji dla gier, biuletyny, konferencje i inne aplikacje bezserwerowe obecności.  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpieczenia sieci peer-to-peer  

 W domenie usługi Active Directory kontrolery domeny zapewniają usługi uwierzytelniania, przy użyciu protokołu Kerberos. W środowisku bez użycia serwera elementu równorzędnego równorzędnym należy podać własny mechanizm uwierzytelniania. Peer-to-Peer Networking dowolny węzeł może pełnić urzędu certyfikacji, usuwając wymagania certyfikatu głównego w magazynie zaufany główny urząd certyfikacji każdego elementu równorzędnego. Uwierzytelnianie jest obsługiwane przy użyciu certyfikatów z podpisem własnym, w formacie certyfikatu x.509. Są certyfikaty, które są tworzone przez każdy komputer, która powoduje wygenerowanie pary kluczy publiczny klucz/prywatny i certyfikat, który jest podpisany przy użyciu klucza prywatnego. Certyfikat z podpisem własnym służy do uwierzytelniania i podaj informacje o jednostce elementów równorzędnych. Takich jak uwierzytelnianie X.509 uwierzytelnianie sieci węzłów równorzędnych opiera się na łańcuch certyfikatów śledzenia do klucza publicznego, który jest zaufany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer.Collaboration>
- [Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje](../../../docs/framework/network-programming/about-the-system-net-peertopeer-collaboration-namespace.md)
