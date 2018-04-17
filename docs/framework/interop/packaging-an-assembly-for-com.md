---
title: Pakowanie zestawu dla modelu COM
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1e3ee38f98eae46c09ec2175f3c9af01288bd2
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="packaging-an-assembly-for-com"></a>Pakowanie zestawu dla modelu COM
COM deweloperzy mogą korzystać z następujące informacje o typach zarządzanych one ma włączenie w aplikacji:  
  
-   Lista typów, które mogą korzystać z aplikacji modelu COM  
  
     Niektóre typy zarządzane są widoczne dla modelu COM; Niektóre są widoczne, ale nie jest możliwość utworzenia; i niektóre są widoczne i możliwość utworzenia. Zestaw może obejmować dowolną kombinację typów niewidoczne, widoczne i nie tworzyć oraz możliwość utworzenia. Aby informacje były kompletne identyfikacji typów w zestawie, który ma zostać udostępniona modelowi COM, szczególnie w przypadku tych typów są podzbiorem typy widoczne dla programu .NET Framework.  
  
     Aby uzyskać dodatkowe informacje, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md).  
  
-   Instrukcje kontroli wersji  
  
     Klasy zarządzane, które implementują interfejs klasy (wygenerowany interop interfejsu COM) obowiązują ograniczenia wersji.  
  
     Aby uzyskać wskazówki na temat używania interfejsu klasy, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).  
  
-   Instrukcje dotyczące wdrażania  
  
     Zestawów o silnej nazwie, które są podpisane przez wydawcę może być zainstalowany w globalnej pamięci podręcznej zestawów. Zestawy nieoznaczone musi być zainstalowany na komputerze użytkownika jako zestawy prywatne.  
  
     Aby uzyskać dodatkowe informacje, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md).  
  
-   Włączenie biblioteki typów  
  
     Większość typów wymagają biblioteki typów, gdy używane przez aplikację COM. Można wygenerować biblioteki typów lub ma deweloperów COM wykonania tego zadania. [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia następujące opcje generowania biblioteki typów:  
  
    -   [Eksporter biblioteki typów](#cpconpackagingassemblyforcomanchor1)  
  
    -   [Typelibconverter — klasa](#cpconpackagingassemblyforcomanchor2)  
  
    -   [Assembly Registration — narzędzie](#cpconpackagingassemblyforcomanchor3)  
  
    -   [.NET services Installation — narzędzie](#cpconpackagingassemblyforcomanchor4)  
  
     Niezależnie od wybranego mechanizmu tylko typy publiczne zdefiniowane w zestawie, który podasz znajdują się w bibliotece typów wygenerowany.  
  
     Możesz biblioteki typów jako osobny plik pakietu lub osadzać go jako plik zasobów Win32 w. Aplikacja Asp.net. Microsoft Visual Basic 6.0 wykonać tego zadania można automatycznie; Jednak przy użyciu [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], należy ręcznie osadzić biblioteki typów. Aby uzyskać instrukcje, zobacz [porady: osadzanie biblioteki typów jako zasobów Win32 w. Aplikacje oparte na sieci](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a>Eksporter biblioteki typów  
 [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) to narzędzie wiersza polecenia, który konwertuje klasy i interfejsy zawarty w zestawie do biblioteki typów COM. Po udostępnieniu informacji o typie klasy, klientów modelu COM. można utworzyć wystąpienia klasy .NET i wywołanie metody wystąpienia, tak jakby był obiektem COM. Tlbexp.exe konwertuje cały zestaw w tym samym czasie. Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a>Typelibconverter — klasa  
 <xref:System.Runtime.InteropServices.TypeLibConverter> Klasa znajduje się w **System.Runtime.Interop** konwertuje przestrzeni nazw, klasy i interfejsy zawarty w zestawie do biblioteki typów COM. Ten interfejs API zapewnia te same informacje typu jako eksporter biblioteki typów opisanych w poprzedniej sekcji.  
  
 **Typelibconverter — klasa** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a>Assembly Registration — narzędzie  
 [Narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) można wygenerować i zarejestrować biblioteki typów, po zastosowaniu **/TLB:** opcji. Klienci COM wymagają zainstalowania bibliotek typów w rejestrze systemu Windows. Bez tej opcji Regasm.exe tylko rejestruje typów w zestawie nie biblioteki typów. Rejestrowanie typów w zestawie i rejestrowania biblioteki typów są różne działania.  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a>.NET services Installation — narzędzie  
 [Narzędzie instalacji usług .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje do usługi składnika systemu Windows 2000 zarządzanej klasy i łączy kilka zadań w ramach jednego narzędzia. Oprócz ładowania i rejestrowanie zestawu, Regsvcs.exe można wygenerować, zarejestrować, a następnie zainstaluj bibliotekę typów do istniejącej aplikacji COM + 1.0.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
 [Kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md)  
 [Wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface)  
 [Zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md)  
 [Tlbexp.exe (eksporter biblioteki typów)](../tools/tlbexp-exe-type-library-exporter.md)  
 [Rejestrowanie zestawów do użycia z modelem COM](registering-assemblies-with-com.md)  
 [Porady: osadzanie biblioteki typów jako zasobów Win32 w aplikacjach](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))
