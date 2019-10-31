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
ms.openlocfilehash: 1f176e81905fe68c6d740a13240fe814659a7a59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128375"
---
# <a name="compiling-apps-with-net-native"></a>Kompilowanie aplikacji z architekturą .NET Native

.NET Native jest technologią prekompilacji do kompilowania i wdrażania aplikacji systemu Windows, które są dołączone do programu Visual Studio 2015 i jego nowszych wersji. Automatycznie kompiluje wydaną wersję aplikacji, które są zapisywane w kodzie zarządzanym (C# lub Visual Basic), które są przeznaczone dla .NET Framework i systemu Windows 10 do kodu natywnego.

Zazwyczaj aplikacje przeznaczone dla .NET Framework są kompilowane do języka pośredniego (IL). W czasie wykonywania kompilator just-in-Time (JIT) tłumaczy kod IL na natywny. Z kolei .NET Native kompiluje aplikacje systemu Windows bezpośrednio do kodu natywnego. Dla deweloperów oznacza to:

- Twoje aplikacje mają wydajność kodu natywnego. Zwykle wydajność zostanie przewyższana do kodu, który jest najpierw kompilowany do IL, a następnie skompilowany do kodu natywnego przez kompilator JIT.

- Możesz kontynuować program w C# programie lub Visual Basic.

- Można nadal korzystać z zasobów udostępnianych przez .NET Framework, w tym biblioteki klas, automatycznego zarządzania pamięcią i wyrzucania elementów bezużytecznych oraz obsługi wyjątków.

W przypadku użytkowników aplikacji .NET Native oferuje następujące korzyści:

- Krótsze czasy wykonywania większości aplikacji i scenariuszy.

- Krótszy czas uruchamiania dla większości aplikacji i scenariuszy.

- Niskie koszty wdrożenia i aktualizacji.

- Zoptymalizowano użycie pamięci przez aplikację.

> [!IMPORTANT]
> W przypadku większości aplikacji i scenariuszy .NET Native oferuje znacznie krótszy czas uruchamiania i wyższą wydajność w porównaniu z aplikacją skompilowaną do IL lub obrazu NGEN. Jednak wyniki mogą się różnić. Aby upewnić się, że aplikacja korzystała z ulepszeń .NET Native, należy porównać jej wydajność z wersją natywną aplikacji non-.NET. Aby uzyskać więcej informacji, zobacz [Omówienie sesji wydajności](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).

Ale .NET Native zawiera więcej niż Kompilacja kodu natywnego. Przekształca on sposób kompilowania i wykonywania .NET Framework aplikacji. W szczególności:

- Podczas wstępnej kompilacji wymagane fragmenty .NET Framework są statycznie połączone z aplikacją. Dzięki temu aplikacja może działać z bibliotekami lokalnymi aplikacji .NET Framework i kompilatorem do wykonywania analizy globalnej w celu zapewnienia wydajności usługi WINS. W efekcie aplikacje są uruchamiane w sposób ciągły nawet po aktualizacji .NET Framework.

- Środowisko uruchomieniowe .NET Native jest zoptymalizowane pod kątem statycznej kompilacji wstępnej, a w większości przypadków oferuje najwyższą wydajność. W tym samym czasie zachowuje podstawowe funkcje odbicia, które deweloperzy mogą znaleźć.

- .NET Native używa tego samego zaplecza, co C++ kompilator, który jest zoptymalizowany pod kątem statycznych scenariuszy prekompilacji.

.NET Native jest w stanie obsłużyć zalety wydajności C++ programu dla deweloperów kodu zarządzanego, ponieważ używa tych samych lub podobnych narzędzi C++ , co w obszarze okapu, jak pokazano w tej tabeli.

||Architektura .NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|Biblioteki|.NET Framework + środowisko wykonawcze systemu Windows|Win32 + środowisko wykonawcze systemu Windows|
|Compiler|Kompilator optymalizacji UTC|Kompilator optymalizacji UTC|
|szczebl|Gotowe do uruchomienia pliki binarne|Gotowe do uruchomienia pliki binarne (ASM)|
|Środowisko uruchomieniowe|MRT. dll (minimalne środowisko uruchomieniowe CLR)|CRT. dll (środowisko uruchomieniowe języka C)|

W przypadku aplikacji systemu Windows dla systemu Windows 10 przekazywanie plików binarnych kompilacji kodu .NET Native w pakietach aplikacji (pliki. appx) do sklepu Windows.

## <a name="in-this-section"></a>W tej sekcji

Aby uzyskać więcej informacji na temat opracowywania aplikacji za pomocą kompilacji kodu .NET Native, zobacz następujące tematy:

- [Wprowadzenie z kompilacją .NET Native kodu: Przewodnik po samouczku dla deweloperów](getting-started-with-net-native.md)

- [.NET Native i kompilacja:](net-native-and-compilation.md) Jak .NET Native kompiluje projekt na kod natywny.

- [Odbicie i architektura .NET Native](reflection-and-net-native.md)

  - [Interfejsy API, które działają na podstawie odbicia](apis-that-rely-on-reflection.md)

  - [Dokumentacja interfejsu API odbicia](net-native-reflection-api-reference.md)

  - [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)

- [Serializacja i metadane](serialization-and-metadata.md)

- [Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native](migrating-your-windows-store-app-to-net-native.md)

- [Ogólne wskazówki dotyczące rozwiązywania problemów z architekturą .NET Native](net-native-general-troubleshooting.md)
