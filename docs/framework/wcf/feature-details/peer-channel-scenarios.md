---
title: Scenariusze obejmujące kanał elementu równorzędnego
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: c4c24a0bafa4f73760d02de6242a9ed438d7d60e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596880"
---
# <a name="peer-channel-scenarios"></a>Scenariusze obejmujące kanał elementu równorzędnego
Interfejsy API kanału równorzędnego obsługują następujące scenariusze projektowania.  
  
## <a name="publicationsubscription-messaging"></a>Obsługa komunikatów publikacji/subskrypcji  
 Firmy, które kompilują aplikacje publikacji/subskrypcji (na przykład znaczniki giełdowe i wydawcy nagłówków wiadomości, ocen sportowych i raportów o pogodzie), mogą używać kanału równorzędnego z aplikacjami bez serwera. Na przykład użytkownicy mogą uzyskać najnowsze wyniki sportowe, łącząc wspólną siatkę (lub grupę klientów) i propagując dużą ilość aktualnych danych gry bez zwiększania obciążenia serwera. Dzięki temu dostawca danych może zapewnić wyższą jakość usługi bez znacznego zwiększenia inwestycji w technologie oparte na serwerze.  
  
## <a name="collaboration"></a>Współpraca  
 Niezależni dostawcy oprogramowania mogą tworzyć aplikacje, które umożliwiają użytkownikom tworzenie ścisłych grup do udziału w działaniach komunikacji równorzędnej. Na przykład może to dotyczyć zespołów pracujących nad projektami współpracy, udostępniania obrazów między przyjaciółmi, działaniami do planowania stron i innych. Tradycyjnie te działania zawsze obejmują serwery; jednak kanał równorzędny zapewnia możliwość wykonania tego działania w bardziej wydajny sposób, włączając scenariusze dostępu w trybie offline, które nie są tak łatwo implementowane w ramach tradycyjnego modelu serwera i klienta.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Rozproszone przetwarzanie i Klastry obliczeniowe  
 Klastry obliczeniowe i Przetwarzanie rozproszone są zwykle używane w przypadku obliczeń na dużą skalę, takich jak modelowanie finansowe/Pogoda i dekodowanie ludzkich DNA. Zazwyczaj jest to realizowane przez serwery, które indywidualnie przypisują zadania do wszystkich klientów uczestniczących w klastrze obliczeniowym. Te serwery mogą także mieć dodatkowe wymagania; na przykład wszystkie zadania mogą wymagać wykonania w określonym czasie, co wymaga więcej niż jednego komputera dla każdego zadania. Ponadto, jeśli jakikolwiek klient z uruchomionym zadaniem zostanie wyłączony, inny klient musi mieć możliwość przejęcia tego zadania i wykonania na nim pracy. Podobnie więcej niż jeden klient może być konieczne do uruchomienia tego samego zadania w celu zapewnienia spójnych wyników. Chociaż serwery programu mogą uruchamiać ten typ koordynacji klienta, można utworzyć rozwiązanie równorzędne, w którym klienci otrzymujący zadanie niezależnie określają wymagania dotyczące serwera i używają siatki obliczeniowej, aby określić, jak wykonać to zadanie.  
  
## <a name="gaming"></a>Gry  
 Korzystając z kanału równorzędnego, deweloperzy aplikacji mogą tworzyć w swoich grach wersje bez serwerów, w których gra jest przenoszona i synchronizowana z innymi graczami przez mechanizm komunikacji równorzędnej, a nie za pośrednictwem serwera centralnego. W przypadku małych niezależnych dostawców oprogramowania pomaga to wyeliminować koszty operacyjne związane z wdrażaniem, konserwacją i obsługą serwerów centralnych. Gry przeznaczone do korzystania z architektury peer-to-peer mogą być odtwarzane przez Internet lub w sieciach lokalnych sieci przewodowych lub bezprzewodowych. Dodatkowe działania dotyczące gier, takie jak lobby i rozmowa w grach, można opracowywać przy użyciu sieci równorzędnej.  
  
## <a name="see-also"></a>Zobacz też

- [Pojęcia kanałów równorzędnych](peer-channel-concepts.md)
