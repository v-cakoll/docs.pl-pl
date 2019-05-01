---
title: Przetwarzanie transakcji
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: dc032746b265a3e781898beb823be0d1bcf1abea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793669"
---
# <a name="transaction-processing"></a>Przetwarzanie transakcji
Kupując książki z księgarni online, wymieniać się pieniądze (w formie kredytu) książki. Jeśli Twój kredytowej jest dobra, serii powiązanych operacji zapewnia, że Pobierz książkę o i księgarni pobiera pieniądze. Jednak w przypadku niepowodzenia podczas wymiany jednej operacji w serii całego exchange nie powiodło się. Użytkownik nie może korzystać książki i księgarni nie otrzymać pieniądze.  
  
 Technologia odpowiedzialnych za udostępnianie wymiany zrównoważona i przewidywalne jest wywoływana przetwarzania transakcji. Transakcje upewnij się, że zasoby ukierunkowane na dane nie trwale aktualizacji, o ile wszystkie operacje w ramach transakcji jednostki ukończone pomyślnie. Łącząc zestaw powiązanych operacji do jednostki, która całkowicie zakończy się powodzeniem lub całkowicie nie powiedzie się, można uprościć odzyskiwania błąd i zapewnić bardziej niezawodny aplikacji.  
  
 Systemy przetwarzania transakcji składają się z sprzęt komputerowy i programy obsługi aplikacji zorientowany, który wykonuje rutynowej transakcji niezbędne do prowadzenia działalności biznesowej. Przykładami systemami zarządzania wpisu zamówienia sprzedaży, rezerwacji linii lotniczych, płac, rekordy pracowników, produkcji i wysyłania.  
  
 Ta sekcja zawiera ogólne informacje na temat przetwarzania transakcji i szczegółowe informacje na temat przygotowania transakcyjnych aplikacji i menedżerów zasobów za pomocą programu Microsoft .NET Framework.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące transakcji](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 Wprowadzono podstawowe transakcji przetwarzania terminy i pojęcia.  
  
 [Funkcje oferowane przez bibliotekę System.Transactions](../../../../docs/framework/data/transactions/features-provided-by-system-transactions.md)  
 W tym artykule omówiono, jak używać funkcji w System.Transactions do zapisania transakcyjnych aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Transactions>  
 Udostępnia klasy, które pozwalają na uczestniczenie w transakcjach kodu. Klasy obsługuje transakcji z wieloma uczestnikami rozproszonej, wieloma powiadomieniami o fazach oraz trwałych rejestracjach.
