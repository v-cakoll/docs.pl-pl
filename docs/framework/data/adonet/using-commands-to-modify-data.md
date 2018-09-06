---
title: Używanie poleceń do modyfikacji danych
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 6388eecb2e96970f47383b61985d672bd0419a1e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864147"
---
# <a name="using-commands-to-modify-data"></a>Używanie poleceń do modyfikacji danych
Za pomocą dostawcy danych .NET Framework, można wykonać procedury składowanej lub instrukcje języka definicji danych (na przykład polecenia CREATE TABLE i ALTER COLUMN) wykonywać operacje na schemat bazy danych lub katalogu. Te polecenia nie zwracają wiersze, tak jak zapytania, więc **polecenia** obiektu **ExecuteNonQuery** do ich przetworzenia.  
  
 Oprócz używania **ExecuteNonQuery** do modyfikacji schematu, umożliwia także tę metodę w celu przetwarzania instrukcji SQL modyfikujących dane, ale nie zwraca wiersze, takich jak INSERT, UPDATE i usunąć.  
  
 Mimo że wierszy nie są zwracane przez **ExecuteNonQuery** przekazane i zwracane przez metody wejściowe i wyjściowe parametrów i zwracanych wartości **parametry** zbiór **polecenia**  obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aktualizowanie danych w źródle danych](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 W tym artykule opisano sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.  
  
 [Wykonywanie operacji katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 W tym artykule opisano sposób wykonywania poleceń, które modyfikują schemat bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
