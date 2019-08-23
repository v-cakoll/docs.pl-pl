---
title: Programowanie za pomocą zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f427e2260fb26be7db0a29c47f38a3cb32dd34e9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921430"
---
# <a name="programming-with-assemblies"></a>Programowanie za pomocą zestawów
Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń. Zestaw udostępnia środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów. Jest to Kolekcja typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności. Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.  
  
 W tej sekcji opisano sposób tworzenia modułów, tworzenia zestawów z modułów, tworzenia pary kluczy i podpisywania zestawu o silnej nazwie, a następnie instalowania zestawu w globalnej pamięci podręcznej zestawów. Ponadto w tej sekcji opisano sposób używania [Dezasembler MSIL (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.  
  
> [!NOTE]
> Począwszy od .NET Framework w wersji 2,0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji .NET Framework, która ma wyższy numer wersji niż aktualnie załadowane środowisko uruchomieniowe. Dotyczy to kombinacji głównych i pomocniczych składników numeru wersji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 Zawiera omówienie zestawów jednoplikowych i wieloplikowych.  
  
 [Nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md)  
 Zawiera omówienie nazewnictwa zestawów.  
  
 [Instrukcje: Określanie w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Opisuje sposób określania w pełni kwalifikowanej nazwy zestawu.  
  
 [Uruchamianie aplikacji intranetowych w trybie pełnego zaufania](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Opisuje sposób określania starszych zasad zabezpieczeń dla zestawów pełnego zaufania w udziale intranetowym.  
  
 [Lokalizacja zestawu](../../../docs/framework/app-domains/assembly-location.md)  
 Zawiera omówienie lokalizacji lokalizowania zestawów.  
  
 [Instrukcje: Kompilowanie zestawu jednoplikowego](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Opisuje sposób tworzenia zestawu jednoplikowego.  
  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)  
 Opisuje przyczyny tworzenia zestawów wieloplikowych.  
  
 [Instrukcje: Kompilowanie zestawu wieloplikowego](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Opisuje sposób tworzenia zestawu wieloplikowego.  
  
 [Ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Opisuje atrybuty zestawu i sposób ich ustawiania.  
  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 Opisuje, jak i dlaczego podpisać zestaw za pomocą silnej nazwy i zawiera tematy porad.  
  
 [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Opisuje, jak opóźnić podpisywanie zestawu.  
  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 Opisuje, jak i dlaczego należy dodać zestawy do globalnej pamięci podręcznej zestawów i zawiera tematy porad.  
  
 [Instrukcje: Wyświetl zawartość zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Opisuje sposób używania Dezasembler MSIL (Ildasm. exe) do wyświetlania zawartości zestawu.  
  
 [Przekazywanie dalej typu w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Opisuje, jak używać przekazywania typów do przenoszenia typu do innego zestawu bez przerywania istniejących aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly>  
 Klasa .NET Framework, która reprezentuje zestaw.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Uzyskiwanie informacji o typie i elemencie członkowskim z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Opisuje, w jaki sposób programowo uzyskać typ i inne informacje z zestawu.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie pojęć dotyczących zestawów środowiska uruchomieniowego języka wspólnego.  
  
 [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)  
 Zawiera omówienie powiązań zestawów i <xref:System.Reflection.AssemblyVersionAttribute> atrybutów i. <xref:System.Reflection.AssemblyInformationalVersionAttribute>  
  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 Opisuje, jak środowisko uruchomieniowe określa, który zestaw ma być używany do realizacji żądania powiązania.  
  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób użycia klasy **odbicia** w celu uzyskania informacji o zestawie.
