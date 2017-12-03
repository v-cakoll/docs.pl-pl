---
title: "Sieć Web hostująca aplikację zakolejkowaną"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7a539fa-e442-4c08-a7f1-17b7f5a03e88
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79b35fc63fa34bf6de462bad3c18d857215cbfa1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="web-hosting-a-queued-application"></a>Sieć Web hostująca aplikację zakolejkowaną
Usługa aktywacji procesów systemu Windows (WAS) zarządza aktywacji i okresem istnienia procesów roboczych, które zawierają aplikacji obsługujących [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług. Stanowi uogólnienie modelu procesów WAS [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu dla serwera HTTP przez usunięcie zależności od protokołu HTTP. Dzięki temu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług jednoczesne używanie protokołów HTTP i protokołów innych niż HTTP, na przykład net.msmq i msmq.formatname w środowisku macierzystym, który obsługuje aktywacji opartej na komunikat i oferuje możliwość obsługi dużej liczby aplikacji na danym komputerze.  
  
 ZOSTAŁ obejmują usługę aktywacji usługi kolejkowania komunikatów (MSMQ), który uaktywnia umieszczonych w kolejce aplikacji, gdy jeden lub więcej komunikatów są umieszczane w jednym z kolejek używany przez aplikację. Usługa aktywacji usługi MSMQ jest usługi NT, który jest automatycznie uruchamiane domyślnie.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Usługa WAS i korzyści, zobacz [Hosting w usłudze aktywacji procesów systemu Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Usługa MSMQ, zobacz [omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
  
## <a name="queue-addressing-in-was"></a>Kolejka adresowania usługi WAS  
 ZOSTAŁ, że aplikacje mają adresy jednolity identyfikator zasobów (URI). Adresy aplikacji ma dwie części: specyficzne dla aplikacji, względny adres (ścieżka) i podstawowa Prefiks URI. Te dwie części Podaj adres zewnętrzny aplikację, jeśli połączone. Podstawowy Prefiks URI jest tworzony z powiązania witryny i jest używany dla wszystkich aplikacji w witrynie, na przykład "net.msmq://localhost", "msmq.formatname://localhost" lub "NET.TCP://localhost". Następnie zbudowanych aplikacji adresów wykonując fragmenty ścieżki specyficzne dla aplikacji (takich jak "/ applicationOne") i dodanie ich do podstawowego identyfikatora URI prefiksu na pełny identyfikator URI aplikacji, na przykład "net.msmq://localhost/applicationOne".  
  
 Usługa MSMQ activation używa identyfikator URI aplikacji w celu dopasowania kolejki usługi MSMQ activation service należy monitorować dla wiadomości. Po uruchomieniu usługi MSMQ activation service wylicza wszystkich kolejek publicznych i prywatnych na komputerze jest skonfigurowana do odbierania z, a monitoruje je dla wiadomości. Co 10 minut, usługi MSMQ activation service Odświeża listę kolejek do monitorowania. Po znalezieniu komunikatu w kolejce z usługą aktywacji jest zgodna z nazwą kolejki, do aplikacji najdłuższy zgodny identyfikator URI dla powiązania net.msmq i aktywuje aplikację.  
  
> [!NOTE]
>  Trwa aktywowanie aplikacji muszą być zgodne (najdłuższe dopasowanie) prefiks nazwy kolejki.  
  
 Na przykład nazwa kolejki jest: msmqWebHost/orderProcessing/service.svc. Jeśli 1 aplikacja nie ma /msmqWebHost/orderProcessing katalogu wirtualnego z service.svc w nim i 2 aplikacji jest /msmqWebHost katalogu wirtualnego z orderProcessing.svc w nim, 1 aplikacja została aktywowana. Usunięcie aplikacji 1, 2 aplikacji jest aktywowane.  
  
> [!NOTE]
>  Podczas tworzenia kolejki komunikaty wysyłane do niego nie aktywować aplikacji, dopóki usługi MSMQ activation service spowoduje odświeżenie listy kolejki, która jest maksymalnie 10 minut od czasu utworzenia kolejki. Ponowne uruchamianie usługi aktywacji odświeża na liście kolejki.  
  
### <a name="the-effect-of-private-and-public-queues-on-addressing"></a>Efekt kolejek prywatnych i publicznych w rozwiązaniu  
 Usługa MSMQ activation nie rozróżnia monitorowania kolejki prywatnej i publicznej. W efekcie nie może mieć kolejek publicznych i prywatnych o takiej samej nazwie. Jeśli to zrobisz, aplikacji sieci Web hostowanych może pobrać aktywować odczytu z jednej z kolejki.  
  
### <a name="queue-configuration-for-activation"></a>Konfiguracja kolejki dla aktywacji  
 Usługa MSMQ activation działa jako usługa sieciowa. To usługa, która monitoruje kolejki, aby aktywować aplikacje. Na jej aktywowania aplikacji z kolejki należy podać kolejki usług sieci dostęp do wglądu dla wiadomości w listy kontroli dostępu (ACL).  
  
### <a name="poison-messaging"></a>Zanieczyszczonych komunikatów  
 Trująca wiadomość została obsługa w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jest obsługiwany przez kanał nie tylko wykryje, że wiadomość jest intoksykowane, ale wybiera dyspozycji, na podstawie konfiguracji użytkownika. W związku z tym jest pojedynczą wiadomość w kolejce. Aplikacja oparta na sieci Web przerywa razy w kolejnych i wiadomość zostanie przeniesiona do kolejki ponawiania. W punkcie ustawieniem Opóźnienie ponownych prób cyklu wiadomość zostanie przeniesiona z kolejki ponawiania do kolejki głównej aby spróbować ponownie. Ale wymaga to zwrócony jako aktywne. Jeśli aplikacja jest ponownego przetworzenia przez WAS, następnie komunikat pozostaje w kolejka ponownych prób do momentu kolejną wiadomość dociera do kolejki głównej do aktywowania aplikacji w kolejce. W takim przypadku obejście jest powrót komunikat ręcznie z kolejka ponownych prób do kolejki głównej do ponownego aktywowania aplikacji.  
  
### <a name="subqueue-and-system-queue-caveat"></a>Podkolejki i zastrzeżenie systemu kolejki:  
 Nie można uaktywnić aplikacji usługi hostowanej WAS oparte na wiadomości w kolejce systemu, takich jak kolejki utraconych wiadomości systemowe lub podrzędnej kolejki, takie jak skażone kolejki podrzędne. Jest to ograniczenie dla tej wersji produktu.  
  
## <a name="see-also"></a>Zobacz też  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 [Punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
