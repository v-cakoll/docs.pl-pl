---
title: Program z zestawami
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03babe701b46eab54a76094c4728af80e6d9911e
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973139"
---
# <a name="program-with-assemblies"></a>Program z zestawami
Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń. Zestaw udostępnia środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów. Jest to Kolekcja typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności. Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.  
  
 W tej sekcji opisano sposób tworzenia modułów, tworzenia zestawów z modułów, tworzenia pary kluczy i podpisywania zestawu o silnej nazwie, a następnie instalowania zestawu w globalnej pamięci podręcznej zestawów. Ponadto w tej sekcji opisano sposób używania [Dezasembler MSIL (Ildasm. exe)](../../framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.  
  
> [!NOTE]
> Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe. Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie zestawów](create.md)  
 Zawiera omówienie zestawów jednoplikowych i wieloplikowych.  
  
 [Nazwy zestawów](names.md)  
 Zawiera omówienie nazewnictwa zestawów.  
  
 [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](find-fully-qualified-name.md)  
 Opisuje sposób określania w pełni kwalifikowanej nazwy zestawu.  
  
 [Uruchamianie aplikacji intranetowych w trybie pełnego zaufania](../../framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Opisuje sposób określania starszych zasad zabezpieczeń dla zestawów pełnego zaufania w udziale intranetowym.  
  
 [Lokalizacja zestawu](location.md)  
 Zawiera omówienie lokalizacji lokalizowania zestawów.  
  
 [Instrukcje: Kompilowanie zestawu jednoplikowego](../../framework/app-domains/build-single-file-assembly.md)  
 Opisuje sposób tworzenia zestawu jednoplikowego.  
  
 [Zestawy wieloplikowe](../../framework/app-domains/multifile-assemblies.md)  
 Opisuje przyczyny tworzenia zestawów wieloplikowych.  
  
 [Instrukcje: Kompilowanie zestawu wieloplikowego](../../framework/app-domains/build-multifile-assembly.md)  
 Opisuje sposób tworzenia zestawu wieloplikowego.  
  
 [Ustawianie atrybutów zestawu](set-attributes.md)  
 Opisuje atrybuty zestawu i sposób ich ustawiania.  
  
 [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md)  
 Opisuje, jak i dlaczego podpisać zestaw za pomocą silnej nazwy i zawiera tematy porad.  
  
 [Opóźnij podpisanie zestawu](delay-sign.md)  
 Opisuje, jak opóźnić podpisywanie zestawu.  
  
 [Pracuj z zestawami i globalną pamięcią podręczną zestawów](../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Opisuje, jak i dlaczego należy dodać zestawy do globalnej pamięci podręcznej zestawów i zawiera tematy porad.  
  
 [Instrukcje: Wyświetl zawartość zestawu](view-contents.md)  
 Opisuje sposób używania Dezasembler MSIL (Ildasm. exe) do wyświetlania zawartości zestawu.  
  
 [Przekazywanie typu w środowisku uruchomieniowym języka wspólnego](type-forwarding.md)  
 Opisuje, jak używać przekazywania typów do przenoszenia typu do innego zestawu bez przerywania istniejących aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly>  
 Klasa .NET Framework, która reprezentuje zestaw.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim z zestawu](../../framework/reflection-and-codedom/get-type-member-information.md)  
 Opisuje, w jaki sposób programowo uzyskać typ i inne informacje z zestawu.  
  
 [Zestawy w środowisku .NET](index.md)  
 Zawiera omówienie pojęć dotyczących zestawów środowiska uruchomieniowego języka wspólnego.  
  
 [Przechowywanie wersji zestawu](versioning.md)  
 Zawiera omówienie powiązań zestawów i <xref:System.Reflection.AssemblyVersionAttribute> atrybutów i. <xref:System.Reflection.AssemblyInformationalVersionAttribute>  
  
 [Jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)  
 Opisuje, jak środowisko uruchomieniowe określa, który zestaw ma być używany do realizacji żądania powiązania.  
  
 [Powiela](../../framework/reflection-and-codedom/reflection.md)   
 Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
