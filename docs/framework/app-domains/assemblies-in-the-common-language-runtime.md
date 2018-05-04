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
ms.openlocfilehash: eefd3773d26fe71741668a9df366f041ba0ae0a4
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="assemblies-in-the-common-language-runtime"></a>Zestawy w środowisku uruchomieniowym języka wspólnego
Zestawy są blokami konstrukcyjnymi aplikacji .NET Framework; stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnienia zabezpieczeń. Zestaw jest kolekcją typów i zasobów, które są przeznaczone do współpracują ze sobą i utworzenia jednostki logicznej funkcji. Zestaw zawiera środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji. Do środowiska wykonawczego typ nie istnieje poza kontekstem zestawu.  
  
 Zestaw wykonuje następujące funkcje:  
  
-   Zawiera kod, który wykonuje środowisko uruchomieniowe języka wspólnego. Kod języka pośredniego (MSIL) firmy Microsoft w pliku przenośny plik wykonywalny (PE) nie zostaną wykonane, jeśli nie ma manifestu zestawu skojarzone. Należy pamiętać, że każdy zestaw może mieć tylko jeden wpis punktu (to znaczy `DllMain`, `WinMain`, lub `Main`).  
  
-   Wchodzi w skład granicy zabezpieczeń. Zestaw jest jednostka, jaką żądanie i przyznane uprawnienia. Aby uzyskać więcej informacji o zabezpieczeniach granic dotyczą one zestawy, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md).  
  
-   Wchodzi w skład typu granicy. Każdy typ tożsamości zawiera nazwę zestawu, w której znajduje się. Typ o nazwie `MyType` czyli załadowany w zakresie jednego zestawu nie jest równocześnie jako typ o nazwie `MyType` który został załadowany w zakresie innego zestawu.  
  
-   Wchodzi w skład granice zakresu odwołania. Manifest zestawu zawiera metadane zestawu jest używany do rozpoznawania typów i spełniające żądania zasobów. Określa typy i zasobów, które są udostępniane poza zestaw. Manifest wylicza również innych zestawów, od których zależy.  
  
-   Wchodzi w skład wersji granicy. Zestaw jest znalezienie najmniejszego w środowisku uruchomieniowym języka; wszystkie typy i zasobów w tym samym zestawie są numerów wersji jako jednostka. Manifest zestawu opisano zależności wersji wybrane wszystkie zależne zestawy. Aby uzyskać więcej informacji o wersji, zobacz [przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md).  
  
-   Wchodzi w skład jednostki wdrożenia. Po uruchomieniu aplikacji tylko zestawy, których aplikacja początkowo wywołuje musi być obecny. Inne zestawy, takich jak zasoby lokalizacyjne lub zestawów zawierających klasy narzędzie można pobrać na żądanie. Dzięki temu aplikacje mają być przechowywane w prosty i alokowania, gdy najpierw pobrać. Aby uzyskać więcej informacji na temat wdrażania zestawów, zobacz [wdrażanie aplikacji](../../../docs/framework/deployment/index.md).  
  
-   Jest to jednostka, jaką wykonywanie side-by-side jest obsługiwane. Aby uzyskać więcej informacji na temat uruchamiania wielu wersji zestawu, zobacz [zestawy i wykonywanie Side-by-Side](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md).  
  
 Zestawy mogą być statyczne lub dynamiczne. Zestawy statyczne mogą obejmować typów .NET Framework (klasy i interfejsy), oraz zasobów dla zestawu (mapy bitowe, JPEG pliki plików zasobów i tak dalej). Zestawy statyczne są przechowywane na dysku w przenośne pliki wykonywalne (PE). .NET Framework również służy do tworzenia dynamicznych zestawów, które są uruchamiane bezpośrednio z pamięci i nie są zapisywane na dysku przed realizacją. Możesz zapisać zestawów dynamicznych na dysku po ich wykonaniu.  
  
 Istnieje kilka sposobów, aby utworzyć zestawy. Korzystając z narzędziami programistycznymi, takimi jak Visual Studio, które zostały użyte w przeszłości, aby utworzyć pliki .dll lub .exe. Korzystając z narzędzi dostępnych w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] utworzyć zestawy z modułów utworzonych w innych środowiskach programistycznych. Umożliwia także aparat plików wykonywalnych języka wspólnego interfejsów API, takich jak <xref:System.Reflection.Emit?displayProperty=nameWithType>, aby utworzyć zestawów dynamicznych.  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Zawartość zestawu](../../../docs/framework/app-domains/assembly-contents.md)|W tym artykule opisano elementy wchodzące w skład zestawu.|  
|[Manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md)|W tym artykule opisano w manifeście zestawu i sposób przechowywania w zestawach danych.|  
|[Global Assembly Cache](../../../docs/framework/app-domains/gac.md)|Opis pamięci podręcznej GAC i sposobu korzystania z zestawami.|  
|[Zestawy o silnych nazwach](../../../docs/framework/app-domains/strong-named-assemblies.md)|Opisuje właściwości zestawy o silnych nazwach.|  
|[Zagadnienia dotyczące zabezpieczeń zestawów](../../../docs/framework/app-domains/assembly-security-considerations.md)|W tym artykule omówiono, jak działają zabezpieczenia z zestawami.|  
|[Przechowywanie wersji zestawu](../../../docs/framework/app-domains/assembly-versioning.md)|Omówienie zasad przechowywania wersji .NET Framework.|  
|[Umieszczanie zestawu](../../../docs/framework/app-domains/assembly-placement.md)|W tym artykule omówiono, gdzie umieścić zestawy.|  
|[Zestawy i wykonywanie równoczesne](../../../docs/framework/app-domains/assemblies-and-side-by-side-execution.md)|Zawiera omówienie sposobu użycia wielu wersji środowiska uruchomieniowego lub zestawu jednocześnie.|  
|[Programowanie za pomocą zestawów](../../../docs/framework/app-domains/programming-with-assemblies.md)|Opisuje sposób tworzenia, zaloguj się i ustawić atrybuty zestawów.|  
|[Emitowanie dynamicznych metod i zestawów](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Opisuje sposób tworzenia zestawów dynamicznych.|  
|[Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|W tym artykule opisano, jak programu .NET Framework jest rozpoznawany jako odwołania do zestawów w czasie wykonywania.|  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection.Assembly?displayProperty=nameWithType>
