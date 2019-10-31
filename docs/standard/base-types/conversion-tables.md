---
title: Tabele konwersji typów w programie .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
ms.openlocfilehash: aa1ef8397338af949bd147fd3252b2d9ecaf53ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103889"
---
# <a name="type-conversion-tables-in-net"></a>Tabele konwersji typów w programie .NET
Konwersja rozszerzająca występuje, gdy wartość jednego typu jest konwertowana na inny typ o równym lub większym rozmiarze. Konwersja zawęża występuje, gdy wartość jednego typu jest konwertowana na wartość innego typu o mniejszym rozmiarze. Tabele w tym temacie ilustrują zachowania w obu typach konwersji.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli opisano konwersje rozszerzające, które mogą być wykonywane bez utraty informacji.  
  
|Typ|Mogą być konwertowane bez utraty danych|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double><xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Niektóre rozszerzone konwersje na <xref:System.Single> lub <xref:System.Double> mogą spowodować utratę precyzji. W poniższej tabeli opisano konwersje rozszerzające, które czasami powodują utratę informacji.  
  
|Typ|Można przekonwertować na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Konwersje zawężające  
 Zawężanie konwersji na <xref:System.Single> lub <xref:System.Double> może spowodować utratę informacji. Jeśli typ docelowy nie może prawidłowo przedstawić wielkości źródła, typ wyniku jest ustawiony na stałą `PositiveInfinity` lub `NegativeInfinity`. `PositiveInfinity` wyniki dzielenia liczby dodatniej przez zero i są zwracane, gdy wartość <xref:System.Single> lub <xref:System.Double> przekracza wartość pola `MaxValue`. `NegativeInfinity` wyniki dzielenia ujemnej liczby przez zero i są zwracane, gdy wartość <xref:System.Single> lub <xref:System.Double> przypada poniżej wartości pola `MinValue`. Konwersja z <xref:System.Double> do <xref:System.Single> może skutkować `PositiveInfinity` lub `NegativeInfinity`.  
  
 Zawężanie konwersji może również spowodować utratę informacji dla innych typów danych. Jednak <xref:System.OverflowException> jest generowany, jeśli wartość konwertowanego typu wykracza poza zakres określony przez pola `MaxValue` i `MinValue` typu docelowego, a konwersja jest sprawdzana przez środowisko uruchomieniowe, aby upewnić się, że wartość typu docelowego nie przekracza jego `MaxValue` lub `MinValue`. Konwersje wykonywane z klasą <xref:System.Convert?displayProperty=nameWithType> są zawsze sprawdzane w ten sposób.  
  
 W poniższej tabeli wymieniono konwersje, które generują <xref:System.OverflowException> przy użyciu <xref:System.Convert?displayProperty=nameWithType> lub dowolnej konwersji zaznaczonej, jeśli wartość konwertowanego typu jest poza zdefiniowanym zakresem typu.  
  
|Typ|Można przekonwertować na|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32><xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert?displayProperty=nameWithType>
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
