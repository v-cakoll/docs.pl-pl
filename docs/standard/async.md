---
title: Przegląd Async
description: Dowiedz się, w jaki sposób programowanie asynchroniczne jest prostą techniką, która ułatwia obsługę blokowania operacji we/wy i współbieżnych na wielu rdzeniach.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: 2f76eb7d2b769b59809bec81aefacb7cec90a450
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106690"
---
# <a name="async-overview"></a>Przegląd Async

Tak długo aplikacje były szybsze po prostu przez zakup nowszego komputera lub serwera, a następnie ten trend został zatrzymany. W rzeczywistości została odwrócona. Pojawiły się telefony komórkowe z 1ghzą pojedyncze podstawowe wióry ARM i obciążenia serwera przenoszone do maszyn wirtualnych. Użytkownicy nadal chcą, aby właściciele interfejsu użytkownika i biznesowe chcą, aby serwery były skalowane wraz z ich działalnością biznesową. Przejście do urządzeń przenośnych i chmurowych oraz połączona z Internetem populacja > 3B użytkowników spowodowało powstanie nowego zestawu wzorców oprogramowania. 

- Aplikacje klienckie powinny być zawsze włączone, zawsze połączone i stale reagować na interakcję z użytkownikiem (na przykład Touch) ze wszystkimi klasyfikacjami w sklepie App Store.
- Usługi powinny obsłużyć wzrost ruchu przez bezpieczne skalowanie w górę i w dół. 

Programowanie asynchroniczne to kluczowa technika, która ułatwia obsługę blokowania operacji we/wy i współbieżnych na wielu rdzeniach. Platforma .NET oferuje możliwość, aby aplikacje i usługi były w stanie reagować i elastycznie korzystać z łatwych w użyciu modeli programów asynchronicznych na C#poziomie języka w językach F#, VB i.

## <a name="why-write-async-code"></a>Dlaczego warto pisać kod asynchroniczny?

Nowoczesne aplikacje wykorzystują wiele operacji we/wy plików i sieci. Interfejsy API we/wy tradycyjnie domyślnie blokują, co powoduje słabą obsługę użytkowników i wykorzystanie sprzętu, chyba że chcesz poznać i korzystać z niewielkich wzorców. Asynchroniczne interfejsy API oparte na zadaniach i asynchroniczny model programowania na poziomie języka odwracają ten model, dzięki czemu asynchroniczne wykonywanie jest domyślnie z kilkoma nowymi koncepcjami, które należy poznać.

Kod asynchroniczny ma następującą charakterystykę:

- Obsługuje więcej żądań serwera, uzyskując wątki do obsługi większej liczby żądań podczas oczekiwania na zwrócenie żądań we/wy.
- Umożliwia interfejsów użytkownika więcej odpowiedzi przez uzyskanie wątków do interakcji z interfejsem użytkownika podczas oczekiwania na żądania we/wy i przez przeniesienie długotrwałej pracy na inne rdzenie procesora.
- Wiele nowszych interfejsów API platformy .NET jest asynchronicznie.
- W programie .NET można łatwo pisać kod asynchroniczny.

## <a name="whats-next"></a>Co dalej?

Więcej informacji znajduje się w temacie [Async in głębokości](async-in-depth.md) .

Temat [wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) zawiera przegląd trzech asynchronicznych wzorców programowania obsługiwanych w programie .NET:  
  
- [Model programowania asynchronicznego (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) starszych  
  
- [Wzorzec asynchroniczny oparty na zdarzeniach (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) starszych  
  
- [Wzorzec asynchroniczny oparty na zadaniach (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (zalecane dla nowego programowania)  

Aby uzyskać więcej informacji na temat zalecanego modelu programowania opartego na zadaniach, zapoznaj się z tematem [programowanie asynchroniczne oparte na zadaniach](parallel-programming/task-based-asynchronous-programming.md) .
