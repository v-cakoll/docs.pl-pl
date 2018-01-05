---
title: Scenariusze sieci peer-to-Peer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
caps.latest.revision: "4"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 5f7da4f1587eb0029cafb482bc2c60f5b19f23f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="peer-to-peer-networking-scenarios"></a>Scenariusze sieci peer-to-Peer
Sieci peer-to-peer umożliwia lub rozszerza następujące scenariusze:  
  
## <a name="real-time-communications-rtc"></a>Komunikacji w czasie rzeczywistym (RTC)  
  
-   Niekorzystającą wiadomości błyskawicznych  
  
 RTC istnieje już dzisiaj. Użytkownicy komputerów można umożliwić rozmowy i ma obecnie głosu lub wideo konwersacji z ich komputerami równorzędnymi. Jednak wielu istniejących programów i ich protokołów komunikacyjnych zależą od serwerów. Jeśli uczestniczą w trybie ad hoc sieci bezprzewodowej lub są częścią sieci izolowanej, to nie można używać urządzeń tych RTC. Technologia peer-to-peer umożliwia rozszerzenie RTC technologie, aby te dodatkowe środowiska sieciowego.  
  
-   W czasie rzeczywistym matchmaking i gry  
  
 Podobny do RTC, w czasie rzeczywistym gry istnieje już dzisiaj. Istnieje wiele opartych na sieci Web gier witryn, które automatycznie dostosowują się do społeczność graczy za pośrednictwem Internetu. Oferują one możliwość znaleźć inne gracze o podobnych zainteresowań i gry razem. Problem jest gier witryn istnieje tylko w Internecie i są skierowaną do zapalonych graczy kto chce Graj z najlepszych graczy na całym świecie. Te witryny śledzenia i podaj statystyk, aby pomóc w procesie. Jednak te witryny nie zezwalają graczy do skonfigurowania gry ad hoc między znajomych w różnych środowiskach sieci. Sieci peer-to-peer zapewniają taką możliwość.  
  
## <a name="collaboration"></a>Współpraca  
  
-   Obszary robocze projektu rozwiązywania cel  
  
 Udostępnionego obszaru roboczego aplikacje umożliwiają tworzenie grup roboczych ad hoc, a następnie zezwolić właścicielom grupy roboczej wypełnić udostępnionego obszaru roboczego z narzędziami i zawartość, która umożliwia grupie, aby rozwiązać problem. Mogą one obejmować tablic wiadomości, narzędzia do pracy biurowej i plików.  
  
-   Udostępnianie plików  
  
 Podzbiór udostępnianie obszaru roboczego projektu jest możliwość udostępniania plików. Mimo że tę możliwość obecnie istnieje z bieżącej wersji systemu Windows, może zostać poprawione za pośrednictwem sieci peer-to-peer, aby udostępnić zawartość pliku w sposób łatwy i przyjazny. Stosowanie łatwy dostęp do bardzo wiele materiałów na krawędzi w Internecie lub w środowiskach obliczeniowych ad hoc zwiększa wartość przetwarzania danych w sieci.  
  
-   Udostępnianie środowiska  
  
 Łączności bezprzewodowej się coraz bardziej powszechnie, sieci peer-to-peer umożliwia w trybie online w grupie elementów równorzędnych i można podzielić się doświadczeniami (na przykład cennik porozumieniu skale lub rejs urlopu) podczas, gdy są one wykonywane.  
  
## <a name="content-distribution"></a>Dystrybucja zawartości  
  
-   Wiadomości SMS  
  
 Rozpowszechnianie informacji tekstowych w formie plików lub wiadomości dla dużej grupy użytkowników umożliwiają sieci peer-to-peer. Przykładem jest listy wiadomości.  
  
-  
  
-   Audio i wideo  
  
 Umożliwiają również sieci peer-to-peer rozpowszechnianie informacji audio i wideo w dużej grupie użytkowników, takich jak duże spotkanie porozumieniu lub firmy. Aby rozesłać zawartość dzisiaj, należy skonfigurować serwery dużej pojemności do gromadzenia i rozkładanie obciążenia setek lub tysięcy użytkowników. Z obsługą sieci peer-to-peer, tylko kilka elementów równorzędnych faktycznie otrzyma ich zawartość z serwerów scentralizowane. Tych elementów równorzędnych czy wypełniania te informacje na kilka większej liczbie użytkowników, którzy wysyłają je do innych użytkowników i tak dalej. Obciążenia dystrybucji zawartość jest dystrybuowana do elementów równorzędnych w chmurze. Równorzędnej, która chce odbierać zawartość będzie znaleźć najbliższy dystrybuowanie elementów równorzędnych i Pobierz zawartość z nich.  
  
-  
  
-   Dystrybucji aktualizacji produktów  
  
 Sieci peer-to-peer, można też podać wydajny mechanizm do dystrybucji oprogramowania, takiego jak aktualizacje produktu (aktualizacje zabezpieczeń i dodatki service pack). Elementu równorzędnego, który jest podłączony do serwera dystrybucji oprogramowania można uzyskać aktualizację produktu i propagację go do elementów członkowskich grupy.  
  
-  
  
## <a name="distributed-processing"></a>Przetwarzanie rozproszone  
  
-   Dzielenie i dystrybucji zadania  
  
 Dużych zadań przetwarzania danych można najpierw podzielić na oddzielnych mniejszych zadań dobrze nadaje się do zasobów komputerowych elementu równorzędnego. Element równorzędny może wykonać dzielenie dużych zadań przetwarzania danych. Następnie sieci peer-to-peer można rozpowszechniać poszczególne zadania do oddzielnych elementów równorzędnych w tej grupie. Każdy komputer wykonuje jego zadanie przetwarzania danych i raporty wyniku wstecz punktu gromadzenia scentralizowane.  
  
-   Agregacja zasobów komputera  
  
 Innym sposobem wykorzystywać sieci peer-to-peer dla przetwarzania rozproszonego jest uruchamianie programów na każdy komputer, które uruchamiane podczas czas bezczynności procesora i są częścią większych zadanie przetwarzania danych, które jest koordynowane przez centralnego serwera. Przez agregowanie procesory z wielu komputerów, sieci peer-to-peer można przekształcić w grupy komputerów równorzędnych dużych procesor równoległe w przypadku dużych zadań.  
  
-  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.PeerToPeer.Collaboration>
