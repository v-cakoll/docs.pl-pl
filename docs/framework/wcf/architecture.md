---
title: Architektura WCF (Windows Communication Foundation)
description: Dowiedz się więcej na temat głównych warstw architektury Windows Communication Foundation, takich jak kontrakty, środowisko uruchomieniowe usług, obsługa komunikatów i aktywacja &.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: a07d5c4be2e36b8123e39a0a04d841797e34212b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245573"
---
# <a name="windows-communication-foundation-architecture"></a>Architektura WCF (Windows Communication Foundation)
Na poniższej ilustracji przedstawiono główne warstwy architektury Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Architektura WCF  
 ![Architektura programu WCF](./media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Kontrakty i opisy  
 Kontrakty definiują różne aspekty systemu komunikatów. W umowie dotyczącej danych opisano każdy parametr, który obejmuje każdy komunikat, który usługa może utworzyć lub wykorzystać. Parametry wiadomości są definiowane przez dokumenty języka definicji schematu XML (XSD), co umożliwia dowolnemu systemowi zrozumienie kodu XML do przetwarzania dokumentów. Kontrakt wiadomości definiuje konkretne części komunikatów korzystające z protokołów SOAP i umożliwia dokładniejszą kontrolę nad częściami komunikatu, gdy współdziałanie wymaga takiej precyzji. Kontrakt usługi określa rzeczywiste podpisy metody usługi i jest dystrybuowany jako interfejs w jednym z obsługiwanych języków programowania, takich jak Visual Basic lub Visual C#.  
  
 Zasady i powiązania określają warunki wymagane do komunikacji z usługą.  Na przykład powiązanie musi (co najmniej) określać używany transport (na przykład HTTP lub TCP) i kodowanie. Zasady obejmują wymagania dotyczące zabezpieczeń i inne warunki, które muszą zostać spełnione, aby komunikować się z usługą.  
  
### <a name="service-runtime"></a>Środowisko uruchomieniowe usługi  
 Warstwa środowiska uruchomieniowego usługi zawiera zachowania, które są wykonywane tylko podczas rzeczywistej pracy usługi, czyli zachowania środowiska uruchomieniowego usługi. Ograniczanie przepływności kontroluje liczbę przetwarzanych komunikatów, co może być zróżnicowane w przypadku, gdy zapotrzebowanie na usługę osiągnie ustawiony limit. Zachowanie błędu określa, co się dzieje w przypadku wystąpienia błędu wewnętrznego w usłudze, na przykład przez kontrolowanie, jakie informacje są przekazywane Klientowi. (Zbyt wiele informacji może dać złośliwemu użytkownikowi korzyść w instalowaniu ataku). Zachowanie metadanych reguluje sposób i informacje o tym, czy metadane są udostępniane na świecie zewnętrznym. Zachowanie wystąpienia określa, ile wystąpień usługi może być uruchomionych (na przykład pojedyncze określa tylko jedno wystąpienie do przetwarzania wszystkich komunikatów). Zachowanie transakcji umożliwia wycofanie operacji transakcyjnych w przypadku wystąpienia błędu. Zachowanie wysyłania to Kontrola sposobu przetwarzania komunikatów przez infrastrukturę WCF.  
  
 Rozszerzalność umożliwia dostosowanie procesów środowiska uruchomieniowego. Na przykład Inspekcja komunikatów jest funkcją do sprawdzania części komunikatu, a filtrowanie parametrów umożliwia wykonywanie wstępnie ustawionych akcji na podstawie filtrów działających na nagłówkach komunikatów.  
  
### <a name="messaging"></a>Obsługa komunikatów  
 Warstwa komunikatów składa się z *kanałów*. Kanał to składnik, który przetwarza komunikat w jakiś sposób, na przykład przez uwierzytelnienie komunikatu. Zestaw kanałów jest również nazywany *stosem kanału*. Kanały działają na komunikatach i nagłówkach komunikatów. Różni się to od warstwy środowiska uruchomieniowego usługi, która jest przede wszystkim zaangażowana w przetwarzanie zawartości treści komunikatów.  
  
 Istnieją dwa typy kanałów: kanały transportu i kanały protokołu.  
  
 Kanały transportu odczytują i zapisują wiadomości z sieci (lub innego punktu komunikacji z zewnętrznym światem). Niektóre transporty wykorzystują koder do konwertowania komunikatów (które są reprezentowane jako XML Infosets) do i z reprezentacji strumienia bajtów używanych przez sieć. Przykładami transportami są HTTP, nazwane potoki, TCP i MSMQ. Przykłady kodowań są XML i zoptymalizowane jako dane binarne.  
  
 Kanały protokołu implementują protokoły przetwarzania komunikatów, często poprzez odczytywanie lub zapisywanie dodatkowych nagłówków w komunikacie. Przykładami takich protokołów są protokoły WS-Security i WS-niezawodność.  
  
 Warstwa obsługi wiadomości ilustruje możliwe formaty i wzorce wymiany danych. WS-Security to implementacja specyfikacji WS-Security, która umożliwia zabezpieczenia w warstwie komunikatów. Kanał obsługi komunikatów w usłudze WS-niezawodny umożliwia gwarancję dostarczania wiadomości. Kodery składają się z różnych kodowań, które mogą być używane do zaspokajania potrzeb wiadomości. Kanał HTTP określa, że protokół transportu hipertekstowego jest używany do dostarczania komunikatów. Kanałem TCP w podobny sposób określa protokół TCP. Kanał przepływu transakcji zarządza wzorcami komunikatów transakcyjnych. Kanał nazwanego potoku umożliwia komunikację międzyprocesową. Kanał usługi MSMQ umożliwia współdziałanie z aplikacjami usługi MSMQ.  
  
### <a name="hosting-and-activation"></a>Hosting i aktywacja  
 W swojej końcowej formie usługa jest programem. Podobnie jak w przypadku innych programów, usługa musi być uruchomiona w pliku wykonywalnym. Jest to tzw. Usługa *samodzielna* .  
  
 Usługi mogą być również *hostowane*lub uruchamiane w pliku wykonywalnym zarządzanym przez agenta zewnętrznego, takiego jak usługi IIS lub usługa aktywacji systemu Windows (was). Program umożliwia automatyczne Aktywowanie aplikacji WCF po wdrożeniu na komputerze z systemem. Usługi można również uruchamiać ręcznie jako pliki wykonywalne (. exe). Usługa może być również uruchamiana automatycznie jako usługa systemu Windows. Składniki modelu COM+ mogą być również hostowane jako usługi WCF.  
  
## <a name="see-also"></a>Zobacz też

- [Co to jest program Windows Communication Foundation](whats-wcf.md)
- [Podstawowe pojęcia programu Windows Communication Foundation](fundamental-concepts.md)
