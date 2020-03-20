---
title: Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: f0c9ecaacc1d875aac8eed61a85ca7579f5cb8a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64649528"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje
Obszar <xref:System.Net.PeerToPeer.Collaboration> nazw udostępnia klasy i interfejsy API, które są używane do implementowania działań współpracy równorzędnej przy użyciu infrastruktury współpracy peer-to-peer.  
  
## <a name="classes"></a>Klasy  
 Główne klasy używane w implementacji działania współpracy peer-to-peer są:  
  
- Program <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, który może służyć do przechowywania kontaktów równorzędnych.  
  
- W <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> którym można współpracować, takich jak gra, klient czatu lub rozwiązanie konferencyjne.  
  
- Elementy równorzędne, które będą współpracować w działaniu.  Te elementy równorzędne mogą być reprezentowane jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact> <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, lub <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> obiekty.  
  
- Sama klasa <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> statyczna, która określa, które aplikacje są dostępne i które elementy równorzędne uczestniczą w nich.  
  
 Metody <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> są używane do zapraszania rysów do sesji współpracy.  Wywołujący element równorzędny może subskrybować innego elementu równorzędnego dla zdarzeń, które sygnalizują aktualizacje informacji o aplikacji, obiekcie lub obecności powiązanych z sesją współpracy. Klasy obecności określają, czy <xref:System.Net.PeerToPeer.Collaboration.Peer> a jest <xref:System.Net.PeerToPeer.Collaboration.PeerScope> dostępny do współpracy, a klasa jest używana <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> do <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>określania, ile <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>uczestnictwa jest dozwolone dla elementu równorzędnego: (globalny), , (podsieć) lub .  
  
 Sesja współpracy składa się z czterech kroków:  
  
- Odnajdywanie. Odnajdowanie lub publikowanie aplikacji, rysów i informacji o obecności.  Na przykład znajdź inne osoby w podsieci lokalnej, które mają zainstalowane te same gry.  
  
- Zaproszenie. Wysyłanie i akceptowanie bezpiecznych zaproszeń dla <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> zdalnych elementów równorzędnych do rozpoczynania lub dołączania do sesji.  
  
- Zarządzanie kontaktami. Dodaj odnalezione elementy <xref:System.Net.PeerToPeer.Collaboration.ContactManager>równorzędne jako kontakt do pliku .  
  
- Komunikacji. Po ustanowieniu komunikacji należy <xref:System.Net> użyć interfejsów <xref:System.Net.PeerToPeer> API, interfejsu API lub klas kanału równorzędnego fundacji komunikacji systemu Windows dla komunikacji wielopartyjnej.  
  
 Na przykład element równorzędny hosta rozpoczyna <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> sesję współpracy i wykorzystuje metodę dodawania zdalnego elementu równorzędnego i jednego z jego lokalnych elementów równorzędnych do Menedżera kontaktów elementu równorzędnego hosta.  Następnie trzej użytkownicy wezmą udział we własnej prywatnej sesji współpracy.  
  
 Typowe aplikacje P2P to: połączenia konferencyjne do wspólnego robienia notatek lub tablicowania, aplikacje czatu bezserwerowe, interaktywne reklamy i sesje gier online.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer.Collaboration>
