---
title: Funkcje (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 52b3d776-5acc-4f69-b614-5a43ce56ef9f
ms.openlocfilehash: ec94a0f16fb3b836297f6675cc938a711816555b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250905"
---
# <a name="functions-entity-sql"></a>Funkcje (Entity SQL)
Entity SQL obsługuje funkcje zdefiniowane przez użytkownika, funkcje kanoniczne i funkcje specyficzne dla dostawcy. Funkcje zdefiniowane przez użytkownika są określone w modelu koncepcyjnym lub wbudowane w zapytaniu. Aby uzyskać więcej informacji, zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md).  
  
 Funkcje kanoniczne są wstępnie zdefiniowane w Entity Framework i powinny być obsługiwane przez dostawców danych. Entity SQL polecenia zakończą się niepowodzeniem, jeśli użytkownik wywoła funkcję, która nie jest obsługiwana przez dostawcę. W związku z tym funkcje kanoniczne są zwykle zalecane w stosunku do funkcji specyficznych dla magazynu, które znajdują się w przestrzeni nazw specyficznej dla dostawcy. Aby uzyskać więcej informacji, zobacz [funkcje kanoniczne](canonical-functions.md).  
  
 Dostawca zarządzany przez klienta programu Microsoft SQL Server udostępnia zestaw funkcji specyficznych dla dostawcy. Aby uzyskać więcej informacji, zobacz temat [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Funkcje zdefiniowane przez użytkownika](user-defined-functions-entity-sql.md)  
  
 [Rozpoznanie przeciążenia funkcji](function-overload-resolution-entity-sql.md)  
  
 [Funkcje agregujące](../aggregate-functions-sqlclient-for-entity-framework.md)  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie jednostki SQL](entity-sql-overview.md)
