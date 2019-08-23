---
title: Typy kopiowalne i niekopiowalne
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2cdaa312c037714a34e25e62ad318c9bc745ea7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953191"
---
# <a name="blittable-and-non-blittable-types"></a>Typy kopiowalne i niekopiowalne
Większość typów danych ma wspólną reprezentację w pamięci zarządzanej i niezarządzanej i nie wymaga specjalnej obsługi przez organizatora międzyoperacyjności. Typy te są nazywane *danych kopiowalnychmi* , ponieważ nie wymagają konwersji podczas przekazywania między zarządzanym i niezarządzanym kodem.  
  
 Struktury zwracane z wywołań wywołania platformy muszą być typami danych kopiowalnych. Wywołanie platformy nie obsługuje struktur innych niż danych kopiowalnych jako typów zwracanych.  
  
 Następujące typy z <xref:System> przestrzeni nazw są typami danych kopiowalnych:  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 Następujące typy złożone są również danych kopiowalnych:  
  
- Jednowymiarowe tablice typów danych kopiowalnych, takie jak tablica liczb całkowitych. Jednak typ, który zawiera zmienną tablicę typów danych kopiowalnych, nie należy do siebie danych kopiowalnych.  
  
- Sformatowane typy wartości, które zawierają tylko typy danych kopiowalnych (i klasy, jeśli są organizowane jako sformatowane typy). Aby uzyskać więcej informacji na temat sformatowanych typów wartości, zobacz [domyślne kierowanie dla typów wartości](default-marshaling-behavior.md#default-marshaling-for-value-types).  
  
 Odwołania do obiektów nie są danych kopiowalnych. Obejmuje to tablicę odwołań do obiektów, które są danych kopiowalnych przez siebie. Na przykład można zdefiniować strukturę danych kopiowalnych, ale nie można zdefiniować typu danych kopiowalnych, który zawiera tablicę odwołań do tych struktur.  
  
 Jako Optymalizacja, tablice typów danych kopiowalnych i klas, które zawierają tylko składowe danych kopiowalnych, [](../../../docs/framework/interop/copying-and-pinning.md) są przypięte zamiast kopiowane podczas organizowania. Te typy mogą być organizowane jako parametry wejściowe/out, gdy wywołujący i wywoływany są w tym samym elemencie Apartment. Jednak te typy są faktycznie organizowane jako parametry i należy zastosować <xref:System.Runtime.InteropServices.InAttribute> atrybuty i <xref:System.Runtime.InteropServices.OutAttribute> , jeśli chcesz zorganizować argument jako parametr in/out.  
  
 Niektóre typy danych zarządzanych wymagają innej reprezentacji w niezarządzanym środowisku. Te typy danych inne niż danych kopiowalnych muszą zostać przekonwertowane na formularz, który może być zorganizowany. Na przykład, zarządzanymi ciągami są typy inne niż danych kopiowalnych, ponieważ muszą one być konwertowane do obiektów String, zanim będą mogły być organizowane.  
  
 Poniższa tabela zawiera listę typów innych niż danych kopiowalnych z <xref:System> przestrzeni nazw. [Delegaty](default-marshaling-behavior.md#default-marshaling-for-delegates), które są strukturami danych, które odwołują się do metody statycznej lub do wystąpienia klasy, również nie są danych kopiowalnych.  
  
|Typ inny niż danych kopiowalnych|Opis|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje na tablicę w stylu C lub `SAFEARRAY`.|  
|[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|Konwertuje do wartości 1, 2 lub 4-bajtowej na wartość `true` 1 lub-1.|  
|[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Konwertuje na znak Unicode lub ANSI.|  
|[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Konwertuje do interfejsu klasy.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Konwertuje na wariant lub interfejs.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje na tablicę w stylu C lub `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Konwertuje na ciąg kończący się w odwołaniu o wartości null lub w postaci BSTR.|  
|[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Konwertuje na strukturę ze stałym układem pamięci.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje na tablicę w stylu C lub `SAFEARRAY`.|  
  
 Typy klas i obiektów są obsługiwane tylko przez międzyoperacyjność modelu COM. W przypadku odpowiednich typów w Visual Basic C#, i C++, zobacz [Omówienie biblioteki klas](../../standard/class-library-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Domyślne zachowanie marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)
