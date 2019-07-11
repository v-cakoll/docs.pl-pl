---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 54faca27e3f70283144f902e531e2a08e45bae3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742711"
---
# <a name="user-defined-functions"></a>Funkcje zdefiniowane przez użytkownika
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używa metody w modelu obiektu, który reprezentuje funkcje zdefiniowane przez użytkownika. Wyznacz metody jako funkcje, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeśli to konieczne, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [LINQ to SQL Model obiektów](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Aby uniknąć <xref:System.InvalidOperationException>zdefiniowany przez użytkownika funkcje w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi należeć do jednej z następujących form:  
  
- Opakowana funkcja jako wywołania metody o atrybuty mapowania poprawne. Aby uzyskać więcej informacji, zobacz [mapowanie oparte na atrybutach](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
- Statyczna metoda SQL specyficzne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
- Funkcja obsługiwane przez metody .NET Framework.  
  
 Tematy w tej sekcji przedstawiają sposób utworzenia i wywoływanie tych metod w aplikacji, jeśli możesz napisać kod. Deweloperzy korzystający z programu Visual Studio będzie zazwyczaj Użyj Object Relational Designer, aby zamapować funkcje zdefiniowane przez użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Użyj funkcji skalarnej zdefiniowanej przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Opisuje sposób implementacji funkcji, która zwraca wartości skalarnych.  
  
 [Instrukcje: Używanie wartościami przechowywanymi w tabeli funkcji zdefiniowanych przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Opisuje sposób implementacji funkcji, która zwraca wartości w tabeli.  
  
 [Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 W tym artykule opisano sposób wprowadzania tekście wywołania funkcji i różnice w wykonywania, gdy dochodzi do wywołania wbudowanego.
