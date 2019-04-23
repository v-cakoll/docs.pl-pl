---
title: Funkcje zdefiniowane przez użytkownika (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
ms.openlocfilehash: 4922e7fada676a6c26042236ccdb6315d6d455ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104627"
---
# <a name="user-defined-functions-entity-sql"></a>Funkcje zdefiniowane przez użytkownika (jednostka SQL)
Jednostka SQL obsługuje wywoływanie funkcji zdefiniowanej przez użytkownika w zapytaniu. Można zdefiniować tych wbudowanych funkcji z zapytaniem (zobacz [jak: Wywołaj funkcję User-defined](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))) lub jako część modelu koncepcyjnego (zobacz [jak: Definiowanie funkcji niestandardowych w modelu koncepcyjnym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456812(v=vs.100))). Model koncepcyjny funkcji są definiowane jako polecenia SQL jednostki w [DefiningExpression](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#definingexpression-element-csdl) elementu [funkcja](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#function-element-csdl) elementu w modelu koncepcyjnym.  
  
 Jednostka SQL umożliwia zdefiniowanie funkcji w niej samo polecenie zapytania. [Funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator definiuje wbudowane funkcje. Można zdefiniować wiele funkcji za pomocą jednego polecenia, a te funkcje mogą mieć taką samą nazwę funkcji, tak długo, jak sygnatury funkcji są unikatowe. Aby uzyskać więcej informacji, zobacz [rozdzielczość przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
