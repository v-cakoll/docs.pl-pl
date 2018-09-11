---
title: Tabele konwersji typów w .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86642da8647d185d863607819bbb18de9e976e6b
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264158"
---
# <a name="type-conversion-tables-in-net"></a>Tabele konwersji typów w .NET
Rozszerzanie konwersji występuje, gdy wartość jednego typu jest konwertowana na inny typ, który jest równy lub większy rozmiar. Konwersja zawężająca występuje, gdy wartości z jednego typu jest konwertowany na wartość innego typu, który ma mniejszy rozmiar. Tabele w tym temacie ilustrują Trojan oba rodzaje konwersji.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli opisano konwersje rozszerzające, które mogą być wykonywane bez utraty informacji.  
  
|Typ|Mogą być konwertowane bez utraty danych do|  
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
  
 Niektóre poszerzeniem konwersji, aby <xref:System.Single> lub <xref:System.Double> może spowodować utratę dokładności. W poniższej tabeli opisano konwersje rozszerzające, które czasami powodować utraty informacji.  
  
|Typ|Mogą być konwertowane na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Konwersje zawężające  
 Konwersja zawężająca do <xref:System.Single> lub <xref:System.Double> może spowodować utratę danych. Jeśli typ docelowy nie może poprawnie express wielkość źródła, wynikowy typ jest ustawiony na wartość stałej `PositiveInfinity` lub `NegativeInfinity`. `PositiveInfinity` wyniki z dzielenia liczby dodatnie przez zero i również jest zwracane, jeśli wartość <xref:System.Single> lub <xref:System.Double> przekracza wartość `MaxValue` pola. `NegativeInfinity` wyniki z dzielenia liczby ujemnej przez zero i również jest zwracane, jeśli wartość <xref:System.Single> lub <xref:System.Double> spadnie poniżej wartości `MinValue` pola. Konwersja z <xref:System.Double> do <xref:System.Single> może spowodować `PositiveInfinity` lub `NegativeInfinity`.  
  
 Konwersja zawężająca może również spowodować utratę informacji dla innych typów danych. Jednak <xref:System.OverflowException> jest generowany, jeśli wartość typu, który jest przekształcany wykraczające poza zakres określony przez typ docelowy `MaxValue` i `MinValue` pola i konwersja jest sprawdzana przez środowisko uruchomieniowe, upewnij się, że wartość elementu docelowego Typ nie przekracza jego `MaxValue` lub `MinValue`. Konwersje, które są wykonywane przy użyciu <xref:System.Convert?displayProperty=nameWithType> klasy zawsze są sprawdzane w ten sposób.  
  
 W poniższej tabeli wymieniono konwersje, które generują <xref:System.OverflowException> przy użyciu <xref:System.Convert?displayProperty=nameWithType> lub dowolny wybrany konwersji, jeśli wartość typu konwertowanego znajduje się poza zakresem zdefiniowanego typu wynikowy.  
  
|Typ|Mogą być konwertowane na|  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Convert?displayProperty=nameWithType>  
- [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
