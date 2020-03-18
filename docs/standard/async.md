---
title: Przegląd asynchronicznego
description: Dowiedz się, jak programowanie asynchroniczne jest kluczową techniką, która ułatwia obsługę blokowania we/wy i równoczesnych operacji na wielu rdzeniach.
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 1e38e9d9-8284-46ee-a15f-199adc4f26f4
ms.openlocfilehash: d649bc3a92d3bb834b3bc4f7d3c1bcb0f9417375
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159731"
---
# <a name="async-overview"></a>Przegląd asynchronicznego

Nie tak dawno temu aplikacje stały się szybsze po prostu kupując nowszy komputer lub serwer, a następnie ten trend się zatrzymał. W rzeczywistości, to odwrócił. Telefony komórkowe pojawiły się z 1ghz jednordzeniowych chipów ARM i obciążeń serwera przeniesione na maszyny wirtualne. Użytkownicy nadal chcą elastycznego interfejsu użytkownika, a właściciele firm chcą serwerów skalowanych wraz z ich działalnością. Przejście na urządzenia mobilne i chmurę oraz populację >użytkowników 3B przyłączoną do Internetu zaowocowało nowym zestawem wzorców oprogramowania.

- Oczekuje się, że aplikacje klienckie będą zawsze włączone, zawsze połączone i stale reagują na interakcję z użytkownikiem (na przykład dotyk) z wysokimi ocenami w sklepach z aplikacjami!
- Oczekuje się, że usługi obsługi skoków ruchu przez bezpiecznie skalowanie w górę iw dół.

Programowanie asynchroniczne jest kluczową techniką, która ułatwia obsługę blokowania we/wy i równoczesnych operacji na wielu rdzeniach. .NET zapewnia aplikacjom i usługom możliwość responsywnego i elastycznego korzystania z łatwych w użyciu modeli programowania asynchronicznego na poziomie języka w językach C#, Visual Basic i F#.

## <a name="why-write-async-code"></a>Dlaczego warto napisać kod Async?

Nowoczesne aplikacje szeroko wykorzystują we/wy plików i sieci. Interfejsy API we/wy tradycyjnie blokują domyślnie, co powoduje słabe doświadczenia użytkowników i wykorzystanie sprzętu, chyba że chcesz uczyć się i używać trudnych wzorców. Asynchroniczne interfejsy API oparte na zadaniach i model programowania asynchronicznego na poziomie języka odwracają ten model, sprawiając, że wykonanie asynchroniczne jest domyślne przy kilku nowych pojęciach do nauczenia się.

Kod asynchronicznego ma następujące właściwości:

- Obsługuje więcej żądań serwera, yielding wątków do obsługi większej liczby żądań podczas oczekiwania na żądania we/wy do zwrócenia.
- Umożliwia interfejsowi użytkownika, aby być bardziej elastyczne przez plonowanie wątków do interakcji interfejsu użytkownika podczas oczekiwania na żądania we/wy i przez przejście długotrwałej pracy do innych rdzeni procesora CPU.
- Wiele nowszych interfejsów API .NET jest asynchronicznych.
- Łatwo jest napisać kod asynchronicznego w .NET!

## <a name="whats-next"></a>Co dalej?

Aby uzyskać więcej informacji, zobacz temat [Async w głębi.](async-in-depth.md)

Temat [Wzorce programowania asynchronicznego](asynchronous-programming-patterns/index.md) zawiera omówienie trzech wzorców programowania asynchronicznego obsługiwanych w programie .NET:  
  
- [Asynchroniczny model programowania (APM)](asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (starsze)  
  
- [Wzorzec asynchroniczny oparty na zdarzeniach (EAP)](asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (starszy)  
  
- [Wzorzec asynchroniczny (TAP)](asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) oparty na zadaniach (zalecany do nowego rozwoju)  

Aby uzyskać więcej informacji na temat zalecanego modelu programowania opartego na zadaniach, zobacz temat [programowania asynchronicznego opartego na zadaniach.](parallel-programming/task-based-asynchronous-programming.md)
