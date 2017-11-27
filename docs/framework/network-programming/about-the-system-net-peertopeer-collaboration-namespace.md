---
title: "Namespace System.Net.PeerToPeer.Collaboration — informacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5d8c1c1-6844-4947-9759-c7f1b564bded
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696b1d3dd7312b52c28f11f64f007c29fb8a94b5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="about-the-systemnetpeertopeercollaboration-namespace"></a>Namespace System.Net.PeerToPeer.Collaboration — informacje
<xref:System.Net.PeerToPeer.Collaboration> Przestrzeń nazw zawiera klasy i interfejsy API, które są używane do wykonywania działań współpracy elementów równorzędnych przy użyciu infrastruktury współpracy Peer-to-Peer.  
  
## <a name="classes"></a>Klasy  
 Klasy głównym zastosowany w implementacji działania współpracy Peer-to-Peer są:  
  
-   <xref:System.Net.PeerToPeer.Collaboration.ContactManager>, Które mogą służyć do przechowywania elementów równorzędnych kontaktów.  
  
-   <xref:System.Net.PeerToPeer.Collaboration.PeerApplication> Umożliwiającym współpracę, takie jak gry, klient rozmów lub konferencji rozwiązania.  
  
-   Elementów równorzędnych, które będą współpracować w działaniu.  Tych elementów równorzędnych może być reprezentowana jako <xref:System.Net.PeerToPeer.Collaboration.PeerContact>, <xref:System.Net.PeerToPeer.Collaboration.PeerNearMe>, lub <xref:System.Net.PeerToPeer.Collaboration.PeerEndPoint> obiektów.  
  
-   Statycznych <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> klasy siebie, który określa, które aplikacje są dostępne i komputerów równorzędnych uczestniczą w nich.  
  
 <xref:System.Net.PeerToPeer.Collaboration.PeerContact.Invite%2A> Metody są używane z zaproszeniem dla elementów równorzędnych do sesji współpracy.  Wywołanie elementu równorzędnego mogą subskrybować innego elementu równorzędnego dla zdarzeń, że aktualizacje sygnał do aplikacji, obiektów lub obecności informacji powiązane z sesją współpracy. Określ klasy obecności czy <xref:System.Net.PeerToPeer.Collaboration.Peer> jest dostępny do współpracy i <xref:System.Net.PeerToPeer.Collaboration.PeerScope> klasa jest używana do określania, ile udział jest dozwolone dla elementu równorzędnego: <xref:System.Net.PeerToPeer.Collaboration.PeerScope.Internet> (globalne) <xref:System.Net.PeerToPeer.Collaboration.PeerScope.NearMe>, (podsieć) lub <xref:System.Net.PeerToPeer.Collaboration.PeerScope.None>.  
  
 Sesję współpracy składa się z czterech etapów:  
  
-   Odnajdywanie. Wykrywanie i publikowania aplikacji, elementów równorzędnych i informacji o obecności.  Na przykład znaleźć inne osoby w podsieci lokalnej, który ma tego samego gier zainstalowanych.  
  
-   Zaproszenia. Wysyłanie i zaakceptować bezpiecznego zaproszeń do zdalnego peer(s) start lub dołączyć <xref:System.Net.PeerToPeer.Collaboration.PeerCollaboration> sesji.  
  
-   Skontaktuj się z zarządzania. Dodawanie odnalezionych elementów równorzędnych jako kontakt <xref:System.Net.PeerToPeer.Collaboration.ContactManager>.  
  
-   Komunikacji. Po nawiązaniu komunikacji, użyj <xref:System.Net> interfejsów API, <xref:System.Net.PeerToPeer> interfejsu API lub klasy kanału równorzędnego Foundation komunikacji Windows wielopartyjnej komunikacji.  
  
 Na przykład równorzędnej hosta uruchamia sesję współpracy i korzysta z <xref:System.Net.PeerToPeer.Collaboration.ContactManager.CreateContact%2A> metody w celu dodania komputer zdalny, a jeden z jego elementów równorzędnych w lokalnej elementu równorzędnego hosta do menedżera kontaktu.  Trzech użytkowników będzie następnie uczestniczyć w sesji współpracy prywatnych.  
  
 Typowe aplikacje P2P: konferencji współpracy notatek lub whiteboarding, aplikacji niekorzystającą rozmowy, interakcyjne anonsów i sesje gier online.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer.Collaboration>
