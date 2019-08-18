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
ms.openlocfilehash: b27a8d89b0345082b8cf06c3eb141e73e2bf0faf
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/17/2019
ms.locfileid: "69567365"
---
# <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w środowisku uruchomieniowym języka wspólnego
Zestawy są blokami konstrukcyjnymi aplikacji .NET Framework; tworzą one podstawową jednostkę wdrożenia, kontrolę wersji, ponowne użycie, zakres aktywacji i uprawnienia zabezpieczeń. Zestaw jest kolekcją typów i zasobów, które są tworzone w celu współdziałania i tworzą logiczną jednostkę funkcjonalności. Zestaw udostępnia środowisko uruchomieniowe języka wspólnego z informacjami, które muszą być świadome implementacji typów. Dla środowiska uruchomieniowego typ nie istnieje poza kontekstem zestawu.  
  
 Zestaw wykonuje następujące funkcje:  
  
- Zawiera kod, który jest wykonywany przez środowisko uruchomieniowe języka wspólnego. Kod języka pośredniego (MSIL) firmy Microsoft w przenośnym pliku wykonywalnym (PE) nie zostanie wykonany, jeśli nie ma skojarzonego manifestu zestawu. Należy zauważyć, że każdy zestaw może mieć tylko jeden punkt wejścia (to `DllMain`jest `WinMain`,, `Main`lub).  
  
- Stanowi ona granicę zabezpieczeń. Zestaw jest jednostką, w której uprawnienia są żądane i udzielane. Aby uzyskać więcej informacji o granicach zabezpieczeń, które są stosowane do zestawów, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
- Tworzy granicę typu. Każda tożsamość typu zawiera nazwę zestawu, w którym znajduje się. Typ o nazwie `MyType` , który jest ładowany w zakresie jednego zestawu, nie jest taki sam jak typ o nazwie `MyType` , który jest ładowany w zakresie innego zestawu.  
  
- Tworzy granicę zakresu odwołania. Manifest zestawu zawiera metadane zestawu, który jest używany do rozpoznawania typów i spełniania żądań zasobów. Określa typy i zasoby, które są widoczne poza zestawem. Manifest wylicza również inne zestawy, od których zależy.  
  
- Jest to granica wersji. Zestaw jest najmniejszą wersją jednostki w środowisku uruchomieniowym języka wspólnego; wszystkie typy i zasoby w tym samym zestawie są w wersji jako jednostka. Manifest zestawu zawiera opis zależności wersji określonych dla wszystkich zestawów zależnych. Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [wersja zestawu](../../../docs/framework/app-domains/assembly-versioning.md).  
  
- Tworzy jednostkę wdrożenia. Po uruchomieniu aplikacji, tylko zestawy, które początkowo wywołuje aplikacja, muszą być obecne. Inne zestawy, takie jak zasoby lokalizacyjne lub zestawy zawierające klasy narzędzi, można pobrać na żądanie. Dzięki temu aplikacje mają być proste i cienkie podczas pierwszego pobierania. Aby uzyskać więcej informacji o wdrażaniu zestawów, zobacz [wdrażanie aplikacji](../../../docs/framework/deployment/index.md).  
  
- Jest to jednostka, w której obsługiwane jest wykonywanie równoczesne. Aby uzyskać więcej informacji na temat uruchamiania wielu wersji zestawu, zobacz [zestawy i wykonywanie równoczesne](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Zestawy mogą być statyczne lub dynamiczne. Zestawy statyczne mogą zawierać typy .NET Framework (interfejsy i klasy), a także zasoby zestawu (mapy bitowe, pliki JPEG, pliki zasobów itd.). Zestawy statyczne są przechowywane na dysku w przenośnych plikach wykonywalnych (PE). Można również użyć .NET Framework do tworzenia zestawów dynamicznych, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed wykonaniem. Zestawy dynamiczne można zapisać na dysku po ich wykonaniu.  
  
 Istnieje kilka sposobów tworzenia zestawów. Możesz użyć narzędzi programistycznych, takich jak Visual Studio, używanych w przeszłości do tworzenia plików. dll lub. exe. Korzystając z narzędzi dostępnych w Windows SDK, można tworzyć zestawy z modułami utworzonymi w innych środowiskach deweloperskich. Możesz również używać interfejsów API środowiska uruchomieniowego języka wspólnego, <xref:System.Reflection.Emit?displayProperty=nameWithType>takich jak, do tworzenia zestawów dynamicznych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zawartość zestawu](../../../docs/framework/app-domains/assembly-contents.md)|Opisuje elementy wchodzące w skład zestawu.|  
|[Manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md)|Opisuje dane w manifeście zestawu i sposób ich przechowywania w zestawach.|  
|[Global Assembly Cache](../../../docs/framework/app-domains/gac.md)|Opisuje globalną pamięć podręczną zestawów i sposób jej użycia z zestawami.|  
|[Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)|Opisuje charakterystykę zestawów o silnych nazwach.|  
|[Zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md)|W tym artykule omówiono sposób działania zabezpieczeń z zestawami.|  
|[Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)|Zawiera omówienie zasad dotyczących wersji .NET Framework.|  
|[Umieszczanie zestawu](../../../docs/framework/app-domains/assembly-placement.md)|W tym artykule omówiono miejsce lokalizowania zestawów.|  
|[Zestawy i wykonywanie równoczesne](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Zawiera omówienie używania wielu wersji środowiska uruchomieniowego lub zestawu jednocześnie.|  
|[Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)|Opisuje sposób tworzenia, podpisywania i ustawiania atrybutów dla zestawów.|  
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Opisuje sposób tworzenia zestawów dynamicznych.|  
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Opisuje sposób, w jaki .NET Framework rozwiązuje odwołania do zestawów w czasie wykonywania.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
