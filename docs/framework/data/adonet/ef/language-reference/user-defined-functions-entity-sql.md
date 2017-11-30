---
title: "Funkcje zdefiniowane przez użytkownika (jednostka SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f9e6bbd-8e5a-43e1-809f-f8a61338e522
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b97834a500328f7853b8a361ec20d7ff06eda3d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="user-defined-functions-entity-sql"></a>Funkcje zdefiniowane przez użytkownika (jednostka SQL)
Jednostki SQL obsługuje wywoływanie funkcji zdefiniowanej przez użytkownika w zapytaniu. Można zdefiniować następujące wbudowane funkcje z zapytaniem (zobacz [porady: wywoływanie funkcji zdefiniowanych przez użytkownika](http://msdn.microsoft.com/en-us/ad131b86-8b4e-4747-8605-d4fc64fb9d02)) lub w ramach modelu koncepcyjnego (zobacz [jak: zdefiniować funkcje niestandardowe w modelu koncepcyjnym](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f)). Model koncepcyjny funkcje są zdefiniowane jako polecenie SQL jednostki w [DefiningExpression](http://msdn.microsoft.com/en-us/d3da8d8b-a048-47ee-8d81-0c2ea3acdd3e) elementu [funkcja](http://msdn.microsoft.com/en-us/dc3beca7-55cf-4977-8db0-5064cdbab134) elementu w modelu koncepcyjnym.  
  
 Jednostki SQL umożliwia zdefiniowanie funkcje w samo polecenie zapytania. [Funkcja](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) operator definiuje funkcji śródwierszowych. Można zdefiniować wiele funkcji za pomocą jednego polecenia, a te funkcje mogą mieć taką samą nazwę funkcji, tak długo, jak sygnatury funkcji są unikatowe. Aby uzyskać więcej informacji, zobacz [rozpoznawanie przeciążenia funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/function-overload-resolution-entity-sql.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)
