---
title: Podsumowanie typu śledzenia
ms.date: 03/30/2017
ms.assetid: e639410b-d1d1-479c-b78e-a4701d4e4085
ms.openlocfilehash: 73777df2b58b14947c416ce409bcb42d439499ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403846"
---
# <a name="trace-type-summary"></a>Podsumowanie typu śledzenia
[Źródło poziomy](https://go.microsoft.com/fwlink/?LinkID=94943) definiuje różne poziomy śledzenia: krytyczny, błąd, ostrzeżenie, informacje i pełne informacje, jak również tak jak opisano w `ActivityTracing` flagi, które włącza/wyłącza dane wyjściowe śledzenia zdarzenia transferu granic i działania.  
  
 Możesz również przejrzeć [opcją TraceEventType](https://go.microsoft.com/fwlink/?LinkId=95169) dla typów danych śledzenia, które mogą być emitowane przez <xref:System.Diagnostics>.  
  
 W poniższej tabeli wymieniono najważniejsze.  
  
|Typ śledzenia|Opis|  
|----------------|-----------------|  
|Krytyczny|Błąd krytyczny lub aplikacji awarii.|  
|Błąd|Nieodwracalny błąd.|  
|Ostrzeżenie|Komunikat informacyjny.|  
|Informacje|Niekrytyczne problem.|  
|Pełny|Śledzenie debugowania.|  
|Uruchamianie|Uruchamianie jednostki logicznej przetwarzania.|  
|Wstrzymywanie|Zawieszenie jednostki logicznej przetwarzania.|  
|Wznawianie|Wznowienie przetwarzania jednostkę logiczną.|  
|Zatrzymywanie|Zatrzymywanie jednostki logicznej przetwarzania.|  
|Transfer|Zmiana tożsamości korelacji.|  
  
 Działanie jest zdefiniowany jako kombinacja powyższych typów śledzenia.  
  
 Oto wyrażeń regularnych, które definiuje działania idealnym rozwiązaniem w zakresie lokalnego (źródła)  
  
 `R = Start (Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop`  
  
 Oznacza to, że działanie musi spełniać następujące warunki.  
  
-   Musi zaczynać się i Zatrzymaj odpowiednio przez uruchamianie i zatrzymywanie danych śledzenia  
  
-   Musi on mieć śledzenia transferu, bezpośrednio poprzedzających śledzenia wstrzymania lub wznowienia  
  
-   Nie może mieć żadnych śladów między śledzenia wstrzymywanie i wznawianie, jeśli istnieją takie ślady  
  
-   Tak długo, jak poprzednie warunki zostały spełnione może mieć żadnych i jak najwięcej ślady krytyczne/błędu/ostrzeżenia/informacji/Verbose/Transfer  
  
 Oto wyrażeń regularnych, które definiuje działania idealnym rozwiązaniem w zakresie globalnym  
  
```  
R+   
```  
  
 przy użyciu języka R trwa wyrażenia regularnego dla działania w zakresie lokalnym. Przekłada się to,  
  
```  
[R+ = Start ( Critical | Error | Warning | Information | Verbose | Transfer | (Transfer Suspend Transfer Resume) )* Stop]+  
```
