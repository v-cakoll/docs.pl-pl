---
title: Przetwarzanie transakcji
description: Przejrzyj przetwarzanie transakcji w programie .NET. Transakcje zapewniają, że zasoby zorientowane na dane nie są trwale aktualizowane, chyba że wszystkie operacje zakończą się pomyślnie.
ms.date: 03/30/2017
ms.assetid: effdc8e6-accf-41eb-98a5-431603ba218b
ms.openlocfilehash: 30d69c55d968865cc80b8633bdbc2442f6d216de
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141916"
---
# <a name="transaction-processing"></a>Przetwarzanie transakcji
Kupując książki z księgarni online, wymieniać się pieniądze (w formie kredytu) książki. Jeśli Twój kredytowej jest dobra, serii powiązanych operacji zapewnia, że Pobierz książkę o i księgarni pobiera pieniądze. Jednak w przypadku niepowodzenia podczas wymiany jednej operacji w serii całego exchange nie powiodło się. Użytkownik nie może korzystać książki i księgarni nie otrzymać pieniądze.  
  
 Technologia odpowiedzialnych za udostępnianie wymiany zrównoważona i przewidywalne jest wywoływana przetwarzania transakcji. Transakcje zapewniają, że zasoby zorientowane na dane nie są trwale aktualizowane, chyba że wszystkie operacje w ramach jednostki transakcyjnej zakończą się pomyślnie. Łącząc zestaw powiązanych operacji w jednostkę, która całkowicie kończy się powodzeniem lub całkowicie niepowodzeniem, można uprościć odzyskiwanie błędów i zwiększyć niezawodność aplikacji.  
  
 Systemy przetwarzania transakcji składają się ze sprzętu komputerowego i oprogramowania hostującym aplikację zorientowaną na transakcje, która wykonuje rutynowe transakcje niezbędne do prowadzenia działalności. Przykłady obejmują systemy zarządzające wpisami zamówienia sprzedaży, rezerwacjami lotniczymi, płacami, rekordami pracowników, produkcją i wysyłką.  
  
 Ta sekcja zawiera ogólne informacje o przetwarzaniu transakcji oraz informacje dotyczące sposobu pisania transakcyjnych aplikacji i menedżerów zasobów przy użyciu platformy Microsoft .NET.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Podstawowe informacje dotyczące transakcji](transaction-fundamentals.md)  
 Wprowadzono podstawowe transakcji przetwarzania terminy i pojęcia.  
  
 [Funkcje oferowane przez bibliotekę System.Transactions](features-provided-by-system-transactions.md)  
 W tym artykule omówiono sposób używania funkcji w ramach programu System. Transactions do pisania własnej aplikacji transakcyjnej.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.Transactions>  
 Udostępnia klasy, które pozwalają na uczestniczenie w transakcjach kodu. Klasy obsługują transakcje z wieloma uczestnikami rozproszonymi, wieloma powiadomieniami fazowymi i trwałymi rejestracjami.
