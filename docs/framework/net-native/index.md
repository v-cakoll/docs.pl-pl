---
title: Kompilowanie aplikacji z architekturą .NET Native
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ecc707bb07d6d17ae4115b483cc8f52083f3933
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiling-apps-with-net-native"></a>Kompilowanie aplikacji z architekturą .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] jest to technologia wstępnej kompilacji umożliwiające tworzenie i wdrażanie aplikacji systemu Windows, która jest dołączana do programu Visual Studio 2015 i nowszych wersjach. Kompiluje automatycznie wersji aplikacji, które są zapisywane w kodu zarządzanego (C# lub Visual Basic), że docelowej platformy .NET Framework i Windows 10 do kodu natywnego.  
  
 Zwykle aplikacje, które odnoszą się do programu .NET Framework są kompilowane do języku pośrednim (IL). W czasie wykonywania przy użyciu kompilatora just in time (JIT) tłumaczy IL do kodu natywnego. Z kolei [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompiluje aplikacji systemu Windows bezpośrednio do kodu natywnego. Dla deweloperów oznacza to:  
  
-   Aplikacje funkcji wydajność kodu natywnego. Zwykle wydajność będzie nadrzędne w stosunku do kodu, który jest najpierw skompilować do IL i następnie skompilowanych do natywnego kodu przy użyciu kompilatora JIT. 
  
-   Można kontynuować do programowania w języku C# lub Visual Basic.  
  
-   Można nadal korzystać z zasobów udostępnianych przez program .NET Framework, w tym biblioteki klas, pamięci automatycznego zarządzania i odzyskiwanie pamięci i obsługi wyjątków.  
  
 Dla użytkowników w aplikacjach [!INCLUDE[net_native](../../../includes/net-native-md.md)] ma następujące zalety:  
  
-   Szybsze wykonywanie w większości scenariuszy i aplikacji.
  
-   Szybsze uruchamianie w większości scenariuszy i aplikacji. 
  
-   Niskie koszty wdrożenia i aktualizacji.  
  
-   Zoptymalizowanych pod kątem użycia pamięci aplikacji.  

> [!IMPORTANT]
> Większość aplikacji i scenariusze platformy .NET Native oferuje znacznie szybsze uruchamianie i lepszą wydajność w porównaniu do aplikacji kompilowane IL lub obrazów NGEN. Jednak wyniki mogą być różne. W celu zapewnienia aplikacji uzyskał ulepszenia wydajności programu .NET Native, należy porównać jego wydajność, z tym nie - platformy .NET Native wersji aplikacji. Aby uzyskać więcej informacji, zobacz [sesja wydajności — omówienie](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Ale [!INCLUDE[net_native](../../../includes/net-native-md.md)] obejmuje więcej niż kompilacji do kodu natywnego. Przekształca ją sposób, że aplikacje .NET Framework są wbudowane i wykonywane. W szczególności:  
  
-   Podczas wstępnej kompilacji wymagane części programu .NET Framework są statycznie połączone w swojej aplikacji. Umożliwia to aplikacji do uruchamiania z bibliotekami lokalnej dla aplikacji programu .NET Framework i kompilator przeprowadzić analizę globalną dostarczać wydajności usługi wins. W związku z tym aplikacje będą uruchamiać zawsze szybciej nawet po aktualizacji .NET Framework.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] Środowiska uruchomieniowego jest zoptymalizowana pod kątem statycznych wstępnej kompilacji i w większość przypadków oferuje lepszą wydajność. W tym samym czasie zachowuje podstawowe funkcje odbicia, które tak produktywności deweloperów.  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)] używa takie same wstecz końcowy jako kompilatora języka C++, która jest zoptymalizowana pod kątem scenariuszy wstępnej kompilacji statycznych.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest w stanie można wyświetlić zwiększenia wydajności C++ deweloperom kodu zarządzanego, ponieważ używa narzędzia takie same lub podobne jako C++ pod maską, jak pokazano w poniższej tabeli.  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|C++|  
|-|----------------------------------------------------------------|-----------|  
|Biblioteki|.NET Framework i środowiska wykonawczego systemu Windows|Win32 + środowiska wykonawczego systemu Windows|  
|Kompilatora|Optymalizacja kompilatora UTC|Optymalizacja kompilatora UTC|  
|Wdrożony|Pliki binarne gotowy do uruchomienia|Pliki binarne gotowy do uruchomienia (ASM)|  
|Środowisko uruchomieniowe|MRT.dll (środowisko uruchomieniowe CLR minimalnego)|CRT.dll (C Runtime)|  
  
 Dla aplikacji systemu Windows dla systemu Windows 10 możesz przekazać dane binarne kompilacja kodu natywnego platformy .NET w pakiety aplikacji (pliki .appx) do Sklepu Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą natywnej kompilacji kodu .NET zobacz następujące tematy:  
  
-   [Wprowadzenie do korzystania z natywnej kompilacji kodu .NET: wskazówki środowisko dewelopera](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   [Platforma .NET native i kompilacja:](../../../docs/framework/net-native/net-native-and-compilation.md) jak platforma .NET Native kompiluje projektu do kodu natywnego.  
  
-   [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [Dokumentacja interfejsu API odbicia](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [Serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a>Zobacz też  
 [.NET natywnego — często zadawane pytania](http://msdn.microsoft.com/vstudio/dn642499.aspx)
