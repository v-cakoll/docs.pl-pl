---
title: Typy danych podstawowych
ms.date: 03/30/2017
ms.assetid: eca2c472-9548-4800-bd31-5d8d9f11752b
ms.openlocfilehash: 6e1e48b3d390cf7c8ec81735b9637f706ad3a0ad
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306261"
---
# <a name="basic-data-types"></a>Typy danych podstawowych
Ponieważ zapytania LINQ to SQL przełożyć na instrukcji języka Transact-SQL przed są one wykonywane w programie Microsoft SQL Server. LINQ do SQL obsługuje wiele wbudowanych funkcji wykonującej programu SQL Server dla podstawowych typów danych.  
  
## <a name="casting"></a>Rzutowanie  
 Rzutowania jawnego lub niejawnego są włączone ze źródła typu CLR do elementu docelowego typu CLR w przypadku podobne prawidłowa konwersja w programie SQL Server. Aby uzyskać więcej informacji na temat środowiska CLR rzutowania zobacz [funkcja CType](~/docs/visual-basic/language-reference/functions/ctype-function.md) (Visual Basic) i [operatory badania typu i konwersji](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md). Po konwersji rzutowania zmienić zachowanie operacje wykonywane na wyrażeniu CLR, aby dopasować zachowanie inne wyrażenia CLR, naturalny mapowane na typ docelowy. Rzutowania są również tłumaczenia w kontekście mapowania dziedziczenia. Obiekty mogą być rzutowane na dokładniejszą podtypy jednostki, tak, aby ich dane specyficzne dla podtypu są dostępne.  
  
## <a name="equality-operators"></a>Operatory równości  
 LINQ do SQL obsługuje następujące operatory równości na podstawowych typów danych w LINQ do kwerendy SQL:  
  
- Równe i Operator nierówności: Operatory równości i nierówności są obsługiwane w przypadku numeryczne, <xref:System.Boolean>, <xref:System.DateTime>, i <xref:System.TimeSpan> typów. Aby uzyskać więcej informacji na temat operatorów Visual Basic `=` i `<>`, zobacz [operatory porównania](~/docs/visual-basic/language-reference/operators/comparison-operators.md). Aby uzyskać więcej informacji na temat C# operatory porównania `==` i `!=`, zobacz [Operatory równości](~/docs/csharp/language-reference/operators/equality-operators.md).
  
- Is — operator: `IS` Operator ma obsługiwanych tłumaczeń, gdy jest używane mapowanie dziedziczenia. Może służyć zamiast bezpośrednio testować kolumna dyskryminatora można określić, czy obiekt jest określonego typu i jest tłumaczona na sprawdzenie kolumna dyskryminatora. Aby uzyskać więcej informacji na temat języka Visual Basic i C# jest operatorów, zobacz [operatora Is](~/docs/visual-basic/language-reference/operators/is-operator.md) i [jest](~/docs/csharp/language-reference/operators/type-testing-and-conversion-operators.md#is-operator).  
  
## <a name="see-also"></a>Zobacz także

- [Mapowania typów środowiska SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Typy danych i funkcje](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
