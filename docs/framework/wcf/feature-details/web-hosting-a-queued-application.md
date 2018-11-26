---
title: Sieć Web hostująca aplikację zakolejkowaną
ms.date: 03/30/2017
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
ms.openlocfilehash: aa50b3b66230930f9553d6f0238b0a5f9178f7a5
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297416"
---
# <a name="web-hosting-a-queued-application"></a>Sieć Web hostująca aplikację zakolejkowaną
Windows Process Activation Service (WAS) zarządza aktywacji i okresem istnienia procesów roboczych, które zawierają aplikacji zawierających usługi Windows Communication Foundation (WCF). Stanowi uogólnienie modelu procesów WAS [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesów dla serwera HTTP przez usunięcie zależności od protokołu HTTP. Dzięki temu usługi WCF do użycia protokołów HTTP i protokołów innych niż HTTP, na przykład net.msmq i msmq.formatname w środowisku macierzystym, który obsługuje aktywację w oparciu o wiadomości i oferuje możliwość hostowania wielu aplikacji na danym komputerze.  
  
 ZOSTAŁ obejmuje usługę aktywacji usługi kolejkowania komunikatów (MSMQ), który aktywuje umieszczonych w kolejce aplikacji, gdy jeden lub więcej komunikatów są umieszczane w jednej z kolejek używanych przez aplikację. Aktywacja usługi MSMQ jest usługą NT, która zostanie automatycznie uruchomiony domyślnie.  
  
 Aby dowiedzieć się więcej o WAS i jego korzyści, zobacz [Hosting w usłudze aktywacji procesów Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). Aby uzyskać więcej informacji na temat usługi MSMQ, zobacz [omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md).
  
## <a name="queue-addressing-in-was"></a>Kolejka adresowania w WAS  
 BYŁO, że aplikacje mają adresy identyfikator (URI). Adresy aplikacji mają dwie części: podstawowy prefiks identyfikatora URI i adres specyficzne dla aplikacji, względna (ścieżka). Te dwie części Obejmij zewnętrzny adres aplikację, jeśli połączone razem. Podstawowy prefiks identyfikatora URI jest tworzony z powiązania witryny i jest używany dla wszystkich aplikacji w ramach lokacji, na przykład "net.msmq://localhost", "msmq.formatname://localhost" lub "NET.TCP://localhost". Adresy aplikacji następnie są tworzone, wykonując fragmenty ścieżki specyficzne dla aplikacji (takich jak "/ applicationOne") i dołączanie ich do podstawowego identyfikatora URI jako prefiksu przyjeździe do biura pełny identyfikator URI aplikacji, na przykład "net.msmq://localhost/applicationOne".  
  
 Aktywacja usługi MSMQ używa identyfikator URI aplikacji w celu dopasowania usługę Aktywacja usługi MSMQ należy monitorować komunikaty kolejki. Po uruchomieniu usługi Aktywacja usługi MSMQ wylicza wszystkich kolejek publicznych i prywatnych na komputerze jest skonfigurowany do otrzymywać i monitoruje ich dla wiadomości. Co 10 minut, usługę Aktywacja usługi MSMQ Odświeża listę kolejek do monitorowania. Po znalezieniu komunikatu w kolejce usługi aktywacji jest zgodna z nazwą kolejki do identyfikator URI aplikacji najdłuższy zgodny dla powiązania net.msmq i aktywuje aplikację.  
  
> [!NOTE]
>  Aplikacja aktywowanego muszą być zgodne (najdłuższe) prefiks nazwy kolejki.  
  
 Na przykład nazwa kolejki jest: msmqWebHost/orderProcessing/service.svc. Jeśli aplikacja 1 ma /msmqWebHost/orderProcessing katalogu wirtualnego, za pomocą service.svc pod nim, a 2 aplikacji ma /msmqWebHost katalogu wirtualnego, za pomocą orderProcessing.svc pod nim, jest aktywowana aplikacja 1. Jeśli aplikacja 1 zostanie usunięty, 2 aplikacja została aktywowana.  
  
> [!NOTE]
>  Podczas tworzenia kolejki komunikaty wysyłane do niej nie zostanie aktywowany aplikacji, dopóki usługa aktywacji usługi MSMQ odświeża Lista kolejek, który jest co najwyżej 10 minut od chwili, gdy kolejka została utworzona. Ponowne uruchamianie usługi aktywacji odświeża na liście kolejki.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Wpływ kolejek prywatnych i publicznych na adresowanie  
 Aktywacja usługi MSMQ nie rozróżnia monitorowania kolejki prywatnej i publicznej. W efekcie nie mogą mieć kolejek publicznych i prywatnych o takiej samej nazwie. Jeśli to zrobisz, aplikacji hostowanej w sieci Web może aktywować odczytu przy użyciu dowolnego z kolejki.  
  
### <a name="queue-configuration-for-activation"></a>Konfiguracja kolejki w celu aktywacji  
 Aktywacja usługi MSMQ działa jako usługa sieciowa. To usługa, która monitoruje kolejki jednak aktywować aplikacje. Na zakończenie jego aktywowania aplikacji z kolejki kolejki należy podać dostępu Usługa sieciowa do wglądu dla wiadomości w listy kontroli dostępu (ACL).  
  
### <a name="poison-messaging"></a>Obsługa zanieczyszczonych komunikatów  
 Zarządzanie skażonymi komunikatami, obsługa w programie WCF jest obsługiwany przez kanał, który nie tylko wykrywa, czy komunikat jest intoksykowane, ale wybiera dyspozycji, na podstawie konfiguracji użytkownika. W rezultacie ma jedną wiadomość w kolejce. Aplikacja sieci Web hostowanych przerywa kolejnych godzin i wiadomość zostanie przeniesiona do kolejki ponownych prób. W momencie z ustawieniem opóźnienie cyklu ponawiania wiadomość zostanie przeniesiona z kolejki ponownych prób do kolejki głównej aby spróbować ponownie. Jednak wymaga to zwrócony jako aktywny. Jeśli aplikacja jest poddawane recyklingowi, WAS, następnie wiadomości pozostaje w kolejce ponownych prób do momentu inny komunikat dociera do kolejki głównej, aby aktywować aplikację zakolejkowaną. W takim przypadku obejście jest powrót komunikat ręcznie z kolejki ponownych prób do kolejki głównej, aby ponownie aktywować aplikację.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Kolejki podrzędnej i zastrzeżenie System kolejki:  
 Aplikacja usługi hostowanej WAS nie można aktywować oparte na komunikatów w kolejce systemu, takich jak kolejki utraconych wiadomości całego systemu lub kolejki podrzędnej, takie jak zarządzanie skażonymi kolejki podrzędnej. Jest to ograniczenie dla tej wersji produktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
