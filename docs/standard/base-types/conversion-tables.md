---
title: Tabele konwersji typów na platformie .NET
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73103889"
---
# <a name="type-conversion-tables-in-net"></a>Tabele konwersji typów na platformie .NET
Konwersja poszerzenia występuje, gdy wartość jednego typu jest konwertowana na inny typ, który ma równy lub większy rozmiar. Konwersja zawężająca występuje, gdy wartość jednego typu jest konwertowana na wartość innego typu, który ma mniejszy rozmiar. Tabele w tym temacie ilustrują zachowania wystawiane przez oba typy konwersji.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli opisano konwersje rozszerzające, które można wykonać bez utraty informacji.  
  
|Typ|Można przekonwertować bez utraty danych na|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.SByte>|<xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int16>|<xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt16>|<xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Char>|<xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int32>|<xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.UInt32>|<xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 Niektóre poszerzenie konwersji <xref:System.Single> <xref:System.Double> do lub może spowodować utratę precyzji. W poniższej tabeli opisano poszerzenie konwersji, które czasami powodują utratę informacji.  
  
|Typ|Można przekonwertować na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zawężanie konwersji  
 Konwersja zawężająca lub <xref:System.Single> <xref:System.Double> może spowodować utratę informacji. Jeśli typ docelowy nie może poprawnie wyrazić wielkości źródła, wynikowy `PositiveInfinity` typ `NegativeInfinity`jest ustawiony na stałą lub . `PositiveInfinity`wynika z podzielenia liczby dodatniej przez zero i <xref:System.Single> jest <xref:System.Double> również zwracany, `MaxValue` gdy wartość a lub przekracza wartość pola. `NegativeInfinity`wynika z podzielenia liczby ujemnej przez zero i <xref:System.Single> <xref:System.Double> jest również zwracany, gdy wartość lub spadnie poniżej wartości `MinValue` pola. Konwersja z <xref:System.Double> a <xref:System.Single> na `PositiveInfinity` a `NegativeInfinity`może spowodować lub .  
  
 Konwersja zawężająca może również spowodować utratę informacji dla innych typów danych. Jednak jest <xref:System.OverflowException> generowany, jeśli wartość typu, który jest konwertowany wykracza poza zakres określony `MaxValue` przez `MinValue` typ docelowy i pola, a konwersja jest sprawdzana przez czas wykonywania, aby upewnić się, że wartość typu docelowego nie przekracza jego `MaxValue` lub `MinValue`. Konwersje, które są <xref:System.Convert?displayProperty=nameWithType> wykonywane z klasą są zawsze sprawdzane w ten sposób.  
  
 W poniższej tabeli wymieniono konwersje, które wyrzucają konwersję <xref:System.OverflowException> przy użyciu <xref:System.Convert?displayProperty=nameWithType> lub dowolną wartość sprawdzaną, jeśli wartość typu konwertowanego znajduje się poza zdefiniowanym zakresem typu wynikowego.  
  
|Typ|Można przekonwertować na|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>|  
|<xref:System.Int16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16>|  
|<xref:System.UInt16>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>|  
|<xref:System.Int32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32>|  
|<xref:System.UInt32>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>|  
|<xref:System.Int64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64>|  
|<xref:System.UInt64>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>|  
|<xref:System.Decimal>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Single>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
|<xref:System.Double>|<xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64>|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Convert?displayProperty=nameWithType>
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
