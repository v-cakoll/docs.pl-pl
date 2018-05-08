---
title: Wartości numeryczne w programie .NET Framework
ms.date: 03/30/2017
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
ms.openlocfilehash: a2a795fb52c123840c1ba7b82f77d6745feba89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="numerics-in-the-net-framework"></a>Wartości numeryczne w programie .NET Framework
.NET Framework obsługuje standardowe liczbowych podstawowych całkowitych i zmiennoprzecinkowych oraz <xref:System.Numerics.BigInteger>, typem całkowitym bez teoretycznej górnej i dolnej granicy <xref:System.Numerics.Complex>, typ, który reprezentuje liczby złożone oraz zestaw włączone SIMD typy wektorów <xref:System.Numerics> przestrzeni nazw.  
  
 Ponadto System.Numerics.Vectors, włączone SIMD biblioteki typów vectory został wydany jako pakietu NuGet.  
  
## <a name="integral-types"></a>Typy całkowite  
 .NET Framework obsługuje zarówno znakiem i bez znaku liczby całkowite z zakresu od jednego bajtu do ośmiu bajtów długości. Poniższa tabela zawiera listę typów całkowitych i ich rozmiarów, wskazuje, czy ich są podpisane lub niepodpisane i dokumentów w ich zakresie. Wszystkie liczby całkowite są typami wartości.  
  
|Typ|Signed/Unsigned|Rozmiar (w bajtach)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bez znaku|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisany|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisany|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisany|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisany|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bez znaku|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bez znaku|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bez znaku|8|0|18,446,744,073,709,551,615|  
  
 Każdy typ całkowity obsługuje standardowy zestaw arytmetyczne, porównania równości, jawnej konwersji i operatory niejawnej konwersji. Każdy liczba całkowita obejmuje również metody, aby wykonać porównania równości i względną porównań, aby przekonwertować reprezentację liczby do tej liczby całkowitej i można przekonwertować typu integer do reprezentacji ciągu. Niektóre dodatkowe operacji matematycznych poza tymi, które obsługiwane przez standardowych operatorów, takich jak zaokrąglania i zidentyfikowaniu mniejsza lub większa wartość dwie liczb całkowitych, są dostępne z <xref:System.Math> klasy. Użytkownik może również współpracować z poszczególne bity wartość całkowitą przy użyciu <xref:System.BitConverter> klasy.  
  
 Należy pamiętać, że niepodpisanych typów całkowitych nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i elementy niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe  
 .NET Framework obejmuje trzy pierwotnych zmiennoprzecinkowych typów, które są wymienione w poniższej tabeli.  
  
|Typ|Rozmiar (w bajtach)|Minimalnie|Maksymalnie|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1, 79769313486232E308|1, 79769313486232E308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3, 402823E38|3, 402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Każdy typ zmiennoprzecinkowy obsługuje standardowy zestaw arytmetyczne, porównania równości, jawnej konwersji i operatory niejawnej konwersji. Każdy zawiera również metody służące do wykonania porównania równości i względną porównań, można przekonwertować ciągu reprezentującego liczba zmiennoprzecinkowa i konwertowanie liczby zmiennoprzecinkowej do reprezentacji ciągu. Niektóre dodatkowe operacji matematycznych, algebraicznych i trygonometryczne są dostępne z <xref:System.Math> klasy. Może również współpracować z wszystkie bity w <xref:System.Double> i <xref:System.Single> wartości przy użyciu <xref:System.BitConverter> klasy. <xref:System.Decimal?displayProperty=nameWithType> Struktury ma własną metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> i <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>, w przypadku pracy z wartości dziesiętnej przez poszczególne usługi bits, a także własny zestaw metod wykonywania pewnych dodatkowych operacji matematycznych.  
  
 <xref:System.Double> i <xref:System.Single> typy są przeznaczone do użycia w przypadku wartości według rodzaju nieprecyzyjne (na przykład odległość między dwóch gwiazdek w Słonecznemu) i dla aplikacji, w których wysoki stopień precision i pomniejszonego zaokrąglania błąd nie jest Wymagane. Należy używać <xref:System.Decimal?displayProperty=nameWithType> typu przypadki, w którym większą dokładność jest wymagany i zaokrąglania błędu jest niepożądane,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> jest niezmiennego typu, który reprezentuje dowolnie dużą liczbą całkowitą, którego wartość teoretycznie nie ma żadnych granic górnej i dolnej. Metody <xref:System.Numerics.BigInteger> typu ściśle równoległe tych innych typów całkowitych.  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex> Typu reprezentuje liczbą, czyli liczby z części liczbą rzeczywistą i zespoloną numer. Obsługuje ona standardowy zestaw arytmetyczne, porównania, równości, jawnej konwersji i operatory niejawnej konwersji, a także metod matematycznych, algebraicznych i trygonometryczne.  
  
## <a name="simd-enabled-vector-types"></a>Typy wektorów SIMD — włączone  
 <xref:System.Numerics> Przestrzeń nazw zawiera zestaw typy wektorów SIMD, włączone dla programu .NET Framework. SIMD (operacje na danych w jednej instrukcji wielu) umożliwia niektórych operacji jest zarządzana z przetwarzaniem na poziomie sprzętu, co powoduje wzrost wydajności dużych matematycznych, naukowych, i wykonać obliczenia przez wektory aplikacjom grafiki.  
  
 Typy wektorów SIMD, włączona w programie .NET Framework są następujące:.  Ponadto System.Numerics.Vectors zawiera typ płaszczyzny i typ Quaternion.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, i <xref:System.Numerics.Vector4> typy, które są 2-, 3 i 4-wymiarowej wektorów typu <xref:System.Single>.  
  
-   Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, który reprezentuje macierz 3 x 2; i <xref:System.Numerics.Matrix4x4>, reprezentuje macierzy 4 x 4.  
  
-   <xref:System.Numerics.Plane> i <xref:System.Numerics.Quaternion> typów.  
  
 Typy wektorów SimD, włączone są implementowane IL, co pozwala na włączone SimD sprzętu i kompilatory JIT. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być skompilowane przez nowe 64-bitowym przy użyciu kompilatora JIT dla zarządzanego kodu, który jest dołączony do platformy .NET Framework 4.6; zostaje włączona obsługa SIMD, gdy x64 procesorów.  
  
 Można również pobrać SIMD jako [pakietu NuGet](https://www.nuget.org/packages/System.Numerics.Vectors).  Pakiet NuGET zawiera również ogólnego <xref:System.Numerics.Vector%601> strukturę, która umożliwia tworzenie wektor żadnych pierwotny typ liczbowy. (Pierwotne typy liczbowe obejmują wszystkie typy liczbowe w <xref:System> przestrzeni nazw z wyjątkiem <xref:System.Decimal>.) Ponadto <xref:System.Numerics.Vector%601> struktury dostarcza bibliotekę podręczne metody, które można wywołać podczas pracy z kierunków.  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawy aplikacji](../../docs/standard/application-essentials.md)
