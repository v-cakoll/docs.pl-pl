---
title: Siatki elementów równorzędnych
ms.date: 03/30/2017
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
ms.openlocfilehash: afd9eae36f28c28b33b74c4456feb4ba8c91314d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766795"
---
# <a name="peer-meshes"></a>Siatki elementów równorzędnych
A *siatki* jest nazywany kolekcją (wykres wzajemnie połączonych) węzłów równorzędnych, który może komunikować się między sobą i które są identyfikowane przez identyfikator unikatowy siatki Każdy węzeł jest połączony z wielu innych węzłów. W dobrze połączonych siatki istnieje ścieżka między dwoma węzłami, przy użyciu stosunkowo kilka przeskoków między węzłami na krawędziach najdalszego siatki, i siatkę pozostanie połączony, nawet jeśli niektóre węzły lub połączenia z nich ją. Aktywnych węzłów w siatce publikuje swoje informacje o punkcie końcowym z odpowiedni identyfikator siatki tak, aby je znaleźć innych elementów równorzędnych.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Właściwości siatki utworzone za pomocą kanału równorzędnego  
  
#### <a name="uniquely-identified"></a>Jednoznacznie zidentyfikować  
  
- Unikatowy identyfikator identyfikuje każdy siatki. Nazwa siatki (lub identyfikator siatki) jest w tym samym formacie co nazwa hosta systemu nazw domen (DNS, Domain Name System). Jako takie ten identyfikator siatki, musi być unikatowa dla właściwego klienta w zakresie stosowania mechanizmu rozpoznawania używany. Nazwa pospolita, takie jak "MyFamilysPeers" lub "KevinsPokerTable," łatwo może dojść do kolizji z nazwami innych użytkowników i niezamierzone elementów równorzędnych może zwrócić informacje o punkcie końcowym, który może spowodować problemy z zachowania lub zwiększyć czas oczekiwania na połączenie. Jednym ze sposobów, aby uniknąć tych problemów może być Dodaj Unikatowy identyfikator jako przyrostkowe do pseudonimu dla siatki (na przykład "KevinsPokerTable90210").  
  
#### <a name="message-flooding"></a>Komunikat o przepełnieniu  
  
- Siatka umożliwia propagowane do innych węzłów elementów równorzędnych w tej samej siatki z co najmniej jeden nadawców wiadomości. Komunikaty nadmiernej ilości danych przez węzły równorzędne Użyj nagłówków określone w przestrzeni nazw na `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>Zoptymalizowane połączeń  
  
- Siatki kanał elementu równorzędnego są automatycznie dostosowuje, gdy węzły Dołącz wyjść, zapewniając, że wszystkie węzły mają dobrej łączności z niewielkie prawdopodobieństwo tworzenie partycji (grupy węzłów odizolowane od siebie). Połączenia w siatce również dynamiczne są optymalizowane w oparciu o bieżące wzorce ruchu, aby możliwie najmniejsze opóźnienie wiadomości od nadawcy do odbiorcy.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Sieć popularnych funkcji zapewniających kanał elementu równorzędnego nie  
 Należy mieć świadomość sieci popularnych funkcji zapewniających kanał elementu równorzędnego nie. Te funkcje, które mogą wszystkie zostać posiadanych kanał elementu równorzędnego, są następujące:  
  
- **Kolejność komunikatów:** Komunikatów pochodzących z jednego źródła nie może pojawić się na wszystkich innych stron w tej samej kolejności lub w kolejności wysyłane źródła. Aplikacje, które wymagają komunikaty były dostarczane w określonej kolejności wbudować go w swoich aplikacjach (na przykład w wyniku umieszczenia monotonicznie rosnący identyfikator przy użyciu wszystkich komunikatów).  
  
- **Niezawodna obsługa komunikatów:** Kanał elementu równorzędnego nie obejmuje mechanizmu, aby zapewnić odbiór wiadomości przez wszystkich elementów równorzędnych. Aby zagwarantować dostarczanie komunikatów, należy napisać warstwę niezawodności na podstawie kanał elementu równorzędnego.
