---
title: "Funkcje zdefiniowane przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: ad269ddaa7d7c3995672398a24de06f57f7122e2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="user-defined-functions"></a>Funkcje zdefiniowane przez użytkownika
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]używa metody w modelu obiektu do reprezentowania funkcje zdefiniowane przez użytkownika. Możesz określić metod jako funkcje, stosując <xref:System.Data.Linq.Mapping.FunctionAttribute> atrybutu i, jeżeli jest to wymagane, <xref:System.Data.Linq.Mapping.ParameterAttribute> atrybutu. Aby uzyskać więcej informacji, zobacz [LINQ w modelu obiektu SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).  
  
 Aby uniknąć <xref:System.InvalidOperationException>, zdefiniowane przez użytkownika funkcji [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi być w jednym z następujących formatów:  
  
-   Opakowana funkcja jako wywołanie metody o atrybuty poprawne mapowania. Aby uzyskać więcej informacji, zobacz [mapowania na podstawie atrybutów](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).  
  
-   Statycznej metody SQL specyficzne dla [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
-   Obsługiwane przez funkcję [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] metody.  
  
 Tematy w tej sekcji przedstawiają sposób tworzą i wywołania tych metod w aplikacji, podczas pisania kodu. Deweloperzy przy użyciu [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] zwykle użyje [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do mapowania funkcje zdefiniowane przez użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Używanie funkcji skalarnej zdefiniowanej przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-scalar-valued-user-defined-functions.md)  
 Zawiera opis sposobu implementacji funkcji, która zwraca wartości skalarnych.  
  
 [Instrukcje: Używanie funkcji tabelarycznej zdefiniowanej przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-table-valued-user-defined-functions.md)  
 Zawiera opis sposobu implementacji funkcji zwracającej tabelę wartości.  
  
 [Instrukcje: Wywoływanie wbudowanych funkcji zdefiniowanych przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/how-to-call-user-defined-functions-inline.md)  
 Zawiera opis sposobu wprowadzania wbudowanego wywołania funkcji i różnice podczas wykonywania, gdy połączenie jest nawiązywane w tekście.
