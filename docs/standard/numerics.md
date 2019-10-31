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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091592"
---
# <a name="numerics-in-net"></a>Wartości numeryczne na platformie .NET

Platforma .NET oferuje zakres liczb całkowitych i zmiennoprzecinkowych, a także <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, który jest typem całkowitym bez teoretycznych górnych lub dolnych granic, <xref:System.Numerics.Complex?displayProperty=nameWithType>, który reprezentuje liczby zespolone oraz zestaw typów z obsługą SIMD w przestrzeni nazw <xref:System.Numerics> .
  
## <a name="integer-types"></a>Typy całkowite

Platforma .NET obsługuje zarówno podpisane, jak i 8-, 16-, 32 i 64-bitowe typy całkowite, które są wymienione w poniższej tabeli:
  
|Typ|Ze znakiem/bez znaku|Rozmiar (w bajtach)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bajt|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Opatrzon|2|-32 768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Opatrzon|4|-2 147 483 648|2 147 483 647|  
|<xref:System.Int64?displayProperty=nameWithType>|Opatrzon|8|-zakresu od|9 223 372 036 854 775 807|  
|<xref:System.SByte?displayProperty=nameWithType>|Opatrzon|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bajt|2|0|65 535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bajt|4|0|4 294 967 295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bajt|8|0|18446744073709551615 są|  
  
Każdy typ Integer obsługuje zestaw standardowych operatorów arytmetycznych. Klasa <xref:System.Math?displayProperty=nameWithType> udostępnia metody szerszego zestawu funkcji matematycznych.

Możesz również korzystać z poszczególnych bitów w wartości całkowitej przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType>.  

> [!NOTE]  
> Typy liczb całkowitych bez znaku nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

Struktura <xref:System.Numerics.BigInteger?displayProperty=nameWithType> jest niezmiennym typem, który reprezentuje arbitralnie dużą liczbę całkowitą, której wartość teoretyczna nie ma górnych lub dolnych granic. Metody typu <xref:System.Numerics.BigInteger> ściśle równolegle z innymi typami całkowitymi.
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

Platforma .NET zawiera trzy pierwotne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli:
  
|Typ|Rozmiar (w bajtach)|Przybliżony zakres|Dokładność|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup>|~ 6-9 cyfr|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 cyfr|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup>|28-29 cyfr|  
  
Zarówno <xref:System.Single>, jak i typy <xref:System.Double> obsługują specjalne wartości, które reprezentują nie liczbę i nieskończoność. Na przykład typ <xref:System.Double> zapewnia następujące wartości: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Możesz użyć metod <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>i <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> do testowania pod kątem tych specjalnych wartości.

Każdy typ zmiennoprzecinkowy obsługuje zestaw standardowych operatorów arytmetycznych. Klasa <xref:System.Math?displayProperty=nameWithType> udostępnia metody szerszego zestawu funkcji matematycznych. Program .NET Core 2,0 lub nowszy zawiera klasę <xref:System.MathF?displayProperty=nameWithType>, która dostarcza metody akceptujące argumenty typu <xref:System.Single>.

Możesz również korzystać z poszczególnych bitów w <xref:System.Double> i <xref:System.Single> wartości przy użyciu klasy <xref:System.BitConverter?displayProperty=nameWithType>. Struktura <xref:System.Decimal?displayProperty=nameWithType> ma własne metody, <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> i <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>do pracy z pojedynczymi bitami wartości dziesiętnych, a także własny zestaw metod wykonywania pewnych dodatkowych operacji matematycznych.
  
Typy <xref:System.Double> i <xref:System.Single> są przeznaczone do użycia w przypadku wartości, które ich charakter są nieprecyzyjne (na przykład odległość między dwiema gwiazdkami) i dla aplikacji, w których nie jest wymagany wysoki stopień dokładności i mały błąd zaokrąglania. Należy użyć typu <xref:System.Decimal?displayProperty=nameWithType> w przypadkach, w których wymagana jest większa precyzja, a błędy zaokrąglania powinny być zminimalizowane.

> [!NOTE]
> Typ <xref:System.Decimal> nie eliminuje potrzeby zaokrąglania. Zamiast tego minimalizuje błędy ze względu na zaokrąglenie.
  
## <a name="complex"></a>Complex

Struktura <xref:System.Numerics.Complex?displayProperty=nameWithType> reprezentuje liczbę zespoloną, czyli liczbę z liczbą rzeczywistą i częściową część liczby. Obsługuje standardowy zestaw arytmetyczny, porównywania, równości, jawnych i niejawnych operatorów konwersji, a także matematycznych, algebraicznychowych i trygonometrycznych metod.  
  
## <a name="simd-enabled-types"></a>Typy z obsługą SIMD

Przestrzeń nazw <xref:System.Numerics> zawiera zestaw typów z obsługą .NET SIMD. Operacje SIMD (Single Instruction Multiple Data) mogą być równoległe na poziomie sprzętu. Zwiększa to przepływność obliczeń wektorowych, które są wspólne w aplikacjach matematycznych, naukowych i graficznych.
  
Dostępne są następujące typy SIMD .NET:

- Typy <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>i <xref:System.Numerics.Vector4>, które reprezentują wektory mające wartości 2, 3 i 4 <xref:System.Single>.

- Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, które reprezentują macierz 3 x 2, i <xref:System.Numerics.Matrix4x4>, które reprezentują macierz 4x4.

- Typ <xref:System.Numerics.Plane>, który reprezentuje płaszczyznę w przestrzeni trójwymiarowej.

- Typ <xref:System.Numerics.Quaternion>, który reprezentuje wektor, który jest używany do kodowania trójwymiarowych obrotów fizycznych.

- Typ <xref:System.Numerics.Vector%601>, który reprezentuje wektor określonego typu liczbowego i zawiera szeroki zestaw operatorów, które korzystają z obsługi SIMD. Liczba wystąpień <xref:System.Numerics.Vector%601> jest stała, ale jej wartość <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> zależy od procesora komputera, na którym wykonywany jest kod.
  > [!NOTE]
  > Typ <xref:System.Numerics.Vector%601> nie jest uwzględniony w .NET Framework. Musisz zainstalować pakiet NuGet [System. Numerics. Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) , aby uzyskać dostęp do tego typu.
  
Typy SIMD są implementowane w taki sposób, że mogą być używane z sprzętem lub kompilatorami JIT z obsługą SIMD. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być uruchamiane przez środowisko uruchomieniowe korzystające z kompilatora RyuJIT, który jest zawarty w oprogramowaniu .NET Core i w .NET Framework 4,6 i nowszych. Dodaje obsługę SIMD, gdy są kierowane procesory 64-bitowe.

## <a name="see-also"></a>Zobacz także

- [Podstawy aplikacji](application-essentials.md)
- [Standardowe ciągi formatujące liczby](base-types/standard-numeric-format-strings.md)
