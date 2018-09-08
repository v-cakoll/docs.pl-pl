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
ms.openlocfilehash: 1d253e7a32d5f302b095a86ddb5c296d5fa8fa11
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209499"
---
# <a name="numerics-in-the-net-framework"></a>Wartości numeryczne w programie .NET Framework
Program .NET Framework obsługuje standardowe liczbowych podstawowych całkowite i zmiennoprzecinkowe także <xref:System.Numerics.BigInteger>, typ całkowitoliczbowy bez teoretycznych górną lub dolną granicę <xref:System.Numerics.Complex>, typ, który reprezentuje liczby zespolone oraz zbiór włączone SIMD Vector — typy w <xref:System.Numerics> przestrzeni nazw.  
  
 Ponadto System.Numerics.Vectors, włączone SIMD biblioteki typów vectory został wydany jako pakiet NuGet.  
  
## <a name="integral-types"></a>Typy całkowite  
 .NET Framework obsługuje zarówno ze znakiem i bez znaku liczby całkowite, począwszy od jednego bajtu do ośmiu bajtów długości. Poniższa tabela zawiera listę typów całkowitych i ich rozmiar, wskazuje, czy ich są podpisane lub niepodpisane i dokumenty, ich zakresu. Wszystkie liczby całkowite są typami wartości.  
  
|Typ|Ze znakiem/bez znaku|Rozmiar (bajty)|Wartość minimalna|Wartość maksymalna|  
|----------|----------------------|--------------------|-------------------|-------------------|  
|<xref:System.Byte?displayProperty=nameWithType>|Bez znaku|1|0|255|  
|<xref:System.Int16?displayProperty=nameWithType>|Podpisany|2|-32,768|32,767|  
|<xref:System.Int32?displayProperty=nameWithType>|Podpisany|4|-2,147,483,648|2,147,483,647|  
|<xref:System.Int64?displayProperty=nameWithType>|Podpisany|8|-9,223,372,036,854,775,808|9,223,372,036,854,775,807|  
|<xref:System.SByte?displayProperty=nameWithType>|Podpisany|1|-128|127|  
|<xref:System.UInt16?displayProperty=nameWithType>|Bez znaku|2|0|65,535|  
|<xref:System.UInt32?displayProperty=nameWithType>|Bez znaku|4|0|4,294,967,295|  
|<xref:System.UInt64?displayProperty=nameWithType>|Bez znaku|8|0|18,446,744,073,709,551,615|  
  
 Każdy typ całkowity obsługuje standardowy zestaw operacji arytmetycznych, porównanie, równości, jawna konwersja i operatory niejawnej konwersji. Każda liczba całkowita zawiera również metody służące do wykonania porównania równości i porównań względnych, aby przekonwertować ciąg reprezentujący liczbę do tej liczby całkowitej i przekonwertować całkowitą na jego reprezentację ciągu. Kilka dodatkowych operacji matematycznych poza tymi, które obsługiwane przez standardowych operatorów, takich jak zaokrąglania oraz identyfikowanie mniejsze lub większe wartości dwóch liczb całkowitych, są dostępne z <xref:System.Math> klasy. Można również pracować wszystkie bity w wartością całkowitą z zakresu przy użyciu <xref:System.BitConverter> klasy.  
  
 Należy pamiętać, że niepodpisanych typów całkowitych nie są zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md).  
  
## <a name="floating-point-types"></a>Typy zmiennoprzecinkowe  
 Program .NET Framework zawiera trzy pierwotne typy zmiennoprzecinkowe, które są wymienione w poniższej tabeli.  
  
|Typ|Rozmiar (w bajtach)|Minimalnie|Maksymalnie|  
|----------|-----------------------|-------------|-------------|  
|<xref:System.Double?displayProperty=nameWithType>|8|-1, 79769313486232E308|1, 79769313486232E308|  
|<xref:System.Single?displayProperty=nameWithType>|4|-3, 402823E38|3, 402823E38|  
|<xref:System.Decimal?displayProperty=nameWithType>|16|-79,228,162,514,264,337,593,543,950,335|79,228,162,514,264,337,593,543,950,335|  
  
 Każdy typ zmiennoprzecinkowy obsługuje standardowy zestaw operacji arytmetycznych, porównanie, równości, jawna konwersja i operatory niejawnej konwersji. Każdy zawiera również metody służące do wykonania porównania równości i porównań względnych, aby przekonwertować ciąg reprezentujący liczbę zmiennoprzecinkową i przekonwertować liczba zmiennoprzecinkowa na jego reprezentację ciągu. Kilka dodatkowych operacji matematycznych algebraicznych i trygonometrycznych są dostępne z <xref:System.Math> klasy. Możesz także pracować z pojedynczych bitów w <xref:System.Double> i <xref:System.Single> wartości przy użyciu <xref:System.BitConverter> klasy. <xref:System.Decimal?displayProperty=nameWithType> Struktura ma swoje własne metody <xref:System.Decimal.GetBits%2A?displayProperty=nameWithType> i <xref:System.Decimal.%23ctor%28System.Int32%5B%5D%29?displayProperty=nameWithType>— w przypadku pracy z wartości dziesiętnej przez poszczególne usługi bits, a także swój własny zestaw metod wykonywania kilka dodatkowych operacji matematycznych.  
  
 <xref:System.Double> i <xref:System.Single> typy są przeznaczone do użycia dla wartości, które z natury są nieprecyzyjną (na przykład odległość między dwóch gwiazdek w systemie słoneczny) i aplikacji, w których wysoki stopień dokładności i małych zaokrąglania błąd nie jest Wymagane. Należy używać <xref:System.Decimal?displayProperty=nameWithType> typu w przypadkach, w którym większej dokładności jest wymagane i zaokrąglania błędu jest niepożądany,  
  
## <a name="biginteger"></a>BigInteger  
 <xref:System.Numerics.BigInteger?displayProperty=nameWithType> to typ niezmienne, który reprezentuje liczbę całkowitą dowolnie dużą, którego wartość teoretycznie nie ma żadnych granic górny lub niższą. Metody <xref:System.Numerics.BigInteger> typu ściśle równoległe udostępnianych przez inne typy całkowitoliczbowe.  
  
## <a name="complex"></a>Complex  
 <xref:System.Numerics.Complex> Typ reprezentuje liczby zespolonej, czyli liczbę części liczba rzeczywista i urojone numer. Obsługuje ona standardowy zestaw operacji arytmetycznych, porównanie, równości, jawna konwersja i operatory niejawnej konwersji, a także metod matematycznych, algebraicznych i trygonometrycznych.  
  
## <a name="simd-enabled-vector-types"></a>Typy wektorowe obsługujące na SIMD  
 <xref:System.Numerics> Przestrzeń nazw zawiera zestaw typów wektora SIMD — włączony dla programu .NET Framework. SIMD (operacje na danych wielu instrukcji jednego) umożliwia niektórych operacji odbywać się równolegle na poziomie sprzętu, co powoduje wzrost wydajności ogromna matematycznych, naukowych i aplikacji graficznych, które wykonują obliczenia wektorów.  
  
 Są następujące typy wektorowe obsługujące na SIMD w .NET Framework:.  Ponadto System.Numerics.Vectors zawiera typ płaszczyzny i typem Quaternion.  
  
-   <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, i <xref:System.Numerics.Vector4> typów, które są 2-, 3 i 4-wymiarowej wektorów typu <xref:System.Single>.  
  
-   Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, która reprezentuje macierzy 3 x 2; i <xref:System.Numerics.Matrix4x4>, która reprezentuje macierzy 4 x 4.  
  
-   <xref:System.Numerics.Plane> i <xref:System.Numerics.Quaternion> typów.  
  
 Typy wektorowe obsługujące na SimD są implementowane w IL, co pozwala je do użycia na włączone SimD sprzętu i kompilatory JIT. Aby skorzystać z instrukcji SIMD, Twoje aplikacje 64-bitowe muszą być skompilowane przy użyciu nowego 64-bitowego kompilatora JIT dla kodu zarządzanego, który jest dołączony do programu .NET Framework 4.6; dodaje obsługę SIMD, gdy x64 procesorów.  
  
 Można również pobrać SIMD jako [pakietu NuGet](https://www.nuget.org/packages/System.Numerics.Vectors).  Pakiet NuGET obejmuje także ogólny <xref:System.Numerics.Vector%601> strukturę, która pozwala na tworzenie wektor dowolnego pierwotnego typu liczbowego. (Pierwotnych typów liczbowych obejmują wszystkie typy danych liczbowych w <xref:System> przestrzeni nazw, z wyjątkiem <xref:System.Decimal>.) Ponadto <xref:System.Numerics.Vector%601> struktura zawiera bibliotekę metody wygody, które można wywołać podczas pracy z wektorami.  
  
## <a name="see-also"></a>Zobacz także

- [Podstawy aplikacji](../../docs/standard/application-essentials.md)
