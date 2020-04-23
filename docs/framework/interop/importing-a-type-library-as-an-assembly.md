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
ms.openlocfilehash: e1a21175bcabc72b86a328d4f73ecec37140c304
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107595"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Importowanie biblioteki typów jako zestawu

Definicje typu COM zwykle znajdują się w bibliotece typów. Z kolei kompilatory zgodne ze specyfikacją CLS generują metadane typu w zestawie. Dwa źródła informacji o typie są zupełnie inne. W tym temacie opisano techniki generowania metadanych z biblioteki typów. Zestaw, który jest nazywany zestawem międzyoperacyjnym, i zawarte w nim informacje o typie umożliwiają aplikacjom .NET Framework korzystanie z typów COM.

Istnieją dwa sposoby, aby te informacje o typie były dostępne dla aplikacji:

- Przy użyciu zestawów międzyoperacyjnych tylko do projektowania: począwszy od .NET Framework 4, można wydać kompilatorowi możliwość osadzenia informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego. Kompilator osadza tylko informacje o typie używane przez aplikację. Nie trzeba wdrażać zestawu międzyoperacyjnego przy użyciu aplikacji. Jest to zalecana technika.

- Wdrażanie zestawów międzyoperacyjnych: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego. W takim przypadku zestaw międzyoperacyjny musi zostać wdrożony wraz z aplikacją. Jeśli ta technika jest stosowana i nie używasz prywatnego składnika COM, zawsze odwołuje się do podstawowego zestawu międzyoperacyjnego (PIA) opublikowanego przez autora składnika COM, który ma zostać dołączony do kodu zarządzanego. Aby uzyskać więcej informacji na temat tworzenia i używania podstawowych zestawów międzyoperacyjnych, zobacz [podstawowe zestawy międzyoperacyjności](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

W przypadku korzystania z zestawów międzyoperacyjnych tylko do projektowania można osadzić informacje o typie z podstawowego zestawu międzyoperacyjnego opublikowanego przez autora składnika modelu COM. Nie trzeba jednak wdrażać podstawowego zestawu międzyoperacyjnego przy użyciu aplikacji.

Używanie zestawów międzyoperacyjnych tylko do projektowania zmniejsza rozmiar aplikacji, ponieważ większość aplikacji nie korzysta ze wszystkich funkcji składnika COM. Kompilator jest bardzo wydajny, gdy osadza informacje o typie; Jeśli aplikacja używa tylko niektórych metod w interfejsie COM, kompilator nie osadza nieużywanych metod. Gdy aplikacja zawierająca informacje o typie osadzonym współdziała z inną aplikacją lub współdziała z aplikacją, która używa podstawowego zestawu międzyoperacyjnego, środowisko uruchomieniowe języka wspólnego używa reguł równoważności typów do określenia, czy dwa typy o takiej samej nazwie reprezentują ten sam typ COM. Nie trzeba znać tych reguł, aby używać obiektów COM. Jednak jeśli interesuje Cię reguły, zobacz [typ równoważności i osadzone typy międzyoperacyjnych](type-equivalence-and-embedded-interop-types.md).

## <a name="generating-metadata"></a>Generowanie metadanych

Biblioteki typu COM mogą być autonomicznymi plikami, które mają rozszerzenie. tlb, takie jak LOANLib. tlb. Niektóre biblioteki typów są osadzone w sekcji zasobów pliku DLL lub exe. Inne źródła informacji o bibliotece typów to. olb i. ocx.

Po znalezieniu biblioteki typów, która zawiera implementację docelowego typu COM, dostępne są następujące opcje generowania zestawu międzyoperacyjnego zawierającego metadane typu:

- Visual Studio

  Program Visual Studio automatycznie konwertuje typy COM w bibliotece typów na metadane w zestawie. Aby uzyskać instrukcje, zobacz [How to: Add References to Library Type](how-to-add-references-to-type-libraries.md)librarys.

- [Importer biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md)

  Importer biblioteki typów zawiera opcje wiersza polecenia służące do dostosowywania metadanych w wyniku pliku międzyoperacyjnego, importuje typy z istniejącej biblioteki typów i generuje zestaw międzyoperacyjny i przestrzeń nazw. Aby uzyskać instrukcje, zobacz [How to: Generate zestawy międzyoperacyjności z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).

- Klasa <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType>

  Ta klasa dostarcza metody do konwertowania klas i interfejsów w bibliotece typów na metadane w ramach zestawu. Generuje te same dane wyjściowe metadanych, co Tlbimp. exe. Jednak, w przeciwieństwie do Tlbimp. exe <xref:System.Runtime.InteropServices.TypeLibConverter> , Klasa może skonwertować bibliotekę typów w pamięci na metadane.

- Otoki niestandardowe

  Gdy biblioteka typów jest niedostępna lub nieprawidłowa, jedną z opcji jest utworzenie zduplikowanej definicji klasy lub interfejsu w zarządzanym kodzie źródłowym. Następnie można skompilować kod źródłowy z kompilatorem przeznaczonym dla środowiska uruchomieniowego w celu utworzenia metadanych w zestawie.

  Aby ręcznie zdefiniować typy COM, musisz mieć dostęp do następujących elementów:

  - Precyzyjne opisy klas i interfejsów, które są definiowane.

  - Kompilator, taki jak kompilator języka C#, który może generować odpowiednie definicje klas .NET Framework.

  - Znajomość reguł konwersji typu "Biblioteka na zestaw".

  Pisanie otoki niestandardowej jest zaawansowaną techniką. Aby uzyskać dodatkowe informacje na temat sposobu generowania otoki niestandardowej, zobacz [Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).

 Aby uzyskać więcej informacji na temat procesu importowania międzyoperacyjności modelu COM, zobacz [Podsumowanie konwersji typu Biblioteka na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [Udostępnianie składników COM programowi.NET Framework](exposing-com-components.md)
- [Podsumowanie dotyczące konwersji biblioteki typów na zestaw](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp. exe (Importer biblioteki typów)](../tools/tlbimp-exe-type-library-importer.md)
- [Dostosowywanie otok standardowych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Używanie typów COM w kodzie zarządzanym](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Kompilowanie projektu międzyoperacyjnego](compiling-an-interop-project.md)
- [Wdrażanie aplikacji międzyoperacyjnych](deploying-an-interop-application.md)
- [Porady: dodawanie odwołań do bibliotek typów](how-to-add-references-to-type-libraries.md)
- [Porada: generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md)
