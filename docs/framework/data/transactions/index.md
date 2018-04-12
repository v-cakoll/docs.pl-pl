---
title: Przetwarzanie transakcji
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6c66e982715d0f7f97e7a4faa92c2de57f3b1471
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-processing"></a>Przetwarzanie transakcji
Kupując książki z księgarni online, wymieniać się pieniądze (w formie kredytu) książki. Jeśli Twój kredytowej jest dobra, serii powiązanych operacji zapewnia, że Pobierz książkę o i księgarni pobiera pieniądze. Jednak w przypadku niepowodzenia podczas wymiany jednej operacji w serii całego exchange nie powiodło się. Użytkownik nie może korzystać książki i księgarni nie otrzymać pieniądze.  
  
 Technologia odpowiedzialnych za udostępnianie wymiany zrównoważona i przewidywalne jest wywoływana przetwarzania transakcji. Transakcje upewnij się, że dotyczący danych zasobów nie są trwałe aktualizowane chyba, że wszystkie operacje w jednostce transakcyjne pomyślnie ukończona. Łącząc zestawu powiązanych operacji do jednostki, która całkowicie zakończy się pomyślnie lub całkowicie nie powiedzie się, można uprościć odzyskiwania po błędzie i wprowadzić aplikacji bardziej niezawodne.  
  
 Systemy przetwarzania transakcji składają się z komputera sprzętu i oprogramowania hosting aplikacji zorientowany transakcyjnie, który wykonuje transakcji procedury niezbędne do prowadzenia działalności. Przykładami systemów, które zarządzać wpis zamówienia, rezerwacji linii lotniczych, Lista płac i pracownikach produkcyjny i wysyłania.  
  
 Ta sekcja zawiera ogólne informacje na temat przetwarzania transakcji i określone informacje na temat sposobu pisania aplikacji transakcyjnych i menedżerowie zasobów przy użyciu programu Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 Wprowadzono podstawowe transakcji przetwarzania terminy i pojęcia.  
  
 [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 W tym artykule omówiono, jak używać funkcji w System.Transactions zapisu transakcyjnych aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Transactions>  
 Udostępnia klasy, które pozwalają na uczestniczenie w transakcjach kodu. Klasy obsługi transakcji z wielu uczestników rozproszonych, wieloma powiadomieniami i trwałych rejestracji.
