---
title: Typy danych podstawowych
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 977f99f129d591898953ed24ad5acdaa3ae9a88a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365994"
---
# <a name="basic-data-types"></a>Typy danych podstawowych
Ponieważ LINQ do SQL zapytań przełożyć na języka Transact-SQL przed są wykonywane w programie Microsoft SQL Server. LINQ do SQL obsługuje wiele wbudowanych funkcji nieistniejącego dla typów podstawowych danych programu SQL Server.  
  
## <a name="casting"></a>Rzutowanie  
 Rzutowania jawnych ani niejawnych są włączone ze źródła typu CLR do docelowego typu CLR w przypadku podobne prawidłowa konwersja w programie SQL Server. Aby uzyskać więcej informacji na temat rzutowanie CLR, zobacz [CType — funkcja](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) i [jako](~/docs/csharp/language-reference/keywords/as.md). Po przeprowadzeniu konwersji rzutowania zmianę zachowania operacji wykonywanych na wyrażeniu CLR, aby dopasować zachowanie inne wyrażenia CLR, które naturalnie zamapować na typ docelowy. Rzutowania są również możliwa w kontekście mapowania dziedziczenia. Obiekty mogą być rzutowane na bardziej szczegółowe podtypów jednostki tak, aby ich dane specyficzne dla podtypu są dostępne.  
  
## <a name="equality-operators"></a>Operatory równości  
 LINQ do SQL obsługuje następujące operatory równości w typach podstawowych danych wewnątrz LINQ kwerendy SQL:  
  
-   Taki sam i Operator nierówności: operatory równości i nierówności są obsługiwane w przypadku liczbowe <xref:System.Boolean>, <xref:System.DateTime>, i <xref:System.TimeSpan> typów. Aby uzyskać więcej informacji na temat operatorów Visual Basic `=` i `<>`, zobacz [operatory porównania](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Aby uzyskać więcej informacji na temat operatory porównania języka C# `==` i `!=`, zobacz [== — Operator](~/docs/csharp/language-reference/operators/equality-comparison-operator.md) i [! = — Operator](~/docs/csharp/language-reference/operators/not-equal-operator.md)odpowiednio  
  
-   Is — operator: `IS` operator ma tłumaczenia obsługiwanych w przypadku mapowania dziedziczenia jest używany. Może służyć zamiast bezpośrednio testowania dyskryminatora, aby określić, czy obiekt jest określonego typu i jest translacja do wyboru w kolumnie rozróżniacza. Aby uzyskać więcej informacji na temat operatorów Visual Basic i C# jest zobacz [operatora Is](~/docs/visual-basic/language-reference/operators/is-operator.md) i [jest](~/docs/csharp/language-reference/keywords/is.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
