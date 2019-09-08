---
title: Używanie poleceń do modyfikacji danych
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 34c73549f18cd4bebb8caf842b252828b7f0a185
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780562"
---
# <a name="using-commands-to-modify-data"></a>Używanie poleceń do modyfikacji danych
Za pomocą .NET Framework dostawcy danych można wykonać procedury składowane lub instrukcje języka definicji danych (na przykład CREATE TABLE i zmienić kolumnę), aby wykonać manipulowanie schematem bazy danych lub wykazu. Te polecenia nie zwracają wierszy jako zapytania, dlatego obiekt **Command** udostępnia **ExecuteNonQuery** do przetwarzania.  
  
 Oprócz używania **ExecuteNonQuery** do modyfikowania schematu, można również użyć tej metody do przetwarzania instrukcji SQL, które modyfikują dane, ale nie zwracają wierszy, takich jak INSERT, Update i DELETE.  
  
 Chociaż wiersze nie są zwracane przez metodę **ExecuteNonQuery** , parametry wejściowe i wyjściowe oraz zwracane wartości mogą być przekazywane i zwracane za pośrednictwem kolekcji **Parameters** obiektu **Command** .  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aktualizowanie danych w źródle danych](updating-data-in-a-data-source.md)  
 Opisuje sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.  
  
 [Wykonywanie operacji katalogu](performing-catalog-operations.md)  
 Opisuje sposób wykonywania poleceń, które modyfikują schemat bazy danych.  
  
## <a name="see-also"></a>Zobacz także

- [Pobieranie i modyfikowanie danych ADO.NET](retrieving-and-modifying-data.md)
- [Polecenia i parametry](commands-and-parameters.md)
- [Omówienie ADO.NET](ado-net-overview.md)
