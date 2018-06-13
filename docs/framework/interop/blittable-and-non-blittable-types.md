---
title: Typy kopiowalne i niekopiowalne
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acef752cf54d28dd1f07431b5dbbadbac0b7849e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392294"
---
# <a name="blittable-and-non-blittable-types"></a>Typy kopiowalne i niekopiowalne
Większość typów danych ma reprezentacji w postaci typowych w pamięci zarządzane i niezarządzane i nie wymagają specjalnej obsługi przez organizatora międzyoperacyjnego. Te typy są nazywane *typy kopiowalne* ponieważ one nie wymagają konwersji, gdy są one przekazywane między zarządzanych i niezarządzanych kodu.  
  
 Struktury, które są zwracane z platformy wywołania wywołania musi być typy kopiowalne. Wywołanie platformy nie obsługuje niekopiowalnej struktury jako typów zwracanych.  
  
 Następujące typy z <xref:System> przestrzeni nazw są typy danych kopiowalnych:  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 Typy kopiowalne są również następujące typy złożone:  
  
-   Tablice jednowymiarowe typy danych kopiowalnych, takich jak tablica liczb całkowitych. Typ zawierający tablicę zmiennych typów danych kopiowalnych nie jest jednak sam danych kopiowalnych.  
  
-   Sformatowana wartość typy, które zawierają typy kopiowalne tylko (i klasy, jeśli są one organizowane jako typy sformatowany). Aby uzyskać więcej informacji na temat typów sformatowana wartość zobacz [domyślny Marshaling dla typów wartości](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).  
  
 Odwołania do obiektów nie są danych kopiowalnych. W tym tablicę odwołania do obiektów, które są kopiowalne samodzielnie. Na przykład można zdefiniować struktury, która jest możliwość kopiowania, ale nie można zdefiniować typu danych kopiowalnych, który zawiera tablicę odwołania do tych konstrukcji.  
  
 Do optymalizacji są tablice typy kopiowalne i klasy, które zawierają tylko elementy członkowskie danych kopiowalnych [przypięty](../../../docs/framework/interop/copying-and-pinning.md) zamiast skopiowanych podczas przekazywanie. Te typy może wydawać można zorganizować jako we/wy parametrów, gdy obiekt wywołujący i wywoływany znajdują się w tym samym apartamencie. Jednak te typy są faktycznie przekazywane tak jak parametry i należy zastosować <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybutów, aby kierować argument jako In/Out parametru.  
  
 Niektóre typy zarządzanych danych wymagają różnych reprezentacji w środowisku niezarządzane. Te typy danych niekopiowalnych należy przekonwertować do formularza, które mogą być przekazywane. Na przykład ciągi zarządzane są niekopiowalne, ponieważ muszą zostać przekonwertowane na obiektów string, zanim one mogą być przekazywane.  
  
 W poniższej tabeli wymieniono niekopiowalne z <xref:System> przestrzeni nazw. [Obiekty delegowane](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), struktury danych, które odwołują się do metody statycznej lub do wystąpienia klasy, które są również są niekopiowalne.  
  
|Typ danych kopiowalnych inne niż|Opis|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicę stylu języka C lub `SAFEARRAY`.|  
|[System.Boolean](https://msdn.microsoft.com/library/d4c00537-70f7-4ca6-8197-bfc1ec037ff9(v=vs.100))|Konwertuje wartość 1, 2 lub 4-bajtowych wartości z `true` jako 1 lub -1.|  
|[System.Char](https://msdn.microsoft.com/library/cecc87c1-075e-4cde-aa56-33d189f66feb(v=vs.100))|Konwertuje znak Unicode lub ANSI.|  
|[System.Class](https://msdn.microsoft.com/library/fe334af5-0123-43d8-be84-26f6f023ddb6(v=vs.100))|Konwertuje interfejsu klasy.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Konwertuje wariant lub interfejs.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicę stylu języka C lub `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Konwertuje ciąg przerywanie w odwołanie o wartości null lub BSTR.|  
|[System.Valuetype](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100))|Konwertuje struktury z układem stałym pamięci.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicę stylu języka C lub `SAFEARRAY`.|  
  
 Typy klas i obiektów są obsługiwane tylko przez COM interop. Dla odpowiednich typów w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++, zobacz [Przegląd biblioteki klas](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zachowanie marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)
