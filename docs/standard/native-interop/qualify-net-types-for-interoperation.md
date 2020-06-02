---
title: Kwalifikowanie typów .NET do współdziałania z modelem COM
description: Ten artykuł zawiera wskazówki ułatwiające uwidocznienie typów w zestawie .NET w aplikacjach COM dla współdziałania z modelem COM.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 5e8d604c8152d37475bf93e3b5687f24cfebfa02
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285966"
---
# <a name="qualifying-net-types-for-com-interoperation"></a>Kwalifikowanie typów .NET do współdziałania z modelem COM
Jeśli zamierzasz uwidocznić typy w zestawie w aplikacjach COM, weź pod uwagę wymagania międzyoperacyjności modelu COM w czasie projektowania. Typy zarządzane (Klasa, interfejs, struktura i Wyliczenie) bezproblemowo integrują się z typami COM w przypadku przestrzegania następujących wytycznych:  
  
- Klasy powinny jawnie implementować interfejsy.  
  
     Chociaż usługa międzyoperacyjna modelu COM zapewnia mechanizm automatycznego generowania interfejsu zawierającego wszystkie elementy członkowskie klasy i elementy członkowskie swojej klasy podstawowej, znacznie lepiej jest zapewnić jawne interfejsy. Wygenerowany automatycznie interfejs jest nazywany interfejsem klasy. Aby uzyskać wskazówki, zobacz [wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Można użyć Visual Basic, C# i C++ do dołączania definicji interfejsu w kodzie, zamiast konieczności używania języka definicji interfejsu (IDL) lub jego odpowiednika. Aby uzyskać szczegółowe informacje na temat składni, zobacz dokumentację języka.  
  
- Typy zarządzane muszą być publiczne.  
  
     Tylko typy publiczne w zestawie są rejestrowane i eksportowane do biblioteki typów. W efekcie tylko typy publiczne są widoczne dla modelu COM.  
  
     Zarządzane typy ujawniają funkcje w innym zarządzanym kodzie, który może nie być ujawniony w modelu COM. Na przykład, konstruktory sparametryzowane, metody statyczne i pola stałe nie są widoczne dla klientów modelu COM. Ponadto, ponieważ środowisko uruchomieniowe prowadzi dane do i z typu, dane mogą być kopiowane lub przekształcane.  
  
- Metody, właściwości, pola i zdarzenia muszą być publiczne.  
  
     Elementy członkowskie typów publicznych muszą być również publiczne, jeśli mają być widoczne dla modelu COM. Można ograniczyć widoczność zestawu, typu publicznego lub publicznych składowych typu publicznego przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute> . Domyślnie wszystkie typy publiczne i członkowie są widoczne.  
  
- Typy muszą mieć publiczny Konstruktor bez parametrów, który ma być aktywowany z modelu COM.  
  
     Typy zarządzane i publiczne są widoczne dla modelu COM. Niemniej jednak, jeśli nie ma publicznego konstruktora bez parametrów (Konstruktor bez argumentów), klienci COM nie mogą utworzyć tego typu. Klienci modelu COM nadal mogą używać typu, jeśli jest aktywowany w inny sposób.  
  
- Typy nie mogą być abstrakcyjne.  
  
     Żaden klient COM ani klient .NET nie mogą tworzyć typów abstrakcyjnych.  
  
 Po eksportowaniu do modelu COM Hierarchia dziedziczenia typu zarządzanego jest spłaszczona. Przechowywanie wersji różni się również między środowiskami zarządzanymi i niezarządzanymi. Typy ujawnione dla modelu COM nie mają takich samych cech wersji jak inne typy zarządzane.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Udostępnianie składników .NET Framework modelowi COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface)
- [Stosowanie atrybutów międzyoperacyjności](apply-interop-attributes.md)
- [Pakowanie zestawu .NET Framework dla modelu COM](../../framework/interop/packaging-an-assembly-for-com.md)
