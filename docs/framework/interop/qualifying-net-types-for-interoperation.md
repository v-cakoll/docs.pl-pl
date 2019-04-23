---
title: Kwalifikowanie typów .NET do międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cad67f52a4ca977606d7b5a307868ff129570e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097980"
---
# <a name="qualifying-net-types-for-interoperation"></a>Kwalifikowanie typów .NET do międzyoperacyjności
Jeśli zamierzasz ujawnić typy w zestawie, do aplikacji modelu COM, należy wziąć pod uwagę wymagania Usługa międzyoperacyjna modelu COM w czasie projektowania. Typy zarządzane (klasy, interfejsu, struktury i wyliczenia) bezproblemowo integrują się z typów modelu COM podczas przestrzegać następujących wytycznych:  
  
-   Klasy należy jawnie implementować interfejsów.  
  
     Chociaż usługa międzyoperacyjna modelu COM udostępnia mechanizm do automatycznego generowania interfejs zawierający wszystkie elementy członkowskie klasy i składowych klasy bazowej, jest znacznie lepiej podać jawne interfejsy. Automatycznie generowanego interfejsu nosi nazwę interfejsu klasy. Aby uzyskać wskazówki, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Visual Basic, można użyć C#i C++, funkcje definicji interfejsu w kodzie, nie trzeba używać języka definicji interfejsu (IDL) lub jej odpowiednik. Szczegóły składni na ten temat można znaleźć w dokumentacji języka.  
  
-   Typy zarządzane muszą być publiczne.  
  
     Tylko typy publiczne w zestawie są rejestrowane i wyeksportowane do biblioteki typów. W rezultacie tylko typy publiczne są widoczne dla modelu COM.  
  
     Zarządzane typy udostępniają funkcje do innego kodu zarządzanego, który nie może być widoczne dla modelu COM. Na przykład konstruktory sparametryzowane, metody statyczne i stałe pola nie są widoczne dla klientów modelu COM. Co więcej jak środowisko uruchomieniowe kieruje danych do i z typu, dane mogą zostać skopiowane lub przekształcone.  
  
-   Metody, właściwości, pola i zdarzenia muszą być publiczne.  
  
     Elementów członkowskich typów publicznych również muszą być publiczne, jeśli mają być widoczne dla modelu COM. Widoczność zestaw, typ publiczny lub publiczne elementy członkowskie typu publicznego można ograniczyć, stosując <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Domyślnie wszystkie typy publiczne i elementy członkowskie są widoczne.  
  
-   Typy muszą mieć publicznego konstruktora domyślnego aktywacji z modelu COM.  
  
     Typy zarządzane, publiczne są widoczne dla modelu COM. Jednak bez publicznego konstruktora domyślnego (Konstruktor bez argumentów), klienci COM nie można utworzyć typu. Klienci COM można nadal używać typu, jeśli jest aktywna w inny sposób.  
  
-   Typy nie może być abstrakcyjna.  
  
     Klienci COM ani klientów programu .NET nie można utworzyć typów abstrakcyjnych.  
  
 Podczas eksportowania dla modelu COM, jest spłaszczany hierarchii dziedziczenia typu zarządzanego. Przechowywanie wersji różni się między środowiskami zarządzanych i niezarządzanych. Typy widoczne dla modelu COM nie mają takie same charakterystyki przechowywania wersji, jak inne zarządzane typy.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Udostępnianie składników .NET Framework modelowi COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface)
- [Stosowanie atrybutów międzyoperacyjności](../../../docs/framework/interop/applying-interop-attributes.md)
- [Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
