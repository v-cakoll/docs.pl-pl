---
title: Typy kopiowalne i niekopiowalne
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b4c1d213c2ed87126fc5eb9995050e14f9214bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199841"
---
# <a name="blittable-and-non-blittable-types"></a>Typy kopiowalne i niekopiowalne
Większość typów danych mają wspólne reprezentacji w pamięci zarządzanych i niezarządzanych i nie wymagają specjalnej obsługi, organizator międzyoperacyjny. Te typy są nazywane *kopiowalnymi* , ponieważ nie wymaga konwersji, gdy są one przekazywane między kodu zarządzanego i niezarządzanego.  
  
 Wywołania struktury, które są zwracane z platformy musi być typy danych kopiowalnych. Wywołanie platformy nie obsługuje struktury niekopiowalnych jako typów zwracanych.  
  
 Następujące typy z <xref:System> nazw są typy danych kopiowalnych:  
  
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
  
 Typy danych kopiowalnych są również następujące typy złożone:  
  
-   Tablice jednowymiarowe typów danych kopiowalnych, takich jak tablica liczb całkowitych. Typ, który zawiera zmienną tablicy typów danych kopiowalnych nie jest jednak sam danych kopiowalnych.  
  
-   Typy sformatowanej wartości, które zawierają typy danych kopiowalnych tylko (i klasy, jeśli są one organizowane jak sformatowane typy). Aby uzyskać więcej informacji na temat typów sformatowaną wartość zobacz [domyślny Marshaling dla typów wartości](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).  
  
 Odwołania do obiektu nie są danych kopiowalnych. Obejmuje to tablica odniesień do obiektów, które danych kopiowalnych samodzielnie. Na przykład można zdefiniować strukturę danych kopiowalnych, ale nie można zdefiniować typ danych kopiowalnych, który zawiera szereg odwołań do tych struktur.  
  
 Optymalizacji, są tablicami typy kopiowalne i klas, które zawierają tylko elementy członkowskie danych kopiowalnych [przypięte](../../../docs/framework/interop/copying-and-pinning.md) zamiast kopiowane podczas przekazywania międzyprocesowego. Te typy może okazać się być organizowany jako we/wy parametrów, gdy obiektami wywołującym i wywoływanym znajdują się w tej samej typu apartment. Jednak te typy są faktycznie przekazywane tak jak parametry i należy najpierw zastosować <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybuty, jeśli chcesz zorganizować argument jako In/Out parametru.  
  
 Niektóre typy zarządzanych danych wymagają różnych reprezentacji w środowisku niezarządzanych. Te typy danych niekopiowalnych należy przekonwertować do formularza, który może być organizowany. Na przykład ciągi zarządzane są typów niekopiowalnych, ponieważ muszą zostać przekonwertowane na obiektów w postaci ciągów, zanim one może być organizowany.  
  
 Poniższa tabela zawiera listę typów niekopiowalnych z <xref:System> przestrzeni nazw. [Delegaty](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), służą do struktur danych, które odwołują się do statycznej metody lub wystąpienia klasy, są również niekopiowalnych.  
  
|Typ danych kopiowalnych inne niż|Opis|  
|-------------------------|-----------------|  
|[System.Array](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicy stylu C lub `SAFEARRAY`.|  
|[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))|Konwertuje wartość 1, 2 lub 4-bajtową wartością `true` jako 1 lub -1.|  
|[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))|Konwertuje znak Unicode lub ANSI.|  
|[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))|Konwertuje interfejsu klasy.|  
|[System.Object](../../../docs/framework/interop/default-marshaling-for-objects.md)|Konwertuje typ variant lub interfejs.|  
|[System.Mdarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicy stylu C lub `SAFEARRAY`.|  
|[System.String](../../../docs/framework/interop/default-marshaling-for-strings.md)|Konwertuje ciąg przerywa w odwołanie o wartości null lub ciąg BSTR.|  
|[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))|Konwertuje struktury z układem stały pamięci.|  
|[System.Szarray](../../../docs/framework/interop/default-marshaling-for-arrays.md)|Konwertuje tablicy stylu C lub `SAFEARRAY`.|  
  
 Typy klas i obiektów są obsługiwane tylko przez współdziałania z modelem COM. Dla odpowiednich typów w pakietach [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#i C++, zobacz [Przegląd biblioteki klas](../../../docs/standard/class-library-overview.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zachowanie marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)
