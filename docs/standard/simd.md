---
title: Typy SIMD-przyspieszone w programie .NET
description: W tym artykule opisano typy SIMD-Enable w programie .NET i pokazano, jak używać sprzętowych operacji SIMD w językach C# i .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507783"
---
# <a name="use-simd-accelerated-numeric-types"></a>Użyj SIMD — przyspieszone typy liczbowe

SIMD (pojedyncza instrukcja, wiele danych) zapewnia obsługę sprzętu na potrzeby wykonywania operacji na wielu danych, równolegle przy użyciu jednej instrukcji. W programie .NET istnieje zestaw SIMD-przyspieszone typy w <xref:System.Numerics> przestrzeni nazw. Operacje SIMD mogą być równoległe na poziomie sprzętu. Zwiększa to przepływność obliczeń wektorowych, które są wspólne w aplikacjach matematycznych, naukowych i graficznych.

## <a name="net-simd-accelerated-types"></a>.NET SIMD — przyspieszone typy

Typy przyspieszone dla programu .NET SIMD obejmują następujące typy:

- Typy <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>i <xref:System.Numerics.Vector4> , które reprezentują wektory z 2, 3 i 4 <xref:System.Single> wartościami.

- Dwa typy macierzy, <xref:System.Numerics.Matrix3x2>, które reprezentują macierz 3 x 2, i <xref:System.Numerics.Matrix4x4>, która reprezentuje macierz 4x4 <xref:System.Single> wartości.

- <xref:System.Numerics.Plane> Typ, który reprezentuje płaszczyznę w trójwymiarowym miejscu przy użyciu <xref:System.Single> wartości.

- <xref:System.Numerics.Quaternion> Typ, który reprezentuje wektor, który jest używany do kodowania trójwymiarowych obrotów fizycznych przy użyciu <xref:System.Single> wartości.

- <xref:System.Numerics.Vector%601> Typ, który reprezentuje wektor określonego typu liczbowego i zawiera szeroki zestaw operatorów, które korzystają z obsługi SIMD. Liczba <xref:System.Numerics.Vector%601> wystąpień jest ustalona przez okres istnienia aplikacji, ale jej wartość <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> zależy od procesora komputera, na którym uruchomiono kod.

  > [!NOTE]
  > <xref:System.Numerics.Vector%601> Typ nie jest uwzględniony w .NET Framework. Musisz zainstalować pakiet NuGet [System. Numerics. Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) , aby uzyskać dostęp do tego typu.
  
Typy SIMD-przyspieszone są implementowane w taki sposób, że mogą być używane z akceleratorami sprzętu lub kompilatorów JIT nieSIMDymi. Aby skorzystać z instrukcji SIMD, aplikacje 64-bitowe muszą być uruchamiane przez środowisko uruchomieniowe, które używa kompilatora **RyuJIT** . Kompilator **RyuJIT** jest dołączany do oprogramowania .NET Core i w .NET Framework 4,6 i nowszych. Obsługa SIMD jest zapewniana tylko w przypadku procesorów 64-bitowych.

## <a name="how-to-use-simd"></a>Jak używać SIMD?

Przed wykonaniem niestandardowych algorytmów SIMD można sprawdzić, czy maszyna hosta obsługuje SIMD przy użyciu <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, która zwraca. <xref:System.Boolean> Nie gwarantuje to, że przyspieszenie SIMD jest włączone dla określonego typu, ale jest wskaźnikiem, który jest obsługiwany przez niektóre typy.

## <a name="simple-vectors"></a>Proste wektory

Najbardziej pierwotne typy SIMD-przyspieszone w programie .NET to <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>i <xref:System.Numerics.Vector4> typy, które reprezentują wektory z 2, 3 i 4 <xref:System.Single> wartościami. Poniższy przykład używa <xref:System.Numerics.Vector2> do dodawania dwóch wektorów.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

Istnieje również możliwość użycia wektorów .NET do obliczenia innych właściwości matematycznych wektorów, takich jak `Dot product`, `Transform`, `Clamp` i tak dalej.

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a>Matrix

<xref:System.Numerics.Matrix3x2>, która reprezentuje macierz 3 x 2, i <xref:System.Numerics.Matrix4x4>reprezentuje macierz 4x4. Może służyć do obliczeń dotyczących macierzy. W poniższym przykładzie pokazano mnożenie macierzy do macierzy transtransponowanej przy użyciu SIMD.

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a>>\<wektor T

<xref:System.Numerics.Vector%601> Daje możliwość użycia dłuższych wektorów. Licznik <xref:System.Numerics.Vector%601> wystąpienia został naprawiony, ale jego wartość <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> zależy od procesora komputera, na którym uruchomiono kod.

W poniższym przykładzie pokazano Dodawanie długich elementów tablic za <xref:System.Numerics.Vector%601>pomocą.

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a>Uwagi

SIMD może usunąć jedną wąskie gardła i uwidocznić kolejne, na przykład przepustowość pamięci. Ogólnie rzecz biorąc, korzyści wynikające z używania SIMD różnią się w zależności od konkretnego scenariusza, a w niektórych przypadkach może to nawet być gorsza niż prostszy kod nieSIMD równoważny.
