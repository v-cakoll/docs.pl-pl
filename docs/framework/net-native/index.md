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
ms.openlocfilehash: 28b09bf07d831747be0006ffe1f1d8c5ac5171ce
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052643"
---
# <a name="compiling-apps-with-net-native"></a>Kompilowanie aplikacji z architekturą .NET Native
.NET native jest technologia kompilacji wstępnej do kompilowania i wdrażania aplikacji Windows, który jest dołączony do programu Visual Studio 2015 i nowszych wersjach. Automatycznie skompiluje wersji aplikacji, które są zapisywane w kodzie zarządzanym (C# lub Visual Basic) i przeznaczone na platformę .NET Framework i Windows 10 do kodu macierzystego.  
  
 Zazwyczaj aplikacje, które obsługują program .NET Framework są kompilowane do języka pośredniego (IL). W czasie wykonywania kompilator just-in-time (JIT) tłumaczy IL do kodu macierzystego. Z kolei .NET Native kompiluje aplikacje Windows bezpośrednio do kodu macierzystego. Dla deweloperów oznacza to:  
  
- Twoje aplikacje są wyposażone w wydajności kodu natywnego. Zwykle wydajność będzie nadrzędne w stosunku do kodu, który jest najpierw skompilowane do IL, a następnie kompilowane do kodu macierzystego przy użyciu kompilatora JIT. 
  
- Można kontynuować programu C# lub Visual Basic.  
  
- Można nadal korzystać z zasobów udostępnianych przez .NET Framework, w tym jego biblioteki klas, pamięcią automatyczną zarządzania i wyrzucania elementów kolekcji i obsługi wyjątków.  
  
 W przypadku użytkowników aplikacji .NET Native oferuje następujące zalety:  
  
- Krótszy czas wykonywania dla większości scenariuszy i aplikacji.
  
- Krótszy czas uruchamiania dla większości scenariuszy i aplikacji. 
  
- Niskie koszty wdrożenia i aktualizacji.  
  
- Zoptymalizowane pod kątem użycia pamięci aplikacji.  

> [!IMPORTANT]
> Większość aplikacji i scenariuszy .NET Native oferuje znacznie krótszy czas uruchamiania i doskonałą wydajność w porównaniu do aplikacji skompilowanych IL lub obrazów NGEN. Jednak wyniki mogą się różnić. Aby upewnić się, że aplikacja skorzystał z ulepszenia wydajności programu .NET Native, należy porównać jego wydajność, korzystając z niego bez — .NET Native wersję aplikacji. Aby uzyskać więcej informacji, zobacz [sesja wydajności — omówienie](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).
 
Jednak .NET Native obejmuje więcej niż kompilacji do kodu macierzystego. Jego zmienia sposób skompilowane i wykonywane aplikacje .NET Framework. W szczególności:  
  
- Podczas wstępnej kompilacji wymagane części programu .NET Framework są łączone statycznie z Twoją aplikacją. Umożliwia to aplikacji do uruchamiania z bibliotekami lokalnego dla aplikacji programu .NET Framework i kompilator do przeprowadzenia analizy globalnego dostarczać wydajności usługi wins. W rezultacie aplikacje będą uruchamiać zawsze szybciej nawet po zakończeniu aktualizacji .NET Framework.  
  
- Środowisko uruchomieniowe platformy .NET Native została zoptymalizowana pod kątem statyczne wstępnej kompilacji i w zdecydowanej większości przypadków zapewnia najlepszą wydajność. W tym samym czasie zachowuje podstawowe funkcje odbicia, które więc produktywności deweloperów.  
  
- .NET native używa tego samego zaplecza co C++ kompilatora, który jest zoptymalizowany pod kątem statyczne scenariuszy wstępnej kompilacji.  
  
 .NET native może przynieść korzyści wydajności C++ do zarządzanego kodu deweloperów, ponieważ używa ona narzędzi takie same lub podobne jak C++ kulisy, jak pokazano w poniższej tabeli.  
  
||Architektura .NET Native|C++|  
|-|----------------------------------------------------------------|-----------|  
|Biblioteki|.NET Framework i środowiska wykonawczego Windows|Win32 i środowiska wykonawczego Windows|  
|Kompilator|Optymalizacja kompilatora UTC|Optymalizacja kompilatora UTC|  
|wdrożony|Pliki binarne gotowe do uruchomienia|Gotowe do uruchomienia pliki binarne (ASM)|  
|Środowisko uruchomieniowe|MRT.dll (środowisko uruchomieniowe CLR minimalny)|CRT.dll (środowiska wykonawczego języka C)|  
  
 W przypadku aplikacji Windows dla systemu Windows 10 możesz przekazać pliki binarne natywnej kompilacji kodu .NET, w pakiety aplikacji (pliki .appx) Store Windows.  
  
## <a name="in-this-section"></a>W tej sekcji  
 Aby uzyskać więcej informacji na temat tworzenia aplikacji za pomocą natywnej kompilacji kodu .NET zobacz następujące tematy:  
  
- [Wprowadzenie do kodu natywnej kompilacji .NET: Przewodnik doświadczenia dewelopera](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- [Architektura .NET native i kompilacja:](../../../docs/framework/net-native/net-native-and-compilation.md) Jak .NET Native kompiluje projekt do kodu natywnego.  
  
- [Odbicie i architektura .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [Interfejsy API, które działają na podstawie odbicia](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [Dokumentacja interfejsu API odbicia](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [Serializacja i metadane](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
