---
title: Pakowanie zestawu dla modelu COM
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
ms.openlocfilehash: fdbbc169999a9faa2ac1c33c8573e51b76899b74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975172"
---
# <a name="packaging-an-assembly-for-com"></a>Pakowanie zestawu dla modelu COM

COM, deweloperzy mogą korzystać z następujące informacje na temat typów zarządzanych, ich planowanie, które należy uwzględnić w swoich aplikacji:

- Lista typów, które mogą używać aplikacje COM

  Niektóre typy zarządzane są niewidoczne dla modelu COM; Niektóre z nich są widoczne, ale nie jest możliwość utworzenia; a niektóre są widoczne i możliwe do utworzenia. Zestaw może zawierać dowolną kombinację typów niewidoczna, nie możliwe do utworzenia, przejrzyste i możliwe do utworzenia. Aby informacje były kompletne identyfikacji typów w zestawie, który chcesz udostępnić w COM, szczególnie w przypadku, gdy te typy są podzbiorem typy widoczne dla programu .NET Framework.

  Aby uzyskać więcej informacji, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md).

- Instrukcje obsługi wersji

  Klasy zarządzane, które implementują interfejs klasy (generowany międzyoperacyjności interfejsu COM) podlegają przechowywanie wersji ograniczenia.

  Aby uzyskać wskazówki na temat korzystania z interfejsu klasy, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).

- Instrukcje dotyczące wdrażania

  Zestawy o silnych nazwach, które są podpisane przez wydawcę, można zainstalować w globalnej pamięci podręcznej. Zestawy nieoznaczone musi być zainstalowany na komputerze użytkownika jako zestawy prywatne.

  Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md).

- Włączenie biblioteki typów

  Większość typów wymagają bibliotekę typów, gdy jest używane przez aplikacji modelu COM. Możesz wygenerować bibliotekę typów lub masz deweloperów COM wykonania tego zadania. [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia następujące opcje podczas generowania biblioteki typów:

  - [Eksporter biblioteki typów](#cpconpackagingassemblyforcomanchor1)

  - [Typelibconverter — klasa](#cpconpackagingassemblyforcomanchor2)

  - [Narzędzie rejestracji zestawów](#cpconpackagingassemblyforcomanchor3)

  - [Narzędzie instalacji usług .NET](#cpconpackagingassemblyforcomanchor4)

  Niezależnie od wybranego mechanizmu tylko typy publiczne zdefiniowane w zestawie, który podasz znajdują się w wygenerowanej biblioteki typów.

  Można bibliotekę typów w osobnym pliku pakietu lub osadzenie go jako plik zasobów Win32 w ciągu. Aplikacja oparta na sieci. Microsoft Visual Basic 6.0 wykonać to zadanie dla Ciebie automatycznie. Jednakże korzystając z [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], należy ręcznie osadzić biblioteki typów. Aby uzyskać instrukcje, zobacz [jak: Osadzanie bibliotek typu jako zasobów Win32 w. Aplikacje oparte na NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Eksporter biblioteki typów

[Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) jest narzędziem wiersza polecenia, który konwertuje klasy i interfejsy, które są zawarte w zestawie do biblioteki typów COM. Po udostępnieniu informacji o typie klasy klientów modelu COM można utworzyć wystąpienia klasy .NET i wywołać metodę wystąpienia, tak, jakby był to obiekt COM. Tlbexp.exe konwertuje cały zespół w tym samym czasie. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>Typelibconverter — klasa

<xref:System.Runtime.InteropServices.TypeLibConverter> Klasy, z siedzibą na terenie **System.Runtime.Interop** konwertuje przestrzeni nazw, klasy i interfejsy, które są zawarte w zestawie do biblioteki typów COM. Ten interfejs API zapewnia te same informacje o typie, eksporter biblioteki typów, opisanych w poprzedniej sekcji.

**Typelibconverter — klasa** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Narzędzie rejestracji zestawów

[Narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) można wygenerować i zarejestrować bibliotekę typów, po zastosowaniu **/TLB:** opcji. Klienci COM wymagają zainstalowania biblioteki typów w rejestrze systemu Windows. Bez tej opcji Regasm.exe rejestruje typy tylko w zestawie nie biblioteki typów. Rejestrowanie typów w zestawie i rejestrowania biblioteki typów są różne działania.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>Narzędzie instalacji usług .NET

[Narzędzie instalacji usług .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje klas zarządzanych do usługi składników systemu Windows 2000 i łączy kilka zadań w ramach jednego narzędzia. Oprócz ładowania i zarejestrowaniu zestawu, Regsvcs.exe wygenerować, rejestrowanie i zainstalować biblioteki typów do istniejącej aplikacji COM + 1.0.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md)
- [Wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface)
- [Zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md)
- [Tlbexp.exe (eksporter biblioteki typów)](../tools/tlbexp-exe-type-library-exporter.md)
- [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)
- [Instrukcje: Osadzanie bibliotek typu jako zasobów Win32 w aplikacjach](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
