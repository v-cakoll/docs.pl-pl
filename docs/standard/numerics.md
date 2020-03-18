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
ms.openlocfilehash: e5815058898cac165e7a47d761ee86bb9c4cb940
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091592"
---
# <a name="numerics-in-net"></a>Wartości numeryczne na platformie .NET

.NET udostępnia zakres liczbowych liczbowych liczbowych i zmiennoprzecinkowych elementów pierwotnych, a także <xref:System.Numerics.BigInteger?displayProperty=nameWithType>typ <xref:System.Numerics.Complex?displayProperty=nameWithType>integralny bez teoretycznej górnej lub dolnej granicy, <xref:System.Numerics> która reprezentuje liczby zespolone, oraz zestaw typów z obsługą karty SIMD w obszarze nazw.
  
## <a name="integer-types"></a>Typy całkowite

.NET obsługuje zarówno podpisane, jak i niepodpisane typy 8-, 16-, 32- i 64-bitowe liczby całkowite, które są wymienione w poniższej tabeli:
  
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
> Niepodpisane typy liczb całkowitych nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [Niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

Struktura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> jest niezmiennytyp, który reprezentuje arbitralnie dużą liczbę całkowitą, której wartość w teorii nie ma górnej lub dolnej granicy. Metody <xref:System.Numerics.BigInteger> typu ściśle równolegle do innych typów całki.
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

.NET zawiera trzy pierwotne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli:
  
|Typ|Rozmiar (w bajtach)|Przybliżony zakres|Dokładność|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1,5 x 10<sup>−45</sup> do ±3,4 x 10<sup>38</sup>|~6-9 cyfr|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5,0 × 10<sup>−324</sup> do ±1,7 × 10<sup>308</sup>|~15-17 cyfr|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1,0 x 10<sup>-28</sup> do ±7,9228 x 10<sup>28</sup>|28-29 cyfr|  
  
Oba <xref:System.Single> <xref:System.Double> i typy obsługują specjalne wartości, które reprezentują nie-liczba i nieskończoność. Na przykład <xref:System.Double> typ zawiera następujące <xref:System.Double.NaN?displayProperty=nameWithType>wartości: <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>, , i . Używasz <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>i <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> metody do testowania tych wartości specjalnych.

Każdy typ zmiennoprzecinkowy obsługuje zestaw standardowych operatorów arytmetycznych. Klasa <xref:System.Math?displayProperty=nameWithType> zawiera metody dla szerszego zestawu funkcji matematycznych. .NET Core 2.0 i <xref:System.MathF?displayProperty=nameWithType> nowsze zawiera klasę, <xref:System.Single> która zawiera metody, które akceptują argumenty typu.

Można również pracować z poszczególnych <xref:System.Double> <xref:System.Single> bitów i <xref:System.BitConverter?displayProperty=nameWithType> wartości przy użyciu klasy. Struktura <xref:System.Decimal?displayProperty=nameWithType> ma swoje własne <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> metody <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>i , do pracy z wartości dziesiętnej poszczególnych bitów, jak również własny zestaw metod wykonywania niektórych dodatkowych operacji matematycznych.
  
I <xref:System.Double> <xref:System.Single> typy są przeznaczone do użycia dla wartości, które ze swej natury są nieprecyzyjne (na przykład odległość między dwiema gwiazdami) oraz dla zastosowań, w których nie jest wymagany wysoki stopień precyzji i mały błąd zaokrąglania. Należy użyć <xref:System.Decimal?displayProperty=nameWithType> tego typu dla przypadków, w których wymagana jest większa precyzja i błędy zaokrąglania powinny być zminimalizowane.

> [!NOTE]
> Typ <xref:System.Decimal> nie eliminuje potrzeby zaokrąglania. Zamiast tego minimalizuje błędy z powodu zaokrąglania.
  
## <a name="complex"></a>Complex

Struktura <xref:System.Numerics.Complex?displayProperty=nameWithType> reprezentuje liczbę zespoloną, czyli liczbę z częścią liczbą rzeczywistą i wyimaginowaną częścią liczbową. Obsługuje standardowy zestaw metod arytmetycznych, porównawczych, równości, jawnych i niejawnych konwersji, a także metod matematycznych, algebraicznych i trygonometrycznych.  
  
## <a name="simd-enabled-types"></a>Typy z obsługą karty SIMD

Obszar <xref:System.Numerics> nazw zawiera zestaw typów obsługujących kartę .NET simd. Operacje SIMD (Single Instruction Multiple Data) mogą być równoległe na poziomie sprzętu. Zwiększa to przepływwę obliczeń wektorowanych, które są wspólne w aplikacjach matematycznych, naukowych i graficznych.
  
Typy z obsługą karty .NET SIMD są następujące:

- , <xref:System.Numerics.Vector2> <xref:System.Numerics.Vector3>i <xref:System.Numerics.Vector4> typy, które reprezentują wektory z <xref:System.Single> wartościami 2, 3 i 4.

- Dwa typy <xref:System.Numerics.Matrix3x2>macierzy , , który reprezentuje <xref:System.Numerics.Matrix4x4>macierz 3x2 i , który reprezentuje macierz 4x4.

- Typ, <xref:System.Numerics.Plane> który reprezentuje płaszczyznę w przestrzeni trójwymiarowej.

- Typ, <xref:System.Numerics.Quaternion> który reprezentuje wektor, który jest używany do kodowania trójwymiarowych obrótów fizycznych.

- Typ, <xref:System.Numerics.Vector%601> który reprezentuje wektor określonego typu liczbowego i zapewnia szeroki zestaw operatorów, które korzystają z obsługi karty SIMD. Liczba <xref:System.Numerics.Vector%601> wystąpienia jest stała, ale <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> jego wartość zależy od procesora CPU komputera, na którym kod jest wykonywany.
  > [!NOTE]
  > Typ <xref:System.Numerics.Vector%601> nie jest uwzględniony w platformie .NET Framework. Aby uzyskać dostęp do tego typu, należy zainstalować pakiet [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet.
  
Typy z obsługą karty SIMD są implementowane w taki sposób, że mogą być używane ze sprzętem nieobsługującym karty SIMD lub kompilatorami JIT. Aby korzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być uruchamiane przez program runtime, który używa kompilatora RyuJIT, który znajduje się w .NET Core i .NET Framework 4.6 i nowszych wersjach. Dodaje obsługę karty SIMD podczas kierowania na procesory 64-bitowe.

## <a name="see-also"></a>Zobacz też

- [Podstawy aplikacji](application-essentials.md)
- [Standardowe ciągi formatujące liczby](base-types/standard-numeric-format-strings.md)
