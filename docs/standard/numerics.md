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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f180e459764d6e8e4484072218f01c8bab8a3b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973462"
---
# <a name="numerics-in-net"></a>Wartości numeryczne na platformie .NET

.NET oferuje szeroką gamę liczbowych liczb całkowitych i zmiennoprzecinkowych podstawowych także <xref:System.Numerics.BigInteger?displayProperty=nameWithType>, który jest typem całkowitym bez teoretycznych górną lub dolną granicę <xref:System.Numerics.Complex?displayProperty=nameWithType>, która reprezentuje liczby zespolone oraz zestaw typów włączone SIMD w <xref:System.Numerics> przestrzeni nazw.
  
## <a name="integer-types"></a>Typy liczb całkowitych

.NET obsługuje zarówno podpisane lub niepodpisane 8-, 16-, 32- i 64-bitową liczbę całkowitą typy, które są wymienione w poniższej tabeli:
  
|Typ|Ze znakiem/bez znaku|Rozmiar (w bajtach)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bez znaku|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisany|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisany|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisany|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisany|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bez znaku|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bez znaku|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bez znaku|8|0|18,446,744,073,709,551,615|  
  
Każdy typ liczby całkowitej obsługuje zestaw standardowych operatorów arytmetycznych. <xref:System.Math?displayProperty=nameWithType> Klasa dostarcza metody dla szerszego zestawu funkcji matematycznych.

Można również pracować wszystkie bity w wartością całkowitą z zakresu przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy.  

> [!NOTE]  
> Typy liczb całkowitych bez znaku nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).

## <a name="biginteger"></a>BigInteger

<xref:System.Numerics.BigInteger?displayProperty=nameWithType> Struktura jest typem niezmienne, który reprezentuje liczbę całkowitą dowolnie dużą, którego wartość, teoretycznie nie ma żadnych granic górnej i dolnej. Metody <xref:System.Numerics.BigInteger> typu ściśle równoległe udostępnianych przez inne typy całkowitoliczbowe.
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe

.NET zawiera trzy pierwotne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli:
  
|Typ|Rozmiar (w bajtach)|Przybliżony zakres|Dokładność|  
|----------|--------|---------------------|--------------------|  
|<xref:System.Single?displayProperty=nameWithType>|4|±1.5 x 10<sup>−45</sup> do ±3.4 x 10<sup>38</sup>|~ 6 – 9 cyfr|  
|<xref:System.Double?displayProperty=nameWithType>|8|±5.0 x 10<sup>−324</sup> do ±1.7 x 10<sup>308</sup>|około 15 – 17 cyfr|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|±1.0 x 10<sup>-28</sup> do ±7.9228 x 10<sup>28</sup>|28 – 29 cyfr|  
  
Zarówno <xref:System.Single> i <xref:System.Double> typy obsługują specjalnych wartości, które reprezentują nie nieliczbowych i nieskończoność. Na przykład <xref:System.Double> typu zawiera następujące wartości: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, i <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>. Możesz użyć <xref:System.Double.IsNaN%2A?displayProperty=nameWithType>, <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType>, <xref:System.Double.IsPositiveInfinity%2A?displayProperty=nameWithType>, i <xref:System.Double.IsNegativeInfinity%2A?displayProperty=nameWithType> metody do testowania tych specjalnych wartości.

Każdy typ zmiennoprzecinkowy obsługuje zestaw standardowych operatorów arytmetycznych. <xref:System.Math?displayProperty=nameWithType> Klasa dostarcza metody dla szerszego zestawu funkcji matematycznych. .NET core 2.0 i nowsze wersje zawierają <xref:System.MathF?displayProperty=nameWithType> klasę, która udostępnia metody, które akceptuje argumenty <xref:System.Single> typu.

Możesz także pracować z pojedynczych bitów w <xref:System.Double> i <xref:System.Single> wartości przy użyciu <xref:System.BitConverter?displayProperty=nameWithType> klasy. <xref:System.Decimal?displayProperty=nameWithType> Struktura ma swoje własne metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> i <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>— w przypadku pracy z wartości dziesiętnej przez poszczególne usługi bits, a także swój własny zestaw metod wykonywania kilka dodatkowych operacji matematycznych.
  
<xref:System.Double> i <xref:System.Single> typy są przeznaczone do użytku z wartościami, które z natury są nieprecyzyjną (na przykład odległość między dwoma gwiazdek) i dla aplikacji, w których wysoki stopień dokładności i małych zaokrąglania błąd nie jest wymagana. Należy używać <xref:System.Decimal?displayProperty=nameWithType> typu w przypadkach, w którym większej dokładności jest wymagane i należy zminimalizować błędy zaokrąglania.

> [!NOTE]
> <xref:System.Decimal> Typu nie eliminuje potrzebę stosowania zaokrąglania. Przeciwnie minimalizuje błędy spowodowane zaokrąglanie.
  
## <a name="complex"></a>Complex

<xref:System.Numerics.Complex?displayProperty=nameWithType> Struktury reprezentuje liczby zespolonej, czyli liczbę części liczba rzeczywista i urojone numer. Obsługuje ona standardowy zestaw operacji arytmetycznych, porównanie, równości, operatory konwersji jawne i niejawne, a także metod matematycznych, algebraicznych i trygonometrycznych.  
  
## <a name="simd-enabled-types"></a>Typy z obsługą SIMD

<xref:System.Numerics> Przestrzeń nazw zawiera zestaw typów włączone .NET SIMD. Operacje SIMD (pojedynczej instrukcji wiele danych), może być przetwarzane równolegle na poziomie sprzętu. Które zwiększa przepływność zwektoryzowane obliczeń, które są wspólne w matematycznych, naukowych, a aplikacje grafiki.
  
Następujące typy włączone .NET SIMD:

- <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, I <xref:System.Numerics.Vector4> typy, które reprezentują wektorów z 2, 3 i 4 <xref:System.Single> wartości.

- Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, która reprezentuje macierz 3 x 2, a <xref:System.Numerics.Matrix4x4>, która reprezentuje macierzy 4 x 4.

- <xref:System.Numerics.Plane> Typ, który reprezentuje płaszczyzny w przestrzeni trójwymiarowej.

- <xref:System.Numerics.Quaternion> Typ, który reprezentuje wektor, który jest używany do kodowania trójwymiarowej rotacji fizycznych.

- <xref:System.Numerics.Vector%601> Typ, który reprezentuje wektor określonego typu liczbowego i oferuje szeroki zestaw operatorów, które korzystają z pomocy technicznej SIMD. Liczba <xref:System.Numerics.Vector%601> wystąpienia jest stała, ale jej wartość <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> zależy od procesora CPU komputera, na którym wykonywany jest kod.
  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Typ nie jest uwzględniony w .NET Framework. Należy zainstalować [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) pakietu NuGet, aby uzyskać dostęp do tego typu.
  
Włączone SIMD typy są implementowane w taki sposób, że mogą być używane z włączoną SIMD sprzętu lub kompilatory JIT. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowych należy uruchomić w czasie wykonywania, który używa kompilatora elementach RyuJIT, która wchodzi w skład platformy .NET Core i .NET Framework 4.6 lub nowszy. Dodaje obsługę SIMD przy przeznaczeniu 64-bitowych procesorach.

## <a name="see-also"></a>Zobacz także

- [Podstawy aplikacji](application-essentials.md)
- [Standardowe ciągi formatujące liczby](base-types/standard-numeric-format-strings.md)
