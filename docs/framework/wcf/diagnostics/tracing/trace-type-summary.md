---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 8f54f71ef63338708a29fac5557c7c7e8f257f58
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856011"
---
# <a name="trace-type-summary"></a>Podsumowanie typu śledzenia
[Poziomy źródła](https://go.microsoft.com/fwlink/?LinkID=94943) definiują różne poziomy śledzenia: Krytyczne, błąd, ostrzeżenie, informacje i pełne, a także zawiera opis `ActivityTracing` flagi, która przełącza dane wyjściowe z granicy śledzenia i zdarzeń transferu aktywności.  
  
 Można również przejrzeć [TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) dla typów śladów, które mogą być emitowane z <xref:System.Diagnostics>.  
  
 W poniższej tabeli przedstawiono najważniejsze elementy.  
  
|Typ śledzenia|Opis|  
|----------------|-----------------|  
|Krytyczny|Błąd krytyczny lub awaria aplikacji.|  
|Błąd|Odwracalny błąd.|  
|Ostrzeżenie|Komunikat informacyjny.|  
|Informacje|Problem niekrytyczny.|  
|Pełny|Śledzenie debugowania.|  
|Uruchamianie|Rozpoczynanie logicznej jednostki przetwarzania.|  
|Wstrzymywanie|Zawieszenie logicznej jednostki przetwarzania.|  
|Wznawianie|Wznawianie jednostki logicznej przetwarzania.|  
|Zatrzymywanie|Zatrzymywanie logicznej jednostki przetwarzania.|  
|Transfer|Zmiana tożsamości korelacji.|  
  
 Działanie jest zdefiniowane jako kombinacja powyższych typów śledzenia.  
  
 Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie lokalnym (śledzenie źródła),  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Oznacza to, że działanie musi spełniać następujące warunki.  
  
- Musi on być odpowiednio uruchamiany i zatrzymany przez uruchamianie i zatrzymywanie śledzenia  
  
- Musi mieć ślad transferu bezpośrednio poprzedzający śledzenie wstrzymania lub wznowienia  
  
- Nie może mieć żadnych śladów między śladami zawieszenia i wznowienia, jeśli istnieją takie ślady  
  
- Może to być dowolny i wiele ze śladów krytyczne/błąd/ostrzeżenie/informacja/pełny/transfer, o ile zostały spełnione poprzednie warunki  
  
 Poniżej znajduje się wyrażenie regularne, które definiuje idealne działanie w zakresie globalnym,  
  
`R+`  
  
 za pomocą języka R jest wyrażeniem regularnym dla działania w zakresie lokalnym. Spowoduje to przetłumaczenie na,  
  
`[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+`
