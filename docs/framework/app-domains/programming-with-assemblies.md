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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705548"
---
# <a name="programming-with-assemblies"></a>Programowanie za pomocą zestawów
Zestawy są blokami konstrukcyjnymi .NET Framework; tworzą one podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń. Zestaw zawiera środowisko uruchomieniowe języka wspólnego informacje potrzebne do należy pamiętać o implementacji typu. Jest to kolekcja typów i zasobów, które zostały opracowane w celu współpracują ze sobą i tworzą jednostkę logiczną funkcji. Do środowiska uruchomieniowego typem nie istnieje poza kontekstem zestawu.  
  
 W tej sekcji opisano sposób tworzenia modułów, tworzenie zestawów z modułów, utworzyć parę kluczy i podpisać zestaw silną nazwą i Instalowanie zestawu w globalnej pamięci podręcznej. Ponadto w tej sekcji opisano sposób używania [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić dane manifestu zestawu.  
  
> [!NOTE]
>  Począwszy od programu .NET Framework w wersji 2.0 środowisko uruchomieniowe nie załaduje zestawu, który został skompilowany przy użyciu wersji programu .NET Framework, który ma wyższy numer wersji niż obecnie załadowanym środowiskiem uruchomieniowym. Dotyczy to kombinacja składniki główny i pomocniczy numer wersji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie zestawów](../../../docs/framework/app-domains/create-assemblies.md)  
 Zawiera omówienie pojedynczego pliku i wieloplikowe zestawy.  
  
 [Nazwy zestawów](../../../docs/framework/app-domains/assembly-names.md)  
 Omówienie zestawów nazewnictwa.  
  
 [Instrukcje: Określić w pełni kwalifikowanej nazwy zestawu](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)  
 W tym artykule opisano, jak określić w pełni kwalifikowana nazwa zestawu.  
  
 [Uruchamianie aplikacji intranetowych w trybie pełnego zaufania](../../../docs/framework/app-domains/running-intranet-applications-in-full-trust.md)  
 Opisuje sposób określania zasad zabezpieczeń w starszej wersji dla zestawów pełnego zaufania w udziale sieci intranet.  
  
 [Lokalizacja zestawu](../../../docs/framework/app-domains/assembly-location.md)  
 Zawiera omówienie gdzie umieścić zestawy.  
  
 [Instrukcje: Kompilacja zestawów pojedynczego pliku](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 W tym artykule opisano sposób tworzenia zestawu pojedynczego pliku.  
  
 [Zestawy wieloplikowe](../../../docs/framework/app-domains/multifile-assemblies.md)  
 W tym artykule opisano tworzenie zespołów wieloplikowych przyczyny.  
  
 [Instrukcje: Kompilacja zestawów wieloplikowych](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 W tym artykule opisano, jak utworzyć zestaw wieloplikowy.  
  
 [Ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 Zawiera opis atrybutów zestawu i sposobu ich ustawiania.  
  
 [Tworzenie i używanie zestawów o silnej nazwie](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 W tym artykule opisano, jak i dlaczego należy podpisać zestaw silną nazwą i zawiera tematy Pomocy.  
  
 [Opóźnione podpisywanie zestawu](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 W tym artykule opisano sposób Opóźnij podpisanie zestawu.  
  
 [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 W tym artykule opisano, jak i dlaczego dodawania zestawów do globalnej pamięci podręcznej i zawiera tematy Pomocy.  
  
 [Instrukcje: Wyświetlanie zawartości zestawu](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 Opisuje sposób używania MSIL Disassembler (Ildasm.exe), aby wyświetlić zawartość zestawu.  
  
 [Przekazywanie dalej typu w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/type-forwarding-in-the-common-language-runtime.md)  
 Opisuje sposób używania przekazywanie dalej typu na przeniesienie typu do innego zestawu bez przerywania istniejących aplikacji.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly>  
 Klasa .NET Framework, która reprezentuje zestaw.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Instrukcje: Uzyskiwanie informacji dotyczących elementu członkowskiego typów i z zestawu](../../../docs/framework/app-domains/how-to-obtain-type-and-member-information-from-an-assembly.md)  
 W tym artykule opisano, jak programowo uzyskać typ i inne informacje z zestawu.  
  
 [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 Zawiera omówienie pojęć dotyczących języka wspólnego zestawów środowiska uruchomieniowego.  
  
 [Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)  
 Zawiera omówienie powiązania zestawu oraz o <xref:System.Reflection.AssemblyVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybutów.  
  
 [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 W tym artykule opisano, jak środowisko wykonawcze określa, które zestawu do używania w celu spełnienia żądania powiązania.  
  
 [Odbicie](../../../docs/framework/reflection-and-codedom/reflection.md)  
 Opisuje sposób używania **odbicia** klasy, aby uzyskać informacje o zestawie.
