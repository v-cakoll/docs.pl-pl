---
title: Architektura WCF (Windows Communication Foundation)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: f152ac48c2897259d07222fafd33d17d5287a870
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745389"
---
# <a name="windows-communication-foundation-architecture"></a>Architektura WCF (Windows Communication Foundation)
Poniższa ilustracja przedstawia główne warstwy architektury usługi Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Architektura programu WCF  
 ![Architektura WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Kontrakty wraz z opisami  
 Kontrakty definiują różne aspekty systemu wiadomości. Kontrakt danych w tym artykule opisano każdy parametr, który sprawia, że każdy komunikat, że usługa może tworzyć lub korzystać. Parametry komunikatu są definiowane przez dokumentów języka (XSD) definicji schematu XML, włączenie dowolnego systemu, który rozumie XML do przetworzenia w dokumentach. Kontrakt komunikatów definiuje części szczegółowy komunikat o błędzie przy użyciu protokołów SOAP i umożliwia bardziej szczegółowej kontroli nad części wiadomości, w przypadku, gdy współdziałanie zapotrzebowania na takie dokładności. Kontrakt usługi określa rzeczywiste sygnatury usługi i jest rozpowszechniany jako interfejs w jeden z obsługiwanych języków programowania, takich jak Visual Basic lub Visual C#.  
  
 Zasady i powiązania określać warunki wymagane do komunikacji z usługą.  Na przykład powiązanie (co najmniej) podaj transportu (na przykład HTTP lub TCP) i kodowania. Zasady zawierają wymagania dotyczące zabezpieczeń i innych warunków, które muszą zostać spełnione do komunikowania się z usługą.  
  
### <a name="service-runtime"></a>Środowisko wykonawcze usług  
 Warstwa środowiska uruchomieniowego usługi zawiera zachowania, które występują tylko podczas bieżącej operacji usługę, oznacza to, zachowania środowiska uruchomieniowego usługi. Ograniczanie pozwala kontrolować, ile komunikatów są przetwarzane, którego można zmieniać Jeśli wzrośnie zapotrzebowanie na usługi, wstępnie ustawionego limitu. To zachowanie błąd Określa, co występuje, gdy występuje błąd wewnętrzny w usłudze, na przykład, kontrolując, jakie informacje są przekazywane do klienta. (Zbyt wiele informacji można nadać złośliwemu użytkownikowi korzyści w instalowaniu ataku.) Kontroluje zachowanie metadanych jak oraz tego, czy metadane staje się dostępny dla świata zewnętrznego. Zachowanie wystąpienia określa, ile wystąpień usługi można uruchamiać (na przykład wzorzec singleton określa tylko jedno wystąpienie, aby przetworzyć wszystkie komunikaty). Zachowanie transakcji umożliwia wycofywania operacji transakcyjnych, jeśli wystąpi awaria. Zachowanie wysyłania jest kontroli jak komunikat jest przetwarzany przez infrastrukturę usługi WCF.  
  
 Rozszerzalność umożliwia dostosowywanie procesów w czasie wykonywania. Na przykład funkcji, aby sprawdzić części wiadomości jest inspekcja wiadomości i filtrowanie parametr umożliwia predefiniowanych akcji nastąpi w oparciu o filtry działający w nagłówkach wiadomości.  
  
### <a name="messaging"></a>Obsługa wiadomości  
 Warstwa obsługi komunikatów składa się z *kanały*. Kanał jest składnikiem, który przetwarza wiadomości w jakiś sposób, na przykład, korzystając z uwierzytelniania wiadomości. Zbiór kanałów jest także znana jako *stosu kanału*. Kanały działają na wiadomości i nagłówków wiadomości. To różni się od warstwy środowiska uruchomieniowego usługi, która jest głównie zajmującym się przetwarzaniem zawartość treści wiadomości.  
  
 Istnieją dwa typy usługi kanały: transportu kanałów i kanały protokołów.  
  
 Kanały transportu odczytu i zapisu wiadomości z sieci (lub w pewnym momencie komunikacji ze światem zewnętrznym). Niektóre transportów umożliwia koder konwertować wiadomości, (które są reprezentowane jako XML Infosets) do i z reprezentacji strumień bajtów używanej przez sieć. Przykłady transportu HTTP, nazwanych potoków, TCP i usługi MSMQ. Przykłady kodowań XML i zoptymalizowanego pliku binarnego.  
  
 Kanały protokołów implementacji protokołów przetwarzania komunikatów, często przez odczyt lub zapis dodatkowe nagłówki do wiadomości. Przykładami takich protokołów WS-Security i usługi WS-niezawodności.  
  
 Warstwa obsługi komunikatów ilustruje możliwych formatów i wzorce wymiany danych. WS-Security jest implementacją specyfikacji WS-Security włączenie zabezpieczeń w warstwie wiadomości. Kanał WS-Reliable Messaging umożliwia gwarancji dostarczanie komunikatów. Kodery przedstawiają różne kodowania, który może służyć do potrzeb wiadomości. Kanał HTTP określa, że protokołu służy do dostarczania wiadomości. Kanału TCP określa podobnie protokołu TCP. Przepływ transakcji kanału decyduje wzorców wiadomości transakcyjne. Kanał nazwanego potoku umożliwia komunikacji międzyprocesowej. Kanał usługi MSMQ umożliwia współdziałanie z aplikacjami usługi MSMQ.  
  
### <a name="hosting-and-activation"></a>Hostowanie i aktywacja  
 W postaci końcowego usługi jest program. Podobnie jak inne programy usługa musi zostać uruchomiony w pliku wykonywalnego. Jest to nazywane *może być samodzielnie hostowane* usługi.  
  
 Można też usług *hostowane*, lub w pliku wykonywalnym, zarządzane przez agenta zewnętrznych, takich jak usługi IIS lub Windows Activation Service (WAS). BYŁA WCF umożliwia aplikacjom aktywowana automatycznie podczas wdrażania na komputerze z systemem. Usługi można również ręcznie uruchomić jako pliki wykonywalne (pliki .exe). Usługi można również uruchomić automatycznie jako usługę Windows. Składniki modelu COM +, może też być hostowana w odróżnieniu od usług WCF.  
  
## <a name="see-also"></a>Zobacz także
- [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Podstawowe pojęcia programu Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
