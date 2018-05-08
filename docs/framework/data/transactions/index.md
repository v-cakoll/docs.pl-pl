---
title: Przetwarzanie transakcji
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: dc032746b265a3e781898beb823be0d1bcf1abea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
