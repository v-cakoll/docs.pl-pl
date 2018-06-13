---
title: Aby zmodyfikować danych za pomocą poleceń
ms.date: 03/30/2017
ms.assetid: f4160389-b9ff-4b74-b655-437c76dcd586
ms.openlocfilehash: 9f13eb2079df959281a44086edf84c34f3c63a14
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365047"
---
# <a name="using-commands-to-modify-data"></a>Aby zmodyfikować danych za pomocą poleceń
Przy użyciu dostawcy danych .NET Framework, można wykonać procedur składowanych lub instrukcje języka definicji danych (na przykład CREATE TABLE i ALTER COLUMN) podczas manipulowania schematu bazy danych lub katalogu. Tych poleceń nie zwracają wierszy, jak zapytania, więc **polecenia** zawiera obiekt **ExecuteNonQuery** do ich przetworzenia.  
  
 Oprócz używania **ExecuteNonQuery** do modyfikowania schematu, umożliwia także tę metodę, aby proces instrukcji SQL, które modyfikują dane, ale nie zwracanie wszystkich wierszy, takie jak INSERT, UPDATE i usunąć.  
  
 Mimo że wierszy nie są zwracane przez **ExecuteNonQuery** przekazany i zwracane przez metody wejściowe i wyjściowe parametrów i zwracanych wartości **parametry** Kolekcja **polecenia**  obiektu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aktualizowanie danych w źródle danych](../../../../docs/framework/data/adonet/updating-data-in-a-data-source.md)  
 Opisuje sposób wykonywania poleceń lub procedur składowanych, które modyfikują dane w bazie danych.  
  
 [Wykonywanie operacji katalogu](../../../../docs/framework/data/adonet/performing-catalog-operations.md)  
 Opisuje sposób wykonywania poleceń, które modyfikują schemat bazy danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
