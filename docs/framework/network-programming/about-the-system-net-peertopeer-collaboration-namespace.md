---
title: Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje
ms.date: 03/30/2017
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
ms.openlocfilehash: a62b659472f6d05e61672fa603e8663d9946977e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867007"
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>Przestrzeń nazw System.Net.PeerToPeer.Collaboration — informacje
<xref:System.Net.PeerToPeer.Collaboration> Przestrzeń nazw zawiera klasy i interfejsy API, które są używane do wykonywania działań współpracy elementów równorzędnych przy użyciu infrastruktury współpracy Peer-to-Peer.  
  
## <a name="classes"></a>Klasy  
 Główne klasy używane w celu wykonania działania współpracy Peer-to-Peer są:  
  
- <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Który może służyć do przechowywania elementu równorzędnego kontaktów.  
  
- <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> , Umożliwiający współpracę, takich jak gry, klient rozmowy lub konferencji rozwiązania.  
  
- Elementów równorzędnych, które będą współpracować w działaniu.  Tych elementów równorzędnych może być reprezentowana jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, lub <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> obiektów.  
  
- Statyczne <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> samej, która określa, które aplikacje są dostępne i które kolegami uczestniczą w nich klasy.  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Metody są używane do zapraszania równorzędnych do sesji współpracy.  Wywołania elementów równorzędnych może subskrybować innego elementu równorzędnego dla zdarzeń, że aktualizacje sygnał do aplikacji, obiekt lub obecności informacji powiązane z sesji współpracy. Określ klasy obecności czy <xref:System.Net.PeerToPeer.Collaboration.Peer> jest dostępny do pracy zespołowej i <xref:System.Net.PeerToPeer.Collaboration.PeerScope> klasa jest używana do określenia, ile udział jest dozwolona dla elementu równorzędnego: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (globalna) <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (podsieć) lub <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 Sesja współpracy składa się z czterech krokach:  
  
- Odnajdywanie. Odkryj lub publikowania aplikacji, partnerom i informacje o obecności.  Na przykład znaleźć inne osoby w podsieci lokalnej, który ma ten sam gier zainstalowanych.  
  
- Zaproszenie. Wysyłanie i zaakceptować zaproszenia bezpieczny dla zdalnego peer(s) uruchomić lub dołączyć <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sesji.  
  
- Skontaktuj się z zarządzania. Dodawanie odnalezionych elementów równorzędnych jako kontakt do <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
- Komunikacja. Po nawiązaniu komunikacji, użyj <xref:System.Net> interfejsów API, <xref:System.Net.PeerToPeer> interfejsu API lub klasy programu Windows Communication Foundation kanał elementu równorzędnego w komunikacji wielostronnej.  
  
 Na przykład element równorzędny hosta uruchamia sesję współpracy i korzysta z <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> metody w celu dodania elementu równorzędnego zdalnego i jeden z jego elementów równorzędnych w lokalnym do Menedżera skontaktuj się z elementu równorzędnego hosta.  Trzech użytkowników będzie następnie uczestniczyć w sesji prywatnej współpracy.  
  
 Typowe aplikacje P2P: konferencji współpracy notatek lub pracę na tablicach, aplikacje bezserwerowe rozmowy, interaktywne anonsów i sesje gier online.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.PeerToPeer.Collaboration>
