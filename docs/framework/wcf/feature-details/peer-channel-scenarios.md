---
title: Scenariusze obejmujące kanał elementu równorzędnego
ms.date: 03/30/2017
ms.assetid: dae6e0f7-900c-45ee-8be9-3647698382fb
ms.openlocfilehash: 610668e5f3625c638fc1e814e0116df87970773b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147059"
---
# <a name="peer-channel-scenarios"></a>Scenariusze obejmujące kanał elementu równorzędnego
Interfejsy API kanał elementu równorzędnego obsługuje następujące scenariusze programowania.  
  
## <a name="publicationsubscription-messaging"></a>Komunikatów publikowania/subskrypcji  
 Firmy, którzy tworzą aplikacje publikacji/subskrypcji, (na przykład, giełdowych i wydawców nagłówki wiadomości sportowe wyniki, a następnie raportuje o pogodzie) umożliwia kanał elementu równorzędnego przy użyciu aplikacji bez serwera. Na przykład użytkownicy mogą uzyskać najnowsze wyniki sportowe, dołączając do wspólnego siatki (lub grupy klientów) i propagowanie dużą ilość danych gier — aktualne bez zwiększania obciążenia serwera. Dzięki temu dostawcy danych, aby dać wyższej jakości usługi bez zwiększania znaczne inwestycje w technologie oparte na serwerze.  
  
## <a name="collaboration"></a>Współpraca  
 Niezależni dostawcy oprogramowania (ISV) tworzyć aplikacje, które umożliwiają użytkownikom tworzenie grup ścisłej uczestnictwa w działaniach peer-to-peer. Na przykład może to obejmować zespołów pracujących nad projektami współpracy, udostępniania obrazów między znajomych, planowanie innej firmy i nie tylko. Tradycyjnie działania te obejmują zawsze serwerów; Kanał elementu równorzędnego zapewnia jednak sposób to zrobić w sposób bardziej efektywny kosztowo sposób po włączeniu scenariusze dostęp w trybie offline, które nie są równie łatwo, zaimplementowane w modelu tradycyjnym klienta z serwera.  
  
## <a name="distributed-processing-and-compute-clusters"></a>Przetwarzania rozproszonego i klastrach obliczeniowych  
 Klastry obliczeniowe i przetwarzania rozproszonego, są zwykle używane do obliczeń na dużą skalę, na przykład financial/pogoda modelowania i dekodowanie DNA ludzi. Zazwyczaj jest to realizowane przez serwerów osobno przypisuje zadania do wszystkich klientów uczestniczących w danym klastrze obliczeniowym. Te serwery mogą także mieć dodatkowe wymagania; Wszystkie zadania może na przykład, należy wykonać w ramach przez określony czas, wymaga więcej niż jedną maszynę dla każdego zadania. Ponadto jeśli dowolnego klienta, uruchamiając zadanie ulegnie awarii, inny klient musi mieć możliwość przejąć zadania i wykonywania pracy na nim. Podobnie więcej niż jeden może być konieczne uruchomienie tego samego zadania, aby zapewnić spójne wyniki. Mimo że serwery można uruchomić tego rodzaju koordynacji klienta, możesz utworzyć rozwiązanie peer-to-peer, gdzie klientom odbieranie zadania niezależnie określić wymagania dotyczące serwera na zadania i użyj siatki obliczeń, aby określić sposób wykonania tego zadania.  
  
## <a name="gaming"></a>Gry  
 Za pomocą kanału równorzędnego, deweloperzy aplikacji można tworzyć wersje bez serwera grą, gdzie przesyłane do gier przenosi i synchronizowane z innymi osobami przez mechanizm peer-to-peer, a nie za pomocą serwera centralnego. Dla małych niezależnych dostawców oprogramowania dzięki temu, Usuń kosztów operacyjnych związanych z wdrażania i obsługi centralne serwery oraz obsługi. Gry napisane przy użyciu architektury peer-to-peer mogą być odtwarzane w Internecie lub w sieci przewodowej lub bezprzewodowej sieci lokalnej. Działań dodatkowej gier, takich jak targach i rozmowy w grze mogą być tworzone przy użyciu sieci peer-to-peer.  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia kanałów równorzędnych](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md)
