---
title: Pakowanie zestawu .NET Framework dla modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11777f21d34da8b529352122bbf185f1938d3eb5
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567230"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a>Pakowanie zestawu .NET Framework dla modelu COM

Deweloperzy COM mogą skorzystać z następujących informacji o zarządzanych typach, które mają zostać dołączone do swojej aplikacji:

- Lista typów, których mogą używać aplikacje COM

  Niektóre typy zarządzane są niewidoczne dla modelu COM. Niektóre są widoczne, ale nie mogą być możliwe do utworzenia; a niektóre są widoczne i możliwe do utworzenia. Zestaw może składać się z dowolnej kombinacji typów niewidocznych, widocznych, niemożliwych do utworzenia i do utworzenia. Aby uzyskać kompletność, zidentyfikuj typy w zestawie, które zamierzasz uwidocznić dla modelu COM, zwłaszcza gdy te typy są podzbiorem typów ujawnionych dla .NET Framework.

  Aby uzyskać dodatkowe informacje, zobacz [kwalifikowanie typów .NET do](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)międzyoperacyjności.

- Instrukcje dotyczące obsługi wersji

  Klasy zarządzane implementujące interfejs klasy (interfejs oparty na modelu COM Interop) podlegają ograniczeniom dotyczącym wersji.

  Aby uzyskać wskazówki dotyczące używania interfejsu klasy, zobacz [wprowadzenie do interfejsu klasy](../../../docs/standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).

- Instrukcje dotyczące wdrażania

  Zestawy o silnych nazwach, które są podpisane przez wydawcę, można zainstalować w globalnej pamięci podręcznej zestawów. Zestawy bez znaku muszą być zainstalowane na komputerze użytkownika jako prywatne zespoły.

  Aby uzyskać dodatkowe informacje, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md).

- Dołączanie biblioteki typów

  Większość typów wymaga biblioteki typów, gdy jest używana przez aplikację COM. Można wygenerować bibliotekę typów lub mieć deweloperów COM wykonujących to zadanie. Windows SDK udostępnia następujące opcje generowania biblioteki typów:

  - [Eksporter biblioteki typów](#cpconpackagingassemblyforcomanchor1)

  - [Klasa TypeLibConverter](#cpconpackagingassemblyforcomanchor2)

  - [Narzędzie rejestracji zestawów](#cpconpackagingassemblyforcomanchor3)

  - [Narzędzie instalacji usług .NET](#cpconpackagingassemblyforcomanchor4)

  Niezależnie od wybranego mechanizmu, tylko typy publiczne zdefiniowane w zestawie, które dostarczasz, są uwzględniane w wygenerowanej bibliotece typów.

Aby uzyskać instrukcje, [zobacz How to: Osadź biblioteki typów jako zasoby Win32 w. Aplikacje](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))oparte na sieci.

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Eksporter biblioteki typów

[Eksporter biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) jest narzędziem wiersza polecenia, które konwertuje klasy i interfejsy zawarte w zestawie do biblioteki typów com. Po udostępnieniu informacji o typie klasy klienci COM mogą utworzyć wystąpienie klasy .NET i wywoływać metody tego wystąpienia, tak jakby był to obiekt COM. Tlbexp. exe konwertuje cały zestaw jednocześnie. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>Klasa TypeLibConverter

Klasa znajdująca się w przestrzeni nazw **System. Runtime. Interop** konwertuje klasy i interfejsy zawarte w zestawie na bibliotekę typów com. <xref:System.Runtime.InteropServices.TypeLibConverter> Ten interfejs API tworzy takie same informacje o typie, jak Eksporter biblioteki typów, opisany w poprzedniej sekcji.

**Klasa TypeLibConverter** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Narzędzie rejestracji zestawów

[Narzędzie do rejestracji zestawu (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) może generować i rejestrować biblioteki typów podczas stosowania opcji **/tlb:** . Klienci COM wymagają, aby biblioteki typów były zainstalowane w rejestrze systemu Windows. Bez tej opcji Regasm. exe rejestruje typy w zestawie, a nie w bibliotece typów. Rejestrowanie typów w zestawie i rejestrowanie biblioteki typów to odrębne działania.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>Narzędzie instalacji usług .NET

[Narzędzie instalacji usług .NET (Regsvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje klasy zarządzane do usług składowych systemu Windows 2000 i łączy kilka zadań w ramach jednego narzędzia. Oprócz ładowania i rejestrowania zestawu, Regsvcs. exe może generować, rejestrować i instalować bibliotekę typów w istniejącej aplikacji COM+ 1,0.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/standard/native-interop/qualify-net-types-for-interoperation.md)
- [Wprowadzenie do interfejsu klasy](../../../docs/standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [Zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../tools/tlbexp-exe-type-library-exporter.md)
- [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)
- [Instrukcje: Osadź biblioteki typów jako zasoby Win32 w aplikacjach](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
