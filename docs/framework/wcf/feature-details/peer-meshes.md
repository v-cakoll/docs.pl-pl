---
title: "Siatki elementów równorzędnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d93e312e-ac04-40f8-baea-5da1cacb546e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f70c1dfba6ceb53cd674726702c471dbe508d46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peer-meshes"></a>Siatki elementów równorzędnych
A *siatki* jest w nazwanej kolekcji (wykres połączonych) węzły równorzędne, który może komunikować się między sobą i które są identyfikowane przez identyfikator unikatowy siatki. Każdy węzeł jest podłączony do wielu innych węzłów. W dobrze połączonych sieci jest ścieżką żadnych dwóch węzłów z małej liczbie przeskoków między węzłami w ostatniej krawędzi siatkę, i siatkę pozostanie połączonych, nawet jeśli niektóre węzły lub połączeń porzucić. Aktywnych węzłów w siatce publikowanie informacji o ich punktu końcowego z odpowiedni identyfikator sieci, dzięki czemu można je znaleźć innych elementów równorzędnych.  
  
## <a name="characteristics-of-a-mesh-created-using-peer-channel"></a>Właściwości siatki utworzone za pomocą kanału równorzędnego  
  
#### <a name="uniquely-identified"></a>Unikatowa identyfikacja  
  
-   Unikatowy identyfikator identyfikuje każdego siatki. Nazwa sieci (lub identyfikator sieci) jest w tym samym formacie co nazwa hosta systemu nazw domen (DNS, Domain Name System). W efekcie tego Identyfikatora sieci musi być unikatowa dla danego klienta aplikacji w zakresie rozpoznawania używany. Nazwa pospolita, takie jak "MyFamilysPeers" lub "KevinsPokerTable", łatwo może dojść do kolizji z innymi nazwami użytkowników i niezamierzone elementów równorzędnych może zwrócić informacje o punkcie końcowym, który może spowodować problemy z prywatności lub zwiększyć opóźnienie połączenia. Jednym ze sposobów uniknąć tych problemów może być mają zostać dodane Unikatowy identyfikator jako przyrostek pseudonimu dla sieci (na przykład "KevinsPokerTable90210").  
  
#### <a name="message-flooding"></a>Zalewania wiadomości  
  
-   Sieci umożliwia propagowane do innych węzłów równorzędnych w tej samej sieci z co najmniej jednego nadawcy wiadomości. Komunikaty w sposób przez węzły równorzędne Użyj nagłówków określone w przestrzeni nazw na `http://schemas.microsoft.com/net/2006/05/peer`.  
  
#### <a name="optimized-connections"></a>Zoptymalizowane połączeń  
  
-   Siatka kanału równorzędnego automatycznie dostosowuje podczas węzłów join i pozostawić, zapewniając, że wszystkie węzły mają dobrej łączności z małego ryzyko tworzenie partycji (grupy węzłów odizolowane od siebie). W siatce są również dynamicznie optymalizowane na podstawie bieżącego wzorce ruchu, aby możliwie najmniejsze opóźnienia wiadomość od nadawcy do odbiornika.  
  
#### <a name="popular-network-features-that-peer-channel-does-not-provide"></a>Popularne sieci funkcje, które nie ma kanału równorzędnego  
 Należy mieć świadomość sieci popularnych funkcji zapewniających kanał elementu równorzędnego nie. Te funkcje, które mogą wszystkie być zbudowane w oparciu kanału równorzędnego, są następujące:  
  
-   **Porządkowanie wiadomości:** wiadomości pochodzących z jednego źródła nie może pojawić na wszystkich innych stron w tej samej kolejności lub w kolejności wysłania źródła. Aplikacje, które wymagają wiadomości były dostarczane w określonej kolejności należy utworzyć ją w swoich aplikacjach (na przykład, umieszczając w niej monotonicznie rosnący identyfikator o wszystkie komunikaty).  
  
-   **Niezawodna obsługa komunikatów:** kanał elementu równorzędnego nie ma mechanizmu zapewnić odbiór wiadomości przez wszystkie elementy równorzędne. Aby zagwarantować dostarczanie komunikatów, musi być zapisana niezawodności warstwą kanał elementu równorzędnego.
