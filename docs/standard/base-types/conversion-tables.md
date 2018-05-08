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
ms.openlocfilehash: fc2698a37dc77ccd8c58164ec5a34f21251b6dbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-conversion-tables-in-net"></a>Tabele konwersji typów w .NET
Rozszerzanie konwersji występuje, gdy wartość jeden typ jest konwertowany na inny typ, który jest równy lub większy rozmiar. Konwersji zawężającej występuje, gdy wartość jeden typ jest konwertowana na wartość innego typu, który ma mniejszy rozmiar. Tabele w tym temacie przedstawiają zachowania eksponowane przez obu typów konwersji.  
  
## <a name="widening-conversions"></a>Poszerzenie konwersji  
 W poniższej tabeli opisano konwersje rozszerzającą, które mogą być wykonywane bez utraty informacji.  
  
|Typ|Można przekonwertować bez utraty danych do|  
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
  
 Niektóre rozszerzanie konwersji do <xref:System.Single> lub <xref:System.Double> może spowodować utratę dokładności. W poniższej tabeli opisano konwersje rozszerzającą, które czasami spowodować utratę danych.  
  
|Typ|Może zostać przekonwertowany na|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.UInt64>|<xref:System.Single>, <xref:System.Double>|  
|<xref:System.Decimal>|<xref:System.Single>, <xref:System.Double>|  
  
## <a name="narrowing-conversions"></a>Zawężanie konwersji  
 Do konwersji zawężającej <xref:System.Single> lub <xref:System.Double> może spowodować utratę danych. Jeśli typ docelowy nie może poprawnie express wielkości źródła, wynikowy typ jest ustawiony na stałą `PositiveInfinity` lub `NegativeInfinity`. `PositiveInfinity` wyniki z dzielenia przez zero dodatnia i jest także zwracany kiedy wartość <xref:System.Single> lub <xref:System.Double> przekracza wartość `MaxValue` pola. `NegativeInfinity` wyniki z dzielenia przez zero ujemna i jest także zwracany kiedy wartość <xref:System.Single> lub <xref:System.Double> spadnie poniżej wartości `MinValue` pola. Konwersja z <xref:System.Double> do <xref:System.Single> może spowodować `PositiveInfinity` lub `NegativeInfinity`.  
  
 Konwersji zawężającej również może spowodować utratę danych dla innych typów danych. Jednak <xref:System.OverflowException> jest generowany, jeśli wartość typu, który jest przekształcany jest spoza zakresu określonego przez typ docelowy `MaxValue` i `MinValue` pola i konwersji jest sprawdzana przez środowiska uruchomieniowego upewnij się, że wartość elementu docelowego Typ nie może przekraczać jego `MaxValue` lub `MinValue`. Konwersje, które są wykonywane z <xref:System.Convert?displayProperty=nameWithType> klasy zawsze są sprawdzane w ten sposób.  
  
 W poniższej tabeli wymieniono konwersje, które zgłaszają <xref:System.OverflowException> przy użyciu <xref:System.Convert?displayProperty=nameWithType> lub dowolny wybrany konwersji, jeśli jest wartość typu konwertowanej do zdefiniowanego zakresu wynikowy typ.  
  
|Typ|Może zostać przekonwertowany na|  
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
 <xref:System.Convert?displayProperty=nameWithType>  
 [Konwersja typów w programie .NET](../../../docs/standard/base-types/type-conversion.md)
