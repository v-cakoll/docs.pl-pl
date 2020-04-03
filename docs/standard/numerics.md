---
title: Wartości numeryczne na platformie .NET
ms.date: 10/18/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- SIMD
- System.Numerics.Vectors
- vectors
- scientific computing
- Complex
- numerics
- BigInteger
ms.assetid: dfebc18e-acde-4510-9fa7-9a0f4aa3bd11
ms.openlocfilehash: 3e9c817006930a36ebdce5c5965d78f1721c7056
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635152"
---
# <a name="numerics-in-net"></a>Wartości numeryczne na platformie .NET

.NET zapewnia zakres liczbowych liczbowych liczb i elementów ekscytacji zmiennoprzecinkowych, a <xref:System.Numerics.BigInteger?displayProperty=nameWithType>także <xref:System.Numerics.Complex?displayProperty=nameWithType>, który jest typem integralnym bez teoretycznej górnej <xref:System.Numerics> lub dolnej granicy, która reprezentuje liczby złożone, oraz zestaw typów obsługujących kartę SIMD w obszarze nazw.
  
## <a name="integer-types"></a>Typy całkowite

Program .NET obsługuje zarówno podpisane, jak i niepodpisane typy całkowitej 8-, 16-, 32- i 64-bitowe, które są wymienione w poniższej tabeli:
  
|Typ|Podpisane/niepodpisane|Rozmiar (w bajtach)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Niepodpisane|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisane|2|-32,768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisane|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisane|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisane|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Niepodpisane|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Niepodpisane|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Niepodpisane|8|0|18,446,744,073,709,551,615|  
  
Każdy typ liczby całkowitej obsługuje zestaw standardowych operatorów arytmetycznych. Klasa <xref:System.Math?displayProperty=nameWithType> zawiera metody dla szerszego zestawu funkcji matematycznych.

Można również pracować z poszczególnych bitów w wartości <xref:System.BitConverter?displayProperty=nameWithType> całkowitej przy użyciu klasy.  

> [!NOTE]  
> Niepodpisane typy całkowite nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [Niezależność języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

Struktura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> jest typu niezmienne, który reprezentuje dowolnie dużą liczbę całkowitą, której wartość w teorii nie ma górnej lub dolnej granicy. Metody <xref:System.Numerics.BigInteger> typu ściśle równoległe do innych typów całkowitych.
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinowe

Program .NET zawiera trzy prymitywne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli:
  
|Typ|Rozmiar (w bajtach)|Przybliżony zakres|Dokładność|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1,5 x 10<sup>−45</sup> do ±3,4 x 10<sup>38</sup>|~6-9 cyfr|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5,0 × 10<sup>−324</sup> do ±1,7 × 10<sup>308</sup>|~15-17 cyfr|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1,0 x 10<sup>-28</sup> do ±7,9228 x 10<sup>28</sup>|28-29 cyfr|  
  
Oba <xref:System.Single> <xref:System.Double> i typy obsługują wartości specjalne, które reprezentują nie-liczba i nieskończoności. Na przykład <xref:System.Double> typ zawiera następujące <xref:System.Double.NaN?displayProperty=nameWithType>wartości: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, , i . Użyj , <xref:System.Double.IsNaN%2A?displayProperty=nameWithType> <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>i <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> metody, aby przetestować dla tych specjalnych wartości.

Każdy typ zmiennoprzecinowy obsługuje zestaw standardowych operatorów arytmetycznych. Klasa <xref:System.Math?displayProperty=nameWithType> zawiera metody dla szerszego zestawu funkcji matematycznych. .NET Core 2.0 i <xref:System.MathF?displayProperty=nameWithType> nowsze zawiera klasę, <xref:System.Single> która zawiera metody, które akceptują argumenty typu.

Można również pracować z poszczególnych <xref:System.Double> <xref:System.Single> bitów i <xref:System.BitConverter?displayProperty=nameWithType> wartości przy użyciu klasy. Struktura <xref:System.Decimal?displayProperty=nameWithType> ma swoje własne <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>metody i , do pracy z wartością dziesiętną poszczególnych bitów, jak również własny zestaw metod wykonywania niektórych dodatkowych operacji matematycznych.
  
<xref:System.Double> Typy <xref:System.Single> i typy są przeznaczone do użycia dla wartości, które ze względu na swój charakter są nieprecyzyjne (na przykład odległość między dwiema gwiazdami) oraz dla zastosowań, w których nie jest wymagany wysoki stopień precyzji i mały błąd zaokrąglania. Użyj <xref:System.Decimal?displayProperty=nameWithType> typu w przypadkach, w których wymagana jest większa precyzja i błędy zaokrąglania powinny być zminimalizowane.

> [!NOTE]
> Typ <xref:System.Decimal> nie eliminuje potrzeby zaokrąglania. Raczej minimalizuje błędy spowodowane zaokrąglaniem.
  
## <a name="complex"></a>Complex

Struktura <xref:System.Numerics.Complex?displayProperty=nameWithType> reprezentuje liczbę zespoloną, czyli liczbę z częścią liczbową rzeczywistą i wyimaginowaną częścią liczbową. Obsługuje standardowy zestaw operatorów konwersji arytmetycznych, porównawczych, równości, jawnych i niejawnych, a także metod matematycznych, algebraicznych i trygonometrycznych.  
  
## <a name="simd-enabled-types"></a>Typy obsługujące kartę SIMD

Obszar <xref:System.Numerics> nazw zawiera zestaw typów obsługujących kartę .NET SIMD. Operacje SIMD (Single Instruction Multiple Data) można zrównoleglić na poziomie sprzętu. Zwiększa to przepływność obliczeń wektoryzowanych, które są powszechne w aplikacjach matematycznych, naukowych i graficznych.
  
Typy obsługujące kartę .NET SIMD są następujące:

- <xref:System.Numerics.Vector3>, <xref:System.Numerics.Vector2>i <xref:System.Numerics.Vector4> typów, które reprezentują wektory z 2, <xref:System.Single> 3 i 4 wartości.

- Dwa typy <xref:System.Numerics.Matrix3x2>macierzy, , który reprezentuje <xref:System.Numerics.Matrix4x4>macierz 3x2 i , który reprezentuje macierz 4x4.

- Typ, <xref:System.Numerics.Plane> który reprezentuje płaszczyznę w przestrzeni trójwymiarowej.

- Typ, <xref:System.Numerics.Quaternion> który reprezentuje wektor, który jest używany do kodowania trójwymiarowych obrotów fizycznych.

- Typ, <xref:System.Numerics.Vector%601> który reprezentuje wektor określonego typu numerycznego i zapewnia szeroki zestaw operatorów, które korzystają z obsługi SIMD. Liczba <xref:System.Numerics.Vector%601> wystąpienia jest stała, ale <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> jego wartość zależy od procesora CPU komputera, na którym kod jest wykonywany.
  > [!NOTE]
  > Typ <xref:System.Numerics.Vector%601> nie jest uwzględniony w .NET Framework. Aby uzyskać dostęp do tego typu, należy zainstalować pakiet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet.
  
Typy obsługujące kartę SIMD są implementowane w taki sposób, że mogą być używane ze sprzętem nieobjętym kartą SIMD lub kompilatorami JIT. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być uruchamiane przez środowisko wykonawcze korzystające z kompilatora RyuJIT, który znajduje się w .NET Core i w wersjach .NET Framework 4.6 i nowszych. Dodaje obsługę SIMD podczas kierowania procesorów 64-bitowych.

## <a name="see-also"></a>Zobacz też

- [Standardowe ciągi formatujące liczby](base-types/standard-numeric-format-strings.md)
