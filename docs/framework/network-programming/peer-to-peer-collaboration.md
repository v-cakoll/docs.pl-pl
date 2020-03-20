---
title: Współpraca równorzędna
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047384"
---
# <a name="peer-to-peer-collaboration"></a>Współpraca między elementami równorzędna

Sieci peer-to-peer to wykorzystanie stosunkowo zaawansowanych komputerów (komputerów osobistych), które istnieją na obrzeżach Internetu w przypadku nie tylko zadań obliczeniowych opartych na kliencie. Ten nowoczesny osobisty rachmistrz (PC) ma pewien bardzo szybki procesor, ogromny pamięć, i pewien duży dysk twardy, zm. żaden jesteście trwający pełno użytkować podczas wykonaniem wspólny obliczanie zadania taki jak poczta elektroniczna i Tkanina pasienie się. Nowoczesny komputer może łatwo działać zarówno jako klient, jak i serwer (równorzędny) dla wielu typów aplikacji.  
  
Infrastruktura współpracy peer-to-peer to uproszczona implementacja infrastruktury równorzędnej systemu Microsoft Windows, która wykorzystuje usługę Ludzie blisko mnie w systemie Windows Vista i nowszych platformach. Najlepiej jest używany dla aplikacji z obsługą elementów równorzędnych w podsieci, dla której działa usługa Kontakty bliskie mi, chociaż może obsługiwać internetowe punkty końcowe lub kontakty. Zawiera wspólny Contact Manager, który jest używany przez Live Messenger i innych aplikacji obsługujących na żywo do określenia punktów końcowych kontaktu, dostępności i obecności.  
  
## <a name="collaboration-applications"></a>Aplikacje do współpracy

 Typowa aplikacja do współpracy peer-to-peer składa się z następujących kroków:  
  
- Peer określa tożsamość elementu równorzędnego, który jest zainteresowany hostowanie sesji współpracy  
  
- Żądanie hosta sesji jest w jakiś sposób wysyłane, a element równorzędny hosta zgadza się zarządzać aktywnością współpracy.  
  
- Host zaprasza kontakty w podsieci (w tym żądacza) do sesji.  
  
- Wszyscy rówieśnicy, którzy chcą współpracować, mogą dodać hosta do swoich menedżerów kontaktów.  
  
- Większość rówieśników wyśle odpowiedzi na zaproszenia, niezależnie od tego, czy zostały zaakceptowane, czy odrzucone, z powrotem do elementu równorzędnego hosta w odpowiednim czasie.  
  
- Wszyscy rówieśnicy, którzy chcą współpracować, zasubskrybują element równorzędny hosta.  
  
- Podczas gdy elementy równorzędne wykonują swoje początkowe działanie współpracy, element równorzędny hosta może dodać zdalne elementy równorzędne do menedżera kontaktów. Przetwarza również wszystkie odpowiedzi na zaproszenia, aby ustalić, kto zaakceptował, kto odmówił, a kto nie odpowiedział.  Może anulować zaproszenia dla tych, którzy nie odpowiedzieli, lub wykonać inne działania.  
  
- W tym momencie element równorzędny hosta można rozpocząć sesję współpracy ze wszystkimi zaproszonymi elementami równorzędnymi lub zarejestrować aplikację w infrastrukturze współpracy.  Aplikacje P2P używają infrastruktury współpracy peer-to-peer i przestrzeni <xref:System.Net.PeerToPeer.Collaboration> nazw do koordynowania komunikacji dla gier, tablic ogłoszeń, konferencji i innych aplikacji bezserwerowych.  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpieczenia sieci peer-to-peer  

 W domenie usługi Active Directory kontrolery domeny świadczą usługi uwierzytelniania przy użyciu protokołu Kerberos. W środowisku równorzędnym bezserwerowym elementy równorzędne muszą zapewnić własne uwierzytelnianie. W przypadku sieci równorzędnych każdy węzeł może działać jako urząd certyfikacji, usuwając wymagania certyfikatu głównego w zaufanym magazynie głównym każdego elementu równorzędnego. Uwierzytelnianie jest dostarczane przy użyciu certyfikatów z podpisem własnym, sformatowanych jako certyfikaty X.509. Są to certyfikaty tworzone przez każdego elementu równorzędnego, który generuje parę klucza publicznego/klucza prywatnego i certyfikat, który jest podpisany przy użyciu klucza prywatnego. Certyfikat z podpisem własnym jest używany do uwierzytelniania i do dostarczania informacji o jednostce równorzędnej. Podobnie jak uwierzytelnianie X.509, uwierzytelnianie w sieci rówieśniczej opiera się na łańcuchu certyfikatów śledzących klucz publiczny, który jest zaufany.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer.Collaboration>
- [Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje](about-the-system-net-peertopeer-collaboration-namespace.md)
