---
title: Architektura WCF (Windows Communication Foundation)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1bc7383c5b93203b144c965f06fa7365c864de27
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="windows-communication-foundation-architecture"></a>Architektura WCF (Windows Communication Foundation)
Poniższa ilustracja przedstawia główne warstwy [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] architektury.  
  
## <a name="wcf-architecture"></a>Architektura WCF  
 ![Architektura WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Kontrakty wraz z opisami  
 Kontrakty definiowanie różnych aspektów dla wiadomości. Kontrakt danych opisano każdy parametr tworzącą każdej usługi można utworzyć lub korzystać z wiadomości. Parametry wiadomości są definiowane przez schematu XML definition language (XSD) dokumentów, włączanie każdy system, który obsługuje usługę XML do przetwarzania dokumentów. Kontraktu komunikatu definiuje części wiadomości przy użyciu protokołów SOAP i umożliwia dopasowanymi bardziej precyzyjną kontrolę nad części wiadomości, gdy współdziałanie wymaga takiego dokładności. Kontrakt usługi określa podpisów aktualnej metody usługi i jest rozpowszechniany jako interfejs w jednym z obsługiwanych języków programowania, takiego jak Visual Basic lub Visual C#.  
  
 Zasady i powiązania określać warunki wymagane do komunikacji z usługą.  Na przykład powiązanie (co najmniej) określić transportu (na przykład HTTP lub TCP) i kodowania. Zasady zawierają wymagania dotyczące zabezpieczeń i inne warunki, które muszą zostać spełnione, aby komunikować się z usługą.  
  
### <a name="service-runtime"></a>Usługi czasu wykonywania  
 Warstwa obsługi usługi zawiera zachowania, które występują tylko podczas bieżącej operacji usługi, to znaczy zachowania środowiska uruchomieniowego usługi. Ograniczanie formantów, ile komunikatów są przetwarzane, które można zmieniać Jeśli wstępnie ustawiony limit zawiera żądanie dla usługi. Zachowanie błąd Określa, jakie występuje, gdy występuje błąd wewnętrzny w usłudze, na przykład, kontrolując, jakie informacje są przekazywane do klienta. (Zbyt dużej ilości informacji zapewnić złośliwy użytkownik korzyści w instalowaniu atak.) Kontroluje zachowanie metadanych wyświetlania metadanych ma zostać udostępnione publicznie. Określa zachowanie wystąpienia może działać jak wiele wystąpień usługi (na przykład pojedyncza określa tylko jedno wystąpienie do przetwarzania wszystkich komunikatów). Zachowanie transakcji umożliwia wycofywanie Operacje transakcyjne, jeśli wystąpi błąd. Zachowania wysyłania jest kontrolę nad jak komunikat jest przetwarzany przez [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] infrastruktury.  
  
 Rozszerzalność umożliwia dostosowywanie procesów w czasie wykonywania. Na przykład komunikatów inspekcji jest możliwość kontroli części wiadomości i filtrowanie parametr umożliwia predefiniowanych operacje zależności od filtrów działającą w nagłówkach wiadomości.  
  
### <a name="messaging"></a>Obsługa wiadomości  
 Warstwa obsługi wiadomości składa się z *kanałów*. Kanał jest składnikiem, który przetwarza komunikat w sposób, na przykład przy uwierzytelniania wiadomości. Zbiór kanałów jest także znana jako *stosu kanału*. Kanały działają na wiadomości i nagłówki komunikatów. To jest inna niż warstwa środowiska uruchomieniowego usługi, która dotyczy przede wszystkim dotyczące przetwarzania zawartości treści wiadomości.  
  
 Istnieją dwa typy kanałów: transportu kanałów i kanały protokołów.  
  
 Kanały transportu odczytu i zapisu wiadomości z sieci (lub w pewnym momencie komunikacji na zewnątrz). Niektóre transportów używać kodera do konwersji wiadomości (które są reprezentowane jako XML Infosets) do i z reprezentacji strumień bajtów używanej przez sieć. Przykłady transportu HTTP nazwanych potoków, TCP i usługi MSMQ. Przykładem kodowania są zoptymalizowane binarnego i XML.  
  
 Kanały protokołów implementacji protokołów przetwarzania komunikatu, często przez odczyt lub zapis dodatkowych nagłówków wiadomości. Przykładami takich protokołów WS-Security i WS-niezawodności.  
  
 Warstwa obsługi wiadomości przedstawiono możliwe formaty i wzorce wymiany danych. Zabezpieczenia WS-Security jest implementacją specyfikacji WS-Security włączenie zabezpieczeń w warstwie wiadomości. Kanał WS-Reliable Messaging umożliwia gwarancji dostarczenia wiadomości. Kodery prezentowanie różnych kodowań, który może służyć do potrzeb wiadomości. Kanał HTTP określa, czy protokołu jest używany przez dostarczanie komunikatów. Kanału TCP podobnie Określa protokół TCP. Przepływ transakcji kanału reguluje wzorce wiadomości transakcyjnych. Kanał nazwanego potoku umożliwia komunikacji międzyprocesowej. Kanał MSMQ umożliwia współdziałanie z aplikacjami usługi MSMQ.  
  
### <a name="hosting-and-activation"></a>Hosting i aktywacji  
 W postaci końcowego usługi jest programem. Podobnie jak inne programy usługa musi zostać uruchomiony w pliku wykonywalnego. Jest to nazywane *hosta samodzielnego* usługi.  
  
 Można też usług *hostowanej*, lub uruchom w pliku wykonywalnym zarządzane przez firmę zewnętrzną, na przykład Windows Activation Service (WAS) lub programu IIS. Umożliwia WAS [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacji zostać aktywowana automatycznie podczas wdrażania na komputerze z systemem WAS. Usługi można też ręcznie uruchomić jako pliki wykonywalne (pliki .exe). Usługi można również uruchomić automatycznie jako usługa systemu Windows. Składniki modelu COM + mogą być również obsługiwane jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług.  
  
## <a name="see-also"></a>Zobacz też  
 [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
