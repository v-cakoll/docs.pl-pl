---
title: Importowanie biblioteki typów jako zestawu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0299ef58d58318714b8f0eb8082928f8da565d2f
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="importing-a-type-library-as-an-assembly"></a>Importowanie biblioteki typów jako zestawu
Definicje typów COM zazwyczaj znajdują się w bibliotece typów. Z kolei kompilatory zgodne ze specyfikacją CLS utworzyć metadanych typów w zestawie. Dwóch źródeł informacji o typie znacznie różnią się. W tym temacie opisano metody generowania metadanych z biblioteki typów. Wynikowy zestaw nosi nazwę zestawu międzyoperacyjnego i informacji o typie, który zawiera umożliwia używanie typów COM aplikacji .NET Framework.  
  
 Istnieją dwa sposoby, aby udostępnić informacje tego typu aplikacji:  
  
-   Przy użyciu projektu tylko od czasu zestawy międzyoperacyjne: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Kompilator osadza informacje typu, używanych przez aplikację. Nie trzeba wdrażać zestawu międzyoperacyjnego z aplikacją. Jest to zalecana technika.  
  
-   Zestawy międzyoperacyjne wdrażania: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku należy wdrożyć zestawu międzyoperacyjnego z aplikacją. Jeśli zostanie zastosowana ta technika, a nie jest używany prywatny składnika modelu COM, zawsze odwoływać się do podstawowego zestawu międzyoperacyjnego (PIA) opublikowane przez autora składnika modelu COM, który chcesz uwzględnić w kodzie zarządzanym. Aby uzyskać więcej informacji na temat Tworzenie i używanie podstawowe zestawy międzyoperacyjne zobacz [podstawowe zestawy międzyoperacyjne](https://msdn.microsoft.com/library/b977a8be-59a0-40a0-a806-b11ffba5c080(v=vs.100)).  
  
 Gdy używasz projektu tylko od czasu zestawy międzyoperacyjne można osadzić informacji o typie z podstawowego zestawu międzyoperacyjnego opublikowane przez autora składnika modelu COM. Jednak nie musisz wdrażać podstawowego zestawu międzyoperacyjnego z aplikacją.  
  
 Przy użyciu projektu tylko od czasu zestawy międzyoperacyjne zmniejsza rozmiar aplikacji, ponieważ większość aplikacji należy używać wszystkich funkcji składnika modelu COM. Kompilator jest bardzo wydajny, gdy ją osadza informacje o typie; Jeśli aplikacja używa pewnych metod w interfejsie COM, kompilator nie można osadzić nieużywane metody. Gdy aplikacja, która zawiera osadzone informacji o typie współdziała z innej takich aplikacji lub współdziała z aplikacją, która używa podstawowego zestawu międzyoperacyjnego, wspólne używa środowiska wykonawczego języka wpisz równoważność zasady w celu ustalenia, czy dwa typy z tej samej nazwy reprezentują ten sam typ COM. Nie trzeba znać obiektów COM tych reguł. Jednak jeśli interesuje Cię w zasadach, zobacz [równoważność typów i osadzone typy międzyoperacyjne](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md).  
  
## <a name="generating-metadata"></a>Generowanie metadanych  
 Biblioteki typów COM może być autonomicznym pliki, które mają rozszerzenie .tlb, takich jak Loanlib.tlb. Niektóre biblioteki typów są osadzone w sekcji zasobów w pliku .dll lub .exe. Inne źródła informacji o typie biblioteki są plikami .olb i .ocx.  
  
 Po zlokalizowaniu bibliotekę typu, która zawiera implementację docelowego typu COM, masz następujące opcje generowania zestawu międzyoperacyjnego zawierający metadane typu:  
  
-   Visual Studio  
  
     Visual Studio automatycznie konwertuje typów COM w bibliotece typów metadanych w zestawie. Aby uzyskać instrukcje, zobacz [porady: Dodawanie odwołania do bibliotek typów](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md) i [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100)).  
  
-   [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     Importer biblioteki typów udostępnia opcje wiersza polecenia, aby dopasować metadanych w wynikowym pliku międzyoperacyjnego, importuje typy z istniejącej biblioteki typów, a następnie generuje zestawu międzyoperacyjnego i przestrzeni nazw. Aby uzyskać instrukcje, zobacz [porady: generowanie zestawy międzyoperacyjne z bibliotek typów](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md).  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> Klasy  
  
     Ta klasa dostarcza metody do przekonwertowania klasy coclass i interfejsy w bibliotece typów do metadanych w zestawie. Tworzy tych samych danych wyjściowych metadanych jako Tlbimp.exe. Jednak w przeciwieństwie do Tlbimp.exe <xref:System.Runtime.InteropServices.TypeLibConverter> klasy można skonwertować biblioteki typów w pamięci na metadanych.  
  
-   Otoki niestandardowe  
  
     Gdy biblioteki typów jest niedostępny lub nieprawidłowy, co rozwiązaniem jest utworzenie zduplikowanych definicji klasy lub interfejsu w kodzie źródłowym zarządzanych. Następnie kompilacja kodu źródłowego z kompilatorem, przeznaczonego dla środowiska uruchomieniowego do utworzenia metadanych w zestawie.  
  
     Aby ręcznie zdefiniować typy dla modelu COM, musi mieć dostęp do następujących elementów:  
  
    -   Dokładne opisy klasy coclass i interfejsy definiowanego.  
  
    -   Kompilator, takich jak C# kompilator, generowany odpowiednie definicje klas .NET Framework.  
  
    -   Znajomość reguły biblioteki do zestawu konwersji typu.  
  
     Pisanie niestandardowych otoki jest zaawansowanych technik. Aby uzyskać dodatkowe informacje na temat generowania otoki niestandardowe, zobacz [dostosowywanie standardowych otoki](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100)).  
  
 Aby uzyskać więcej informacji na temat procesu importowania międzyoperacyjnego COM zobacz [biblioteki typów na zestaw konwersja — Podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 [Udostępnianie składników COM programowi .NET Framework](../../../docs/framework/interop/exposing-com-components.md)  
 [Biblioteki typów na zestaw konwersja — podsumowanie](https://msdn.microsoft.com/library/bf3f90c5-4770-4ab8-895c-3ba1055cc958(v=vs.100))  
 [Tlbimp.exe (importer biblioteki typów)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [Dostosowywanie standardowych otoki](https://msdn.microsoft.com/library/c40d089b-6a3c-41b5-a20d-d760c215e49d(v=vs.100))  
 [Używanie typów COM w kodzie zarządzanym](https://msdn.microsoft.com/library/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66(v=vs.100))  
 [Kompilowanie projektu międzyoperacyjnego](../../../docs/framework/interop/compiling-an-interop-project.md)  
 [Wdrażanie aplikacji międzyoperacyjnych](../../../docs/framework/interop/deploying-an-interop-application.md)  
 [Instrukcje: Dodawanie odwołań do bibliotek typów](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)  
 [Instrukcje: Generowanie zestawów międzyoperacyjnych z bibliotek typów](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)  
 [Przewodnik: osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))
