---
title: Funkcje zdefiniowane przez użytkownika (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 03146d895c6ca780692228937fafcf25b24902aa
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275382"
---
# <a name="user-defined-functions-entity-sql"></a>Funkcje zdefiniowane przez użytkownika (jednostka SQL)
Jednostka SQL obsługuje wywoływanie funkcji zdefiniowanej przez użytkownika w zapytaniu. Można zdefiniować tych wbudowanych funkcji z zapytaniem (zobacz [jak: Wywołaj funkcję User-defined](https://msdn.microsoft.com/library/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) lub jako część modelu koncepcyjnego (zobacz [jak: definiowania funkcji niestandardowych w modelu koncepcyjnym](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Model koncepcyjny funkcji są definiowane jako polecenia SQL jednostki w [DefiningExpression](https://msdn.microsoft.com/library/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elementu [funkcja](https://msdn.microsoft.com/library/dc3beca7-55cf-4977-8db0-5064cdbab134) elementu w modelu koncepcyjnym.  
  
 Jednostka SQL umożliwia zdefiniowanie funkcji w niej samo polecenie zapytania. [Funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator definiuje wbudowane funkcje. Można zdefiniować wiele funkcji za pomocą jednego polecenia, a te funkcje mogą mieć taką samą nazwę funkcji, tak długo, jak sygnatury funkcji są unikatowe. Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
