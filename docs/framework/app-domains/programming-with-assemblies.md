---
title: Programowanie za pomocą zestawów
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], programming
- programming assemblies
ms.assetid: 25918b15-701d-42c7-95fc-c290d08648d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6a20a2e678c10157fed7da6f5de9f3ffee0c9ad
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751873"
---
# <a name="programming-with-assemblies"></a>Programowanie za pomocą zestawów
Zestawy są blokami konstrukcyjnymi programu .NET Framework; stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnienia zabezpieczeń. Zestaw zawiera środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji. Jest kolekcją typów i zasobów, które są przeznaczone do współpracują ze sobą i utworzenia jednostki logicznej funkcji. Do środowiska wykonawczego typ nie istnieje poza kontekstem zestawu.  
  
 Ta sekcja zawiera opis sposobu tworzenia modułów, tworzenie zestawów z modułów utworzyć pary kluczy i podpisać zestaw o silnej nazwie i Instalowanie zestawu w globalnej pamięci podręcznej zestawów. Ponadto w tej sekcji opisano sposób użycia [dezasembler MSIL (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania informacji manifestu zestawu.  
  
> [!NOTE]
>  W programie .NET Framework w wersji 2.0, środowisko uruchomieniowe nie zostanie załadowany zestaw, który został skompilowany przy użyciu wersji programu .NET Framework, która ma wyższy numer wersji niż aktualnie załadowany. Dotyczy to kombinacja główne i pomocnicze składniki numeru wersji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 Zawiera omówienie zestawy jednoplikowe i wiele plików.  
  
 [Nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md)  
 Omówienie zestawu nazewnictwa.  
  
 [Instrukcje: określanie w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 Opisuje sposób ustalić w pełni kwalifikowana nazwa zestawu.  
  
 [Uruchamianie aplikacji intranetowych w trybie pełnego zaufania](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Opisuje sposób określenia zasady zabezpieczeń starsze dla zestawów pełnego zaufania w udziale sieci intranet.  
  
 [Lokalizacja zestawu](../../../docs/framework/app-domains/assembly-location.md)  
 Zawiera omówienie gdzie umieścić zestawy.  
  
 [Instrukcje: kompilacja zestawu jednoplikowego](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 Opisuje sposób tworzenia zestawu pojedynczego pliku.  
  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)  
 W tym artykule opisano powodów tworzenia zestawy wieloplikowe.  
  
 [Instrukcje: kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 Opisuje sposób tworzenia zestawów wieloplikowych.  
  
 [Ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Zawiera opis atrybutów zestawu i sposobu ich ustawiania.  
  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 W tym artykule opisano, jak i dlaczego podpisać zestaw o silnej nazwie i zawiera tematy porad.  
  
 [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 Opisuje sposób Podpisz zestaw opóźnieniem.  
  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 W tym artykule opisano, jak i dlaczego dodawania zestawów do globalnej pamięci podręcznej zestawów i zawiera tematy porad.  
  
 [Instrukcje: wyświetlanie zawartości zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Informacje dotyczące używania dezasembler MSIL (Ildasm.exe), aby wyświetlić zawartość zestawu.  
  
 [Przekazywanie dalej typu w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Opisuje sposób umożliwia przekazywanie dalej typu przenosić typu w innym zestawie bez przerywania istniejących aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly>  
 Klasa .NET Framework, która reprezentuje zestaw.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: uzyskiwanie informacji dotyczących typów i elementów członkowskich z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 Opisuje sposób programowego uzyskać inne informacje dotyczące typu i z zestawu.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie języka wspólnego zestawy środowiska wykonawczego.  
  
 [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)  
 Omówienie powiązań zestawów i z <xref:System.Reflection.AssemblyVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybutów.  
  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 W tym artykule opisano, jak środowisko uruchomieniowe Określa, które zestawu do używania w celu spełnienia żądania powiązania.  
  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Informacje dotyczące używania **odbicia** klasę, aby uzyskać informacje o zestawie.
