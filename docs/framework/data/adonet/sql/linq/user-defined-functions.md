---
title: Funkcje zdefiniowane przez użytkownika
ms.date: 03/30/2017
ms.assetid: 3304c9b2-5c7a-4a95-9d45-4f260dcb606e
ms.openlocfilehash: 40697da4fe678668f8f7ecda86abebf40da7b973
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792304"
---
# <a name="user-defined-functions"></a>Funkcje zdefiniowane przez użytkownika
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]używa metod w modelu obiektu do reprezentowania funkcji zdefiniowanych przez użytkownika. Należy wyznaczyć metody jako funkcje, <xref:System.Data.Linq.Mapping.FunctionAttribute> stosując atrybut i, w razie potrzeby <xref:System.Data.Linq.Mapping.ParameterAttribute> , atrybut. Aby uzyskać więcej informacji, zobacz [model obiektów LINQ to SQL](the-linq-to-sql-object-model.md).  
  
 Aby uniknąć <xref:System.InvalidOperationException>, funkcje zdefiniowane przez użytkownika w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] muszą mieć jedną z następujących form:  
  
- Funkcja opakowana jako wywołanie metody ma poprawne atrybuty mapowania. Aby uzyskać więcej informacji, zobacz [Mapowanie oparte na atrybutach](attribute-based-mapping.md).  
  
- Statyczna metoda SQL specyficzna [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]dla.  
  
- Funkcja obsługiwana przez metodę .NET Framework.  
  
 W tematach w tej sekcji pokazano, jak tworzyć i wywoływać te metody w aplikacji, jeśli piszesz kod samodzielnie. Deweloperzy korzystający z programu Visual Studio zwykle używają Object Relational Designer do mapowania funkcji zdefiniowanych przez użytkownika.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami skalarnymi](how-to-use-scalar-valued-user-defined-functions.md)  
 Opisuje sposób implementowania funkcji zwracającej wartości skalarne.  
  
 [Instrukcje: Korzystanie z funkcji zdefiniowanych przez użytkownika z wartościami przechowywanymi w tabeli](how-to-use-table-valued-user-defined-functions.md)  
 Opisuje sposób implementowania funkcji zwracającej wartości tabeli.  
  
 [Instrukcje: Wywołaj wbudowane funkcje zdefiniowane przez użytkownika](how-to-call-user-defined-functions-inline.md)  
 Opisuje sposób wykonywania wywołań wbudowanych do funkcji i różnic w wykonywaniu, gdy wywołanie jest wykonywane w tekście.
