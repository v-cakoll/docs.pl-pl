---
title: Scenariusze sieci równorzędnych
ms.date: 03/30/2017
ms.assetid: d23b1a64-2e08-4014-882a-c1dd766bdcc2
ms.openlocfilehash: 9b5d4d35085585fe04f2f0c0a105e6dff4b1fcc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "64623088"
---
# <a name="peer-to-peer-networking-scenarios"></a>Scenariusze sieci równorzędnych

Sieci peer-to-peer umożliwia lub ulepsza następujące scenariusze:

## <a name="real-time-communications-rtc"></a>Komunikacja w czasie rzeczywistym (RTC)

- Wiadomości błyskawiczne bezserwerowe

  RTC istnieje dzisiaj. Użytkownicy komputerów mogą rozmawiać i prowadzić rozmowy głosowe lub wideo ze swoimi rówieśnikami. Jednak wiele istniejących programów i ich protokołów komunikacyjnych polega na serwerach do działania. Jeśli uczestniczysz w sieci bezprzewodowej ad hoc lub jesteś częścią izolowanej sieci, nie możesz korzystać z tych obiektów RTC. Technologia peer-to-peer umożliwia rozszerzenie technologii RTC na te dodatkowe środowiska sieciowe.

- Dobieranie graczy w czasie rzeczywistym i rozgrywka

  Podobnie jak RTC, gra w czasie rzeczywistym istnieje dzisiaj. Istnieje wiele stron internetowych gier, które zaspokajają społeczności graczy za pośrednictwem Internetu. Oferują one możliwość znalezienia innych graczy o podobnych zainteresowaniach i grać razem. Problem polega na tym, że strony gry istnieją tylko w Internecie i są nastawione na zapalonych graczy, którzy chcą grać przeciwko najlepszym graczom na świecie. Witryny te śledzą i dostarczają statystyki, aby pomóc w tym procesie. Jednak te strony nie pozwalają graczowi na skonfigurowanie gry ad-hoc wśród znajomych w różnych środowiskach sieciowych. Sieci peer-to-peer może zapewnić tę możliwość.

## <a name="collaboration"></a>Współpraca

- Obszary robocze projektu rozwiązujące cel

  Udostępnione aplikacje obszaru roboczego umożliwiają tworzenie grup roboczych ad hoc, a następnie umożliwiają właścicielom grup roboczych wypełnianie udostępnionego obszaru roboczego narzędziami i zawartością, które pozwolą grupie rozwiązać problem. Może to obejmować fora dyskusyjne, narzędzia zwiększające produktywność i pliki.

- Udostępnianie plików innym osobom

  Podzbiór udostępniania obszaru roboczego projektu to możliwość udostępniania plików. Chociaż ta możliwość istnieje dziś w obecnej wersji systemu Windows, można ją ulepszyć za pomocą sieci peer-to-peer, aby zawartość plików była dostępna w łatwy i przyjazny sposób. Umożliwienie łatwego dostępu do niesamowitego bogactwa treści na obrzeżach Internetu lub w środowiskach komputerowych ad hoc zwiększa wartość komputerów sieciowych.

- Dzielenie się doświadczeniami

  Dzięki łączności bezprzewodowej staje się coraz bardziej rozpowszechnione, peer-to-peer sieci pozwala być online w grupie rówieśników i być w stanie podzielić się swoimi doświadczeniami (takie jak zachód słońca, koncert rockowy, lub rejs wakacje), podczas gdy występują.

## <a name="content-distribution"></a>Dystrybucja zawartości

- Wiadomości SMS

  Sieci peer-to-peer mogą umożliwiać rozpowszechnianie informacji tekstowych w postaci plików lub wiadomości do dużej grupy użytkowników. Przykładem jest lista wiadomości.

- Dźwięk i wideo

  Sieci peer-to-peer mogą również umożliwiać rozpowszechnianie informacji audio lub wideo wśród dużej grupy użytkowników, takich jak duży koncert lub spotkanie firmowe. Aby rozpowszechniać zawartość dzisiaj, należy skonfigurować serwery o dużej pojemności do zbierania i dystrybucji obciążenia do setek lub tysięcy użytkowników. Dzięki sieci peer-to-peer tylko garstka elementów równorzędnych faktycznie uzyskałaby zawartość ze scentralizowanych serwerów. Ci rówieśnicy zalaliby te informacje jeszcze kilkoma osobami, które wysyłają je do innych i tak dalej. Obciążenie dystrybucji zawartości jest dystrybuowane do wiązek pracy w chmurze. Element równorzędny, który chce otrzymać zawartość, znajdzie najbliższy element równorzędny dystrybucji i pobierze od nich zawartość.

- Dystrybucja aktualizacji produktów

  Sieci peer-to-peer mogą również zapewnić skuteczny mechanizm dystrybucji oprogramowania, takiego jak aktualizacje produktów (aktualizacje zabezpieczeń i dodatki Service Pack). Element równorzędny, który ma połączenie z serwerem dystrybucji oprogramowania, może uzyskać aktualizację produktu i propagować ją innym członkom swojej grupy.

## <a name="distributed-processing"></a>Przetwarzanie rozproszone

- Podział i podział zadania

  Duże zadanie obliczeniowe można najpierw podzielić na oddzielne mniejsze zadania obliczeniowe dobrze dostosowane do zasobów obliczeniowych elementu równorzędnego. Element równorzędny może wykonać podział zadania przetwarzania dużych. Następnie sieci peer-to-peer można dystrybuować poszczególne zadania do oddzielnych elementów równorzędnych w grupie. Każdy element równorzędny wykonuje swoje zadanie obliczeniowe i zgłasza jego wynik z powrotem do scentralizowanego punktu akumulacji.

- Agregacja zasobów komputera

  Innym sposobem wykorzystania sieci peer-to-peer do przetwarzania rozproszonego jest uruchamianie programów na każdym elementów równorzędnych, które działają w czasie bezczynności procesora i są częścią większego zadania obliczeniowego, które jest koordynowane przez serwer centralny. Dzięki agregowaniu procesorów wielu komputerów sieci peer-to-peer mogą przekształcić grupę komputerów równorzędnych w duży procesor równoległy do wykonywania dużych zadań obliczeniowych.

## <a name="see-also"></a>Zobacz też

- <xref:System.Net.PeerToPeer.Collaboration>
