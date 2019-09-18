---
title: Współpraca równorzędna
ms.date: 03/30/2017
ms.assetid: b6216d88-bccb-4a59-9f1c-9f751708e811
ms.openlocfilehash: 7cf92f6bf3c269e584cb8b3cdcf910be5b89fd7e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047384"
---
# <a name="peer-to-peer-collaboration"></a>Współpraca między elementami równorzędnymi

Sieć równorzędna to użycie stosunkowo wydajnych komputerów (komputerów osobistych), które znajdują się na granicy Internetu przez więcej niż tylko zadania obliczeniowe oparte na kliencie. Nowoczesny komputer osobisty (komputer) ma bardzo szybki procesor, olbrzymią pamięć i duży dysk twardy, w którym żaden z nich nie jest w pełni wykorzystany podczas wykonywania typowych zadań obliczeniowych, takich jak poczta e-mail i przeglądanie w sieci Web. Nowoczesny komputer może łatwo pełnić rolę klienta i serwera (elementu równorzędnego) dla wielu typów aplikacji.  
  
Infrastruktura współpracy równorzędnej jest uproszczoną implementacją infrastruktury równorzędnej systemu Microsoft Windows, która wykorzystuje usługę osoby niemal ja w systemie Windows Vista i nowszych platformach. Najlepiej używać w przypadku aplikacji obsługujących elementy równorzędne w podsieci, dla której działa usługa osoby niemal ja, chociaż może ona również kierować do Internetu lub kontakty. Obejmuje wspólny Menedżer kontaktów używany przez program Live Messenger i inne aplikacje obsługujące informacje na żywo w celu określenia punktów końcowych kontaktu, dostępności i obecności.  
  
## <a name="collaboration-applications"></a>Aplikacje współpracy

 Typowa aplikacja do współpracy równorzędnej składa się z następujących kroków:  
  
- Element równorzędny Określa tożsamość elementu równorzędnego, który jest interesujący hosting sesji współpracy  
  
- Żądanie hostowania sesji jest wysyłane, w dowolny sposób, a element równorzędny hosta zgadza się na zarządzanie działaniem współpracy.  
  
- Host zaprasza do sesji kontakty w podsieci (łącznie z obiektem żądającym).  
  
- Wszystkie elementy równorzędne, które chcą współpracować, mogą dodać hosta do menedżerów kontaktu.  
  
- Większość elementów równorzędnych wyśle odpowiedzi na zaproszenie, niezależnie od tego, czy zostały zaakceptowane lub odrzucone, z powrotem do węzła równorzędnego hosta.  
  
- Wszystkie elementy równorzędne, które chcą współpracować, będą subskrybować elementy równorzędne hosta.  
  
- Gdy elementy równorzędne wykonują swoje początkowe działania dotyczące współpracy, element równorzędny hosta może dodać zdalnych elementów równorzędnych do Menedżera kontaktów. Przetwarza także wszystkie odpowiedzi na zaproszenia, aby określić, kto zaakceptował, kto odrzucił i kto nie odpowiedział.  Może ona anulować zaproszenia do osób, które nie odpowiedziały lub wykonywać inne działania.  
  
- W tym momencie element równorzędny hosta może rozpocząć sesję współpracy ze wszystkimi zaproszonymi elementami równorzędnymi lub zarejestrować aplikację w infrastrukturze współpracy.  Aplikacje P2P wykorzystują infrastrukturę współpracy równorzędnej i <xref:System.Net.PeerToPeer.Collaboration> przestrzeń nazw w celu koordynowania komunikacji dla gier, tablic biuletynów, konferencji i innych aplikacji niezwiązanych z nieobecnością serwerów.  
  
## <a name="peer-to-peer-networking-security"></a>Zabezpieczenia sieci równorzędnej  

 W domenie Active Directory kontrolery domeny zapewniają usługi uwierzytelniania przy użyciu protokołu Kerberos. W środowisku równorzędnym bezserwerowym elementy równorzędne muszą zapewnić własne uwierzytelnianie. W przypadku sieci równorzędnej dowolny węzeł może pełnić rolę urzędu certyfikacji, usuwając wymóg certyfikatu głównego w zaufanym magazynie głównym każdego elementu równorzędnego. Uwierzytelnianie jest zapewniane przy użyciu certyfikatów z podpisem własnym, sformatowane jako certyfikaty X. 509. Są to certyfikaty, które są tworzone przez poszczególne elementy równorzędne, które generują parę klucz publiczny/prywatny i certyfikat podpisany przy użyciu klucza prywatnego. Certyfikat z podpisem własnym jest używany do uwierzytelniania i dostarczania informacji o jednostce równorzędnej. Podobnie jak w przypadku uwierzytelniania X. 509, Uwierzytelnianie sieci równorzędnej polega na śledzeniu łańcucha certyfikatów z powrotem do klucza publicznego, który jest zaufany.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer.Collaboration>
- [Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje](about-the-system-net-peertopeer-collaboration-namespace.md)
