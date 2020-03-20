---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8ed6dceb19caa52f928f285064c60337e3f15a87
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78674841"
---
# <a name="trace-type-summary"></a>Podsumowanie typu śledzenia
[Poziomy źródła](xref:System.Diagnostics.SourceLevels) definiuje różne poziomy śledzenia: Krytyczne, Błąd, Ostrzeżenie, Informacje i Pełne, a `ActivityTracing` także zawiera opis flagi, która przełącza dane wyjściowe śledzenia granic i zdarzeń transferu działania.  
  
 Można również <xref:System.Diagnostics.TraceEventType> przejrzeć typy śladów, które <xref:System.Diagnostics>mogą być emitowane z .  
  
 W poniższej tabeli wymieniono najważniejsze z nich.  
  
|Typ śledzenia|Opis|  
|----------------|-----------------|  
|Krytyczny|Błąd krytyczny lub awaria aplikacji.|  
|Błąd|Błąd do odzyskania.|  
|Ostrzeżenie|Wiadomość informacyjna.|  
|Informacje|Problem niekrytyczny.|  
|Pełny|Debugowanie śledzenia.|  
|Rozpoczęcie|Rozpoczęcie logicznej jednostki przetwarzania.|  
|Wstrzymanie|Zawieszenie logicznej jednostki przetwarzania.|  
|Resume|Wznowienie logicznej jednostki przetwarzania.|  
|Stop|Zatrzymywanie logicznej jednostki przetwarzania.|  
|Transfer|Zmiana tożsamości korelacji.|  
  
 Działanie jest zdefiniowane jako kombinacja typów śledzenia powyżej.  
  
 Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie lokalnym (źródło śledzenia),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Oznacza to, że działanie musi spełniać następujące warunki.  
  
- Musi rozpocząć i zatrzymać odpowiednio przez ślady start i stop  
  
- Musi mieć transfer śledzenia bezpośrednio poprzedzających wstrzymanie lub wznowienie śledzenia  
  
- Nie może mieć żadnych śladów między wstrzymywają i wznawiaj ślady, jeśli takie ślady istnieją  
  
- Może mieć dowolną i dowolną liczbę krytycznych/błąd/ostrzeżenie/informacje/pełne/transferowe ślady, o ile zaobserwowano poprzednie warunki  
  
 Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie globalnym,  
  
`R+`  
  
 z R jest wyrażeniem regularnym dla działania w zakresie lokalnym. Przekłada się to na,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
