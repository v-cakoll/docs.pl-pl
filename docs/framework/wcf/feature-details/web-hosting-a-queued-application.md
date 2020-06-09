---
title: Sieć Web hostująca aplikację zakolejkowaną
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: 17c3d2167d3f98017c5f366ab0d700d9fb889f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600143"
---
# <a name="web-hosting-a-queued-application"></a>Sieć Web hostująca aplikację zakolejkowaną
Usługa aktywacji procesów systemu Windows (WAS) zarządza aktywacją i okresem istnienia procesów roboczych, które zawierają aplikacje obsługujące usługi Windows Communication Foundation (WCF). Proces WAS przetwarza model procesów usług IIS 6,0 dla serwera HTTP, usuwając zależność od protokołu HTTP. Dzięki temu usługi WCF mogą korzystać zarówno z protokołu HTTP, jak i protokołów innych niż HTTP, takich jak net. MSMQ i MSMQ. formatname, w środowisku hostingu obsługującym aktywację opartą na komunikatach i oferuje możliwość hostowania dużej liczby aplikacji na danym komputerze.  
  
 Obejmuje usługę aktywacji usługi kolejkowania komunikatów (MSMQ), która aktywuje aplikację w kolejce, gdy co najmniej jeden komunikat znajduje się w jednej z kolejek używanych przez aplikację. Usługa aktywacji usługi MSMQ to usługa NT, która domyślnie jest uruchamiana automatycznie.  
  
 Aby uzyskać więcej informacji o usłudze WAS i jej korzyściach, zobacz [hosting w usłudze aktywacji procesów systemu Windows](hosting-in-windows-process-activation-service.md). Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [Omówienie kolejek](queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Adresowanie kolejki w zostało  
 Aplikacje mają adresy Uniform Resource Identifier (URI). Adresy aplikacji mają dwie części: podstawowy prefiks identyfikatora URI i specyficzny dla aplikacji adres względny (ścieżka). Te dwie części zapewniają adres zewnętrzny dla aplikacji, gdy jest sprzężony razem. Podstawowy prefiks identyfikatora URI jest konstruowany z powiązania witryny i jest używany dla wszystkich aplikacji w lokacji, na przykład "net. MSMQ://localhost", "MSMQ. formatname://localhost", lub "net. TCP://localhost". Następnie adresy aplikacji są tworzone przez pobranie fragmentów ścieżek specyficznych dla aplikacji (takich jak "/applicationOne") i dołączenie ich do podstawowego prefiksu URI w celu uzyskania pełnego identyfikatora URI aplikacji, na przykład "net. MSMQ://localhost/applicationOne".  
  
 Usługa aktywacji usługi MSMQ używa identyfikatora URI aplikacji w celu dopasowania do kolejki, którą usługa aktywacji MSMQ musi monitorować w poszukiwaniu komunikatów. Po uruchomieniu usługa aktywacji usługi MSMQ wylicza wszystkie kolejki publiczne i prywatne na komputerze, który jest skonfigurowany do odbierania z i monitoruje je pod kątem komunikatów. Co 10 minut usługa aktywacji MSMQ odświeża listę kolejek do monitorowania. Po znalezieniu komunikatu w kolejce usługa aktywacji dopasowuje nazwę kolejki do najdłuższego zgodnego identyfikatora URI aplikacji dla powiązania net. MSMQ i aktywuje aplikację.  
  
> [!NOTE]
> Aktywowana aplikacja musi być zgodna z prefiksem nazwy kolejki (najdłuższym dopasowaniem).  
  
 Na przykład nazwa kolejki to: msmqWebHost/orderProcessing/Service. svc. Jeśli aplikacja 1 ma katalog wirtualny/msmqWebHost/orderProcessing z usługą. svc w tym obszarze, a aplikacja 2 ma katalog wirtualny/msmqWebHost z orderProcessing. svc w tym obszarze, aktywowano aplikację 1. Jeśli aplikacja 1 zostanie usunięta, zostanie uaktywniona aplikacja 2.  
  
> [!NOTE]
> Po utworzeniu kolejki wszystkie wysyłane do niej wiadomości nie uaktywniają aplikacji do momentu odświeżenia listy kolejek przez usługę aktywacji usługi MSMQ, czyli maksymalnie 10 minut od momentu utworzenia kolejki. Ponowne uruchomienie usługi aktywacji spowoduje odświeżenie listy kolejek.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Wpływ kolejek prywatnych i publicznych na adresowanie  
 Usługa aktywacji usługi MSMQ nie rozróżnia monitorowania kolejek prywatnych i publicznych. W związku z tym nie można mieć kolejek publicznych i prywatnych o tej samej nazwie. W takim przypadku aplikacja hostowana w sieci Web może uzyskać aktywację z jednej z kolejek.  
  
### <a name="queue-configuration-for-activation"></a>Konfiguracja kolejki na potrzeby aktywacji  
 Usługa aktywacji usługi MSMQ działa jako usługa sieciowa. Jest to usługa, która monitoruje kolejki w celu aktywowania aplikacji. Aby można było aktywować aplikacje z kolejki, kolejka musi zapewnić dostęp usługi sieciowej do wglądu w komunikaty na liście kontroli dostępu (ACL).  
  
### <a name="poison-messaging"></a>Trująca obsługa komunikatów  
 Obsługa skażonych komunikatów w programie WCF jest obsługiwana przez kanał, który nie tylko wykrywa, że komunikat jest trujący, ale wybiera dyspozycję opartą na konfiguracji użytkownika. W związku z tym w kolejce znajduje się jeden komunikat. Aplikacja hostowana w sieci Web przerywa pracę po kolejnych godzinach, a komunikat jest przenoszony do kolejki ponawiania prób. W punkcie podyktowanym opóźnieniem cyklu ponawiania komunikat jest przenoszony z kolejki ponownych prób do kolejki głównej, aby spróbować ponownie. Jednak wymaga to aktywności kanału znajdującego się w kolejce. Jeśli aplikacja jest odtwarzana przez program, wówczas komunikat pozostaje w kolejce ponownych prób do momentu, aż inny komunikat zostanie umieszczony w kolejce głównej w celu aktywowania aplikacji znajdującej się w kolejce. Obejście w tym przypadku polega na przeniesieniu komunikatu ręcznie z kolejki ponownych prób z powrotem do kolejki głównej w celu ponownego aktywowania aplikacji.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Przeciwkolejka i przeciwsystemowe zastrzeżenie  
 Nie można aktywować aplikacji hostowanej na podstawie komunikatów w kolejce systemowej, takich jak Kolejka utraconych wiadomości w całej systemie, lub podkolejki, takie jak podkolejki trujące. Jest to ograniczenie dla tej wersji produktu.  
  
## <a name="see-also"></a>Zobacz też

- [Obsługa komunikatów zanieczyszczonych](poison-message-handling.md)
- [Punkty końcowe usługi i adresowanie kolejki](service-endpoints-and-queue-addressing.md)
