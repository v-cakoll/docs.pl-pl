---
title: Zestawy w środowisku uruchomieniowym języka wspólnego
ms.date: 03/30/2017
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.assetid: 2cfebe19-7436-49f1-bd99-3c4019f0b676
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3b516e43c07666f4b52e67f85cb567ab310f020
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832915"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w środowisku uruchomieniowym języka wspólnego
Zestawy są blokami konstrukcyjnymi aplikacji .NET Framework; tworzą one podstawową jednostką wdrażania, kontroli wersji, ponownego użycia, określania zakresu aktywacji i uprawnień zabezpieczeń. Zestaw jest kolekcją typów i zasobów, które zostały opracowane w celu współpracują ze sobą i tworzą jednostkę logiczną funkcji. Zestaw zawiera środowisko uruchomieniowe języka wspólnego informacje potrzebne do należy pamiętać o implementacji typu. Do środowiska uruchomieniowego typem nie istnieje poza kontekstem zestawu.  
  
 Zespół wykonuje następujące funkcje:  
  
- Zawiera kod, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego. Kod języka intermediate language (MSIL) firmy Microsoft w pliku wykonalnego (PE) pliku nie zostaną wykonane, jeśli nie ma skojarzonego manifestu dla aplikacji. Należy pamiętać, że każdy zestaw może mieć tylko jeden wpis punktu (czyli `DllMain`, `WinMain`, lub `Main`).  
  
- Stanowi on granicy zabezpieczeń. Zestaw to jednostka, jaką żądane oraz udzielili uprawnień. Aby uzyskać więcej informacji o zabezpieczeniach granice odnoszących się do zestawów, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Stanowi on granicy typu. Każdy typ tożsamości zawiera nazwę zestawu, w której znajduje się. Typ o nazwie `MyType` czyli jest załadowany w zakresie jednego zestawu, nie taka sama, jak typ o nazwie `MyType` który jest ładowany w zakresie innego zestawu.  
  
- Wchodzi w skład granice zakresu odwołań. Manifest zestawu zawiera metadane zestawu jest używana do rozpoznawania typów i spełniającej żądania zasobu. Określa typy i zasoby, które są udostępniane poza zestawem. Manifest również wylicza inne zestawy, od których zależy.  
  
- Stanowi on granicy wersji. Zestaw jest najmniejszego obsługą wersji środowiska uruchomieniowego języka wspólnego; wszystkie typy i zasoby z tego samego zestawu są wersjonowane jako jednostka. Manifest zestawu zawiera opis wersji zależności, o których należy określić wszystkie zależne zestawy. Aby uzyskać więcej informacji dotyczących wersjonowania, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Wchodzi w skład jednostki wdrożenia. Po uruchomieniu aplikacji tylko zestawy, które początkowo wywołuje aplikacji musi być obecny. Inne zestawy, takie jak zasoby lokalizacyjne lub zestawów zawierających klasy narzędzi mogą być pobierane na żądanie. Dzięki temu aplikacje były proste i alokowania elastycznego, gdy pobrane po raz pierwszy. Aby uzyskać więcej informacji o wdrażaniu zestawów, zobacz [wdrażanie aplikacji](../../../docs/framework/deployment/index.md).  
  
- Jest to jednostka, jaką wykonywanie side-by-side jest obsługiwane. Aby uzyskać więcej informacji dotyczących uruchamiania wielu wersji zestawu, zobacz [zestawy i wykonywanie Side-by-Side](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Zespoły mogą być statyczne lub dynamiczne. Statyczne zestawy mogą obejmować typów programu .NET Framework (klasy i interfejsy), a także zasoby dla zestawu (mapy bitowe, JPEG pliki, pliki zasobów i tak dalej). Statyczne zestawy są przechowywane na dysku w przenośnych plików wykonywalnych (PE). Umożliwia także programu .NET Framework do tworzenia dynamicznych zestawów, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed wykonaniem. Możesz zapisać dynamicznych zestawów na dysku, po ich wykonaniu.  
  
 Istnieje kilka sposobów tworzenia zestawów. Można użyć narzędzi deweloperskich, takich jak Visual Studio, użytego w przeszłości do tworzenia plików .dll lub .exe. Można użyć narzędzi dostępnych w Windows Software Development Kit (SDK) do tworzenia zestawów przy użyciu modułów utworzonych w innych środowiskach programistycznych. Umożliwia także środowiska uruchomieniowego języka wspólnego interfejsów API, takich jak <xref:System.Reflection.Emit?displayProperty=nameWithType>, aby utworzyć zestawów dynamicznych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zawartość zestawu](../../../docs/framework/app-domains/assembly-contents.md)|W tym artykule opisano elementy, które tworzą zestaw.|  
|[Manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md)|W tym artykule opisano je w manifeście zestawu i jak są przechowywane w zestawach.|  
|[Global Assembly Cache](../../../docs/framework/app-domains/gac.md)|Opis globalnej pamięci podręcznej i sposobie ich użycia za pomocą zestawów.|  
|[Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)|Opisuje charakterystykę zestawy o silnych nazwach.|  
|[Zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md)|W tym artykule omówiono, jak działają zabezpieczenia za pomocą zestawów.|  
|[Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)|Omówienie zasad przechowywania wersji .NET Framework.|  
|[Umieszczanie zestawu](../../../docs/framework/app-domains/assembly-placement.md)|W tym artykule omówiono, gdzie umieścić zestawy.|  
|[Zestawy i wykonywanie równoczesne](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Zawiera omówienie sposobu użycia wielu wersji środowiska uruchomieniowego lub zestawie jednocześnie.|  
|[Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)|W tym artykule opisano sposób tworzenia, zaloguj się i ustawianie atrybutów zestawów.|  
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|W tym artykule opisano sposób tworzenia zestawów dynamicznych.|  
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|W tym artykule opisano, jak .NET Framework jest rozpoznawana jako odwołania do zestawów w czasie wykonywania.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
