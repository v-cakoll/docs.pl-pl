---
title: Aplikacje 64-bitowe
description: Uzyskaj informacje na temat konfigurowania aplikacji w systemie Windows 64-bitowego systemu operacyjnego jako natywnej aplikacji 64-bitowej lub w emulatorze WOW64 (Windows 32-bit w systemie Windows 64-bit).
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
ms.openlocfilehash: 4589d7a070a477dcb229fbaea686f6c6ff7d7e08
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989991"
---
# <a name="64-bit-applications"></a>Aplikacje 64-bitowe
Podczas kompilowania aplikacji można określić, że powinna być uruchamiana w systemie operacyjnym Windows 64-bitowym jako aplikacja natywna lub w emulatorze WOW64 (Windows 32-bit w systemie Windows 64-bit). Emulator WOW64 to środowisko zgodności, które umożliwia uruchamianie aplikacji 32-bitowych w systemie 64-bitowym. Emulator WOW64 jest uwzględniony we wszystkich 64-bitowych wersjach systemu operacyjnego Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Uruchamianie aplikacji 32-bitowych a 64-bitowych w systemie Windows  
 Wszystkie aplikacje, które są oparte na .NET Framework 1,0 lub 1,1 są traktowane jako aplikacje 32-bitowe w 64-bitowym systemie operacyjnym i są zawsze wykonywane w ramach emulatora WOW64 i 32-bitowego środowiska uruchomieniowego języka wspólnego (CLR). aplikacje 32-bitowe, które są oparte na .NET Framework 4 lub nowszych wersjach, również są uruchamiane w emulatorze WOW64 w systemach 64-bitowych.  
  
 Program Visual Studio instaluje 32-bitową wersję środowiska CLR na komputerze z procesorem x86 oraz wersję 32-bitową i odpowiednią 64-bitową wersję środowiska CLR na komputerze z systemem 64-bitowym. (Ponieważ program Visual Studio jest aplikacją 32-bitową, gdy jest zainstalowana w systemie 64-bitowym, działa w emulatorze WOW64).  
  
> [!NOTE]
> Ze względu na sposób projektowania emulacji x86 i podsystemu WOW64 dla rodziny procesorów Itanium aplikacje są ograniczone do wykonywania na jednym procesorze. Czynniki te zmniejszają wydajność i skalowalność 32-.NET Framework bitowych aplikacji, które działają w systemach opartych na procesorze Itanium. Zalecamy używanie .NET Framework 4, który obejmuje natywną 64-bitową obsługę systemów opartych na procesorze Itanium w celu zwiększenia wydajności i skalowalności.  
  
 Domyślnie po uruchomieniu 64-bitowej aplikacji zarządzanej w 64-bitowym systemie operacyjnym Windows można utworzyć obiekt o wartości nie większej niż 2 gigabajty (GB). Jednak w .NET Framework 4,5 można zwiększyć ten limit.  Aby uzyskać więcej informacji, zobacz [ \<gcAllowVeryLargeObjects> element](./configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Wiele zestawów działa identycznie na 32-bitowym CLR i 64-bitowym środowisku CLR. Niektóre programy mogą jednak zachowywać się inaczej, w zależności od środowiska CLR, jeśli zawierają jedną lub więcej z następujących elementów:  
  
- Struktury zawierające elementy członkowskie, które zmieniają rozmiar w zależności od platformy (na przykład dowolnego typu wskaźnika).  
  
- Arytmetyczny wskaźnik obejmujący stałe rozmiary.  
  
- Nieprawidłowe wywołanie platformy lub deklaracje COM, które są używane `Int32` do obsługi zamiast `IntPtr` .  
  
- Kod, który jest rzutowany `IntPtr` na `Int32` .  
  
 Aby uzyskać więcej informacji na temat sposobu przenoszenia aplikacji 32-bitowej do uruchamiania na 64-bitowym CLR, zobacz [migrowanie 32-bitowego kodu zarządzanego do 64-bitowego](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10)).  
  
## <a name="general-64-bit-programming-information"></a>Ogólne informacje nt. programowania 64-bitowego  
 Aby uzyskać ogólne informacje na temat programowania 64-bitowego, zobacz następujące dokumenty:  
  
- W dokumentacji Windows SDK zapoznaj się z [przewodnikiem programowania dla systemu Windows 64-bitowego](/windows/win32/winprog64/programming-guide-for-64-bit-windows).  
  
- Aby uzyskać informacje o obsłudze programu Visual Studio do tworzenia aplikacji 64-bitowych, zobacz [Visual Studio IDE 64-bit support](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Obsługa kompilatora do tworzenia aplikacji 64-bitowych  
 Domyślnie w przypadku używania .NET Framework do kompilowania aplikacji na komputerze 32-bitowym lub 64-bitowym aplikacja zostanie uruchomiona na komputerze 64-bitowym jako aplikacja natywna (czyli nie poniżej emulatora WOW64). W poniższej tabeli wymieniono dokumenty, które wyjaśniają, jak używać kompilatorów programu Visual Studio do tworzenia aplikacji 64-bitowych, które będą uruchamiane jako natywne w emulatorze WOW64.  
  
|Compiler|Opcja kompilatora|  
|--------------|---------------------|  
|Visual Basic|[-Platforma (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[-platform (opcje kompilatora C#)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Możesz tworzyć aplikacje platform-niezależny od, Microsoft pośredniego języka (MSIL) za pomocą **/CLR: Safe**. Aby uzyskać więcej informacji, zobacz [-CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ zawiera oddzielny kompilator dla każdego 64-bitowego systemu operacyjnego. Aby uzyskać więcej informacji na temat sposobu użycia Visual C++ do tworzenia natywnych aplikacji działających w 64-bitowym systemie operacyjnym Windows, zobacz [64-bitowe programowanie](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Określanie stanu pliku .exe lub pliku .dll  
 Aby określić, czy plik. exe lub plik DLL ma być uruchamiany tylko na określonej platformie, czy w emulatorze WOW64, użyj [CorFlags.exe (narzędzie konwersji CorFlags)](./tools/corflags-exe-corflags-conversion-tool.md) bez opcji. Można również użyć CorFlags.exe, aby zmienić stan platformy pliku. exe lub pliku dll. W nagłówku CLR zestawu programu Visual Studio jest ustawiony numer wersji głównej środowiska uruchomieniowego na 2, a dla dodatkowego numeru wersji środowiska uruchomieniowego ustawiono wartość 5. Aplikacje, które mają niewielką wersję środowiska uruchomieniowego ustawioną na 0, są traktowane jako starsze aplikacje i są zawsze wykonywane w emulatorze WOW64.  
  
 Aby programowo zbadać plik exe lub dll w celu sprawdzenia, czy ma on być uruchamiany tylko na określonej platformie lub w emulatorze WOW64, użyj <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metody.
