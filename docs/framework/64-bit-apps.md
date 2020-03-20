---
title: Aplikacje 64-bitowe
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
ms.openlocfilehash: 90e022d5643dc49ccc5b78d071b3b473c92f0670
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74429664"
---
# <a name="64-bit-applications"></a>Aplikacje 64-bitowe
Podczas kompilowania aplikacji można określić, że powinna ona być uruchamiana w 64-bitowym systemie operacyjnym Windows jako aplikacja natywna lub w obszarze WOW64 (Windows 32-bitowy w systemie Windows 64-bitowy). WOW64 to środowisko zgodności, które umożliwia uruchamianie aplikacji 32-bitowej w systemie 64-bitowym. WOW64 znajduje się we wszystkich 64-bitowych wersjach systemu operacyjnego Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Uruchamianie aplikacji 32-bitowych i 64-bitowych w systemie Windows  
 Wszystkie aplikacje, które są zbudowane na .NET Framework 1.0 lub 1.1 są traktowane jako aplikacje 32-bitowe w 64-bitowym systemie operacyjnym i są zawsze wykonywane w ramach WOW64 i 32-bitowego wspólnego środowiska wykonawczego języka (CLR). Aplikacje 32-bitowe, które są zbudowane w wersjach .NET Framework 4 lub nowszych, są również uruchamiane w ramach WOW64 w systemach 64-bitowych.  
  
 Program Visual Studio instaluje 32-bitową wersję programu CLR na komputerze x86 oraz wersję 32-bitową i odpowiednią 64-bitową wersję programu CLR na 64-bitowym komputerze z systemem Windows. (Ponieważ program Visual Studio jest aplikacją 32-bitową, gdy jest zainstalowana w systemie 64-bitowym, działa w obszarze WOW64.  
  
> [!NOTE]
> Ze względu na konstrukcję emulacji x86 i podsystemu WOW64 dla rodziny procesorów Itanium, aplikacje są ograniczone do wykonania na jednym procesorze. Te czynniki zmniejszają wydajność i skalowalność 32-bitowych aplikacji .NET Framework, które są uruchamiane w systemach opartych na itanium. Zaleca się użycie programu .NET Framework 4, który zawiera natywną obsługę 64-bitową dla systemów opartych na itanium, aby zwiększyć wydajność i skalowalność.  
  
 Domyślnie po uruchomieniu 64-bitowej aplikacji zarządzanej w 64-bitowym systemie operacyjnym Windows można utworzyć obiekt o wartości nie większej niż 2 gigabajty (GB). Jednak w .NET Framework 4.5 można zwiększyć ten limit.  Aby uzyskać więcej informacji, zobacz [ \<gcAllowVeryLargeObjects> element](./configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Wiele zestawów działa identycznie zarówno na 32-bitowym clr i 64-bitowym CLR. Jednak niektóre programy mogą zachowywać się inaczej, w zależności od clr, jeśli zawierają one co najmniej jedną z następujących czynności:  
  
- Struktury, które zawierają elementy członkowskie, które zmieniają rozmiar w zależności od platformy (na przykład dowolnego typu wskaźnika).  
  
- Arytmetyka wskaźnika, która zawiera stałe rozmiary.  
  
- Niepoprawna platforma wywołać lub `Int32` deklaracje COM, `IntPtr`które używają do uchwytów zamiast .  
  
- Kod, który `IntPtr` `Int32`rzuca do .  
  
 Aby uzyskać więcej informacji na temat przenoszenia aplikacji 32-bitowej do uruchomienia w 64-bitowym programie CLR, zobacz [Migrowanie 32-bitowego kodu zarządzanego do 64-bitowego](https://docs.microsoft.com/previous-versions/dotnet/articles/ms973190(v=msdn.10)).  
  
## <a name="general-64-bit-programming-information"></a>Ogólne informacje nt. programowania 64-bitowego  
 Aby uzyskać ogólne informacje na temat programowania 64-bitowego, zobacz następujące dokumenty:  
  
- W dokumentacji systemu Windows SDK zobacz [Przewodnik po programowaniu 64-bitowego systemu Windows](/windows/win32/winprog64/programming-guide-for-64-bit-windows).  
  
- Aby uzyskać informacje na temat obsługi programu Visual Studio do tworzenia aplikacji 64-bitowych, zobacz [64-bitowa obsługa środowiska VISUAL Studio IDE](/visualstudio/ide/visual-studio-ide-64-bit-support).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Obsługa kompilatora do tworzenia aplikacji 64-bitowych  
 Domyślnie podczas tworzenia aplikacji na komputerze 32-bitowym lub 64-bitowym za pomocą programu .NET Framework aplikacja będzie działać na komputerze 64-bitowym jako aplikacja natywna (czyli nie w ramach wow64). W poniższej tabeli wymieniono dokumenty, które wyjaśniają, jak używać kompilatorów programu Visual Studio do tworzenia aplikacji 64-bitowych, które będą uruchamiane jako natywne, w obszarze WOW64 lub obu.  
  
|Kompilator|Kompilator, opcja|  
|--------------|---------------------|  
|Visual Basic|[-platforma (Visual Basic)](../visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[-platform (Opcje kompilatora Języka C#)](../csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Aplikacje dla niezależnego od platformy, języka pośredniego firmy Microsoft (MSIL) można tworzyć za pomocą **/clr:safe**. Aby uzyskać więcej informacji, zobacz [-clr (Kompilacja środowiska wykonawczego języka wspólnego)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ zawiera oddzielny kompilator dla każdego 64-bitowego systemu operacyjnego. Aby uzyskać więcej informacji na temat używania języka Visual C++ do tworzenia natywnych aplikacji działających w 64-bitowym systemie operacyjnym Windows, zobacz [Programowanie 64-bitowe](/cpp/build/configuring-programs-for-64-bit-visual-cpp).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Określanie stanu pliku .exe lub pliku .dll  
 Aby ustalić, czy plik exe lub plik .dll jest przeznaczony do uruchamiania tylko na określonej platformie, czy w obszarze WOW64, należy użyć [pliku CorFlags.exe (CorFlags Conversion Tool)](./tools/corflags-exe-corflags-conversion-tool.md) bez żadnych opcji. Można również użyć programu CorFlags.exe, aby zmienić stan platformy pliku exe lub pliku dll. Nagłówek CLR zestawu programu Visual Studio ma numer wersji głównego środowiska wykonawczego ustawiony na 2, a numer wersji pomocniczego środowiska wykonawczego ustawiony na 5. Aplikacje, które mają wersję podrzędnego środowiska uruchomieniowego ustawioną na 0, są traktowane jako starsze aplikacje i są zawsze wykonywane w ramach WOW64.  
  
 Aby programowo kwerendy .exe lub .dll, aby zobaczyć, czy jest przeznaczony do uruchamiania <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> tylko na określonej platformie lub w ramach WOW64, należy użyć metody.
