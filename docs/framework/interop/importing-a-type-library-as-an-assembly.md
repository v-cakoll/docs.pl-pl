---
title: Importowanie biblioteki typów jako zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4104ddba1942f9cb9bd860d53dc54968de5af891
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151271"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Importowanie biblioteki typów jako zestawu
Definicje typów modelu COM zazwyczaj znajdują się w bibliotece typów. Z kolei zgodne ze specyfikacją CLS kompilatory generuje metadanych typu w zestawie. Dwa źródła informacji o typie są zupełnie inny. W tym temacie opisano techniki do generowania metadanych z biblioteki typów. Wynikowy zestaw nosi nazwę zestawu międzyoperacyjnego i zawartych w nim informacje o typie umożliwia używanie typów modelu COM aplikacji .NET Framework.  
  
 Istnieją dwa sposoby, aby udostępnić te informacje typu aplikacji:  
  
-   Korzystanie z projektowania czas — tylko do zestawów międzyoperacyjnych: Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można nakazać kompilatorowi do osadzenia informacji o typie z zestawu międzyoperacyjnego w programie wykonywalnym. Kompilator osadza tylko informacje o typie, używanych przez aplikację. Nie masz do wdrożenia zestawu międzyoperacyjnego z aplikacją. Jest to zalecana technika.  
  
-   Wdrażanie zestawów międzyoperacyjnych: Można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W tym przypadku zestaw międzyoperacyjny musi zostać wdrożony z aplikacją. Jeśli zostanie zastosowana ta technika, a nie jest używany prywatny składnika modelu COM, zawsze odwoływać się do podstawowego zestawu międzyoperacyjnego (PIA), opublikowana przez autora składnika modelu COM, który chcesz zastosować w kodzie zarządzanym. Aby uzyskać więcej informacji dotyczących tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjne](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).  
  
 Gdy używasz projektu czas — tylko do zestawów międzyoperacyjnych, możesz osadzić informacji o typie z podstawowego zestawu międzyoperacyjnego opublikowane przez autora składnika modelu COM. Jednakże nie musisz wdrażać podstawowego zestawu międzyoperacyjnego z aplikacją.  
  
 Za pomocą projektu czas — tylko do zestawów międzyoperacyjnych ogranicza rozmiar Twojej aplikacji, ponieważ większość aplikacji należy używać wszystkich funkcji wersji składnika modelu COM. Kompilator jest bardzo wydajny w przypadku, gdy ją osadza informacje o typie; Jeśli aplikacja używa tylko niektóre metody interfejsu COM, kompilator nie jest możliwe osadzanie nieużywane metody. Gdy aplikacja, która zawiera osadzone informacje o typie wchodzi w interakcje z innym tego typu aplikacji lub wchodzi w interakcję z aplikacją, która używa podstawowego zestawu międzyoperacyjnego, typowych zastosowań środowiska uruchomieniowego języka wpisz reguły równoważności w celu ustalenia, czy dwa typy z tej samej nazwie reprezentują ten sam typ COM. Nie trzeba znać te zasady, aby użyć obiektów COM. Jednak jeśli interesują Cię reguły, zobacz [równoważności typów i osadzone typy międzyoperacyjne](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Generowanie metadanych  
 Biblioteki typów COM mogą być autonomiczne pliki, które mają rozszerzenie .tlb, takich jak Loanlib.tlb. Niektóre biblioteki typów są osadzone w sekcji zasobów w pliku .dll lub .exe. Inne źródła informacji o typie biblioteki są plikami .olb i .ocx.  
  
 Po zlokalizowaniu biblioteki typów, zawierający implementację docelowy typ COM, masz następujące opcje podczas generowania zestawu międzyoperacyjnego, zawierający metadane typu:  
  
-   Visual Studio  
  
     Program Visual Studio automatycznie konwertuje typy modelu COM w bibliotece typów na metadanych w zestawie. Aby uzyskać instrukcje, zobacz [jak: Dodaj odwołania do bibliotek typów](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md).  
  
-   [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Importer biblioteki typów udostępnia opcje wiersza polecenia do Dostosuj metadane w powstałym pliku międzyoperacyjnych, importuje typy z istniejącej biblioteki typów, a następnie generuje zestaw międzyoperacyjny i przestrzeni nazw. Aby uzyskać instrukcje, zobacz [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> Klasa  
  
     Ta klasa dostarcza metody do przekonwertowania klasy coclass i interfejsy w bibliotece typów na metadane w zestawie. Generuje ten sam wynik metadanych jako Tlbimp.exe. Jednak w przeciwieństwie do Tlbimp.exe <xref:System.Runtime.InteropServices.TypeLibConverter> klasy można przekonwertować biblioteki typów w pamięci na metadanych.  
  
-   Otoki niestandardowe  
  
     Gdy biblioteki typów jest niedostępny lub nieprawidłowy, jednym rozwiązaniem jest utworzenie zduplikowaną definicję klasy lub interfejsu w zarządzanym kodzie źródłowym. Następnie skompilować kod źródłowy za pomocą kompilatora, który jest przeznaczony dla środowiska uruchomieniowego, aby wygenerować metadane w zestawie.  
  
     Aby ręcznie zdefiniować typy modelu COM, musi mieć dostęp do następujących elementów:  
  
    -   Dokładne opisy klasy coclass i interfejsy, które zostały zdefiniowane.  
  
    -   Kompilator, taki jak C# kompilatora, który można wygenerować odpowiedniego definicje klas .NET Framework.  
  
    -   Znajomość reguły konwersji biblioteki do zestawu typów.  
  
     Pisanie niestandardowej otoki jest zaawansowane techniki. Aby uzyskać dodatkowe informacje o tym, jak można wygenerować otokę niestandardową, zobacz [Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).  
  
 Aby uzyskać więcej informacji na temat procesu importowania międzyoperacyjnego modelu COM, zobacz [biblioteki typów na zestaw konwersja — Podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [Udostępnianie składników COM programowi .NET Framework](../../../docs/framework/interop/exposing-com-components.md)
- [Biblioteki typów na zestaw konwersja — podsumowanie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp.exe (importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)
- [Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Używanie typów modelu COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilowanie projektu międzyoperacyjnego](../../../docs/framework/interop/compiling-an-interop-project.md)
- [Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md)
- [Instrukcje: Dodaj odwołania do bibliotek typów](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)
- [Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)
