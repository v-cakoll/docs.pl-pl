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
ms.openlocfilehash: 3b95a322377e82249a0375af589df74c658fcbf4
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507419"
---
# <a name="numerics-in-net"></a>Wartości numeryczne na platformie .NET

Platforma .NET oferuje zakres liczb całkowitych i zmiennoprzecinkowych, a także <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, który jest typem całkowitym bez teoretycznego górnego lub dolnego powiązania, <xref:System.Numerics.Complex?displayProperty=nameWithType>który reprezentuje liczby zespolone i zestaw typów z obsługą SIMD w <xref:System.Numerics> przestrzeni nazw.
  
## <a name="integer-types"></a>Typy całkowite

Platforma .NET obsługuje zarówno podpisane, jak i 8-, 16-, 32 i 64-bitowe typy całkowite, które są wymienione w poniższej tabeli:
  
|Typ|Ze znakiem/bez znaku|Rozmiar (w bajtach)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bajt|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Opatrzon|2|-32 768|32 767|  
|<xref:System.Int32?displayProperty=nameWithType>|Opatrzon|4|-2 147 483 648|2 147 483 647|  
|<xref:System.Int64?displayProperty=nameWithType>|Opatrzon|8|-zakresu od|9 223 372 036 854 775 807|  
|<xref:System.SByte?displayProperty=nameWithType>|Opatrzon|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bajt|2|0|65 535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bajt|4|0|4 294 967 295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bajt|8|0|18446744073709551615 są|  
  
Każdy typ Integer obsługuje zestaw standardowych operatorów arytmetycznych. <xref:System.Math?displayProperty=nameWithType> Klasa udostępnia metody szerszego zestawu funkcji matematycznych.

Możesz również korzystać z poszczególnych bitów w wartości całkowitej przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  

> [!NOTE]  
> Typy liczb całkowitych bez znaku nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura jest niezmiennym typem, który reprezentuje arbitralnie dużą liczbę całkowitą, której wartość teoretyczna nie ma górnych lub dolnych granic. Metody typu są <xref:System.Numerics.BigInteger> ściśle równoległe o inne typy całkowite.
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

Platforma .NET zawiera trzy pierwotne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli:
  
|Typ|Rozmiar (w bajtach)|Przybliżony zakres|Dokładność|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|± 1,5 x 10<sup>− 45</sup> do ± 3,4 x 10<sup>38</sup>|~ 6-9 cyfr|  
|<xref:System.Double?displayProperty=nameWithType>|8|± 5,0 × 10<sup>− 324</sup> do ± 1,7 × 10<sup>308</sup>|~ 15-17 cyfr|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|1,0 x 10<sup>-28</sup> do ± 7,9228 x 10<sup>28</sup>|28-29 cyfr|  
  
Oba <xref:System.Single> typy <xref:System.Double> i obsługują wartości specjalne, które reprezentują nie liczbę i nieskończoność. Na przykład <xref:System.Double> typ zawiera następujące wartości: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, i. <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> W celu przetestowania <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>tych specjalnych <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> wartości należy użyć metod <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, i.

Każdy typ zmiennoprzecinkowy obsługuje zestaw standardowych operatorów arytmetycznych. <xref:System.Math?displayProperty=nameWithType> Klasa udostępnia metody szerszego zestawu funkcji matematycznych. Program .NET Core 2,0 lub nowszy zawiera <xref:System.MathF?displayProperty=nameWithType> klasę, która dostarcza metody akceptujące argumenty <xref:System.Single> typu.

Możesz również korzystać z poszczególnych bitów w <xref:System.Double> i <xref:System.Single> wartości przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy. <xref:System.Decimal?displayProperty=nameWithType> Struktura ma własne metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> i, do pracy z pojedynczymi bitami wartości dziesiętnych, a <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29>także własny zestaw metod wykonywania pewnych dodatkowych operacji matematycznych.
  
Typy <xref:System.Double> i <xref:System.Single> są przeznaczone do użycia w przypadku wartości, które ich charakter są nieprecyzyjne (na przykład odległość między dwiema gwiazdkami) i dla aplikacji, w których nie jest wymagany wysoki stopień dokładności i mały błąd zaokrąglania. Użyj <xref:System.Decimal?displayProperty=nameWithType> typu dla przypadków, w których wymagana jest większa precyzja, a błędy zaokrąglania powinny być zminimalizowane.

> [!NOTE]
> <xref:System.Decimal> Typ nie eliminuje potrzeby zaokrąglania. Zamiast tego minimalizuje błędy ze względu na zaokrąglenie.
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> Struktura reprezentuje liczbę zespoloną, czyli liczbę z liczbą rzeczywistą i częściową część liczby. Obsługuje standardowy zestaw arytmetyczny, porównywania, równości, jawnych i niejawnych operatorów konwersji, a także matematycznych, algebraicznychowych i trygonometrycznych metod.  
  
## <a name="simd-enabled-types"></a>Typy z obsługą SIMD

<xref:System.Numerics> Przestrzeń nazw zawiera zestaw typów z obsługą .NET SIMD. Operacje SIMD (Single Instruction Multiple Data) mogą być równoległe na poziomie sprzętu. Zwiększa to przepływność obliczeń wektorowych, które są wspólne w aplikacjach matematycznych, naukowych i graficznych.
  
Dostępne są następujące typy SIMD .NET:

- Typy <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>i <xref:System.Numerics.Vector4> , które reprezentują wektory z 2, 3 i 4 <xref:System.Single> wartościami.

- Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, które reprezentują macierz 3 x 2, i <xref:System.Numerics.Matrix4x4>, która reprezentuje macierz 4x4.

- <xref:System.Numerics.Plane> Typ, który reprezentuje płaszczyznę w trójwymiarowej przestrzeni.

- <xref:System.Numerics.Quaternion> Typ, który reprezentuje wektor, który jest używany do kodowania trójwymiarowych obrotów fizycznych.

- <xref:System.Numerics.Vector%601> Typ, który reprezentuje wektor określonego typu liczbowego i zawiera szeroki zestaw operatorów, które korzystają z obsługi SIMD. Licznik <xref:System.Numerics.Vector%601> wystąpienia został ustalony, ale jego wartość <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> zależy od procesora CPU komputera, na którym wykonywany jest kod.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Typ nie jest uwzględniony w .NET Framework. Musisz zainstalować pakiet NuGet [System. Numerics. Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) , aby uzyskać dostęp do tego typu.
  
Typy SIMD są implementowane w taki sposób, że mogą być używane z sprzętem lub kompilatorami JIT z obsługą SIMD. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być uruchamiane przez środowisko uruchomieniowe korzystające z kompilatora RyuJIT, który jest zawarty w oprogramowaniu .NET Core i w .NET Framework 4,6 i nowszych. Dodaje obsługę SIMD, gdy są kierowane procesory 64-bitowe.

Aby uzyskać więcej informacji, zobacz [Korzystanie z SIMD-przyspieszonych typów liczbowych](simd.md).

## <a name="see-also"></a>Zobacz także

- [Standardowe ciągi formatujące liczby](base-types/standard-numeric-format-strings.md)
