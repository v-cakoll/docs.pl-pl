---
title: Aplikacje 64-bitowe
ms.date: 03/30/2017
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8cfe1f76cfe489095dfa996bce8005d2777966b7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537984"
---
# <a name="64-bit-applications"></a>Aplikacje 64-bitowe
Podczas kompilowania aplikacji można określić, że powinna działać w systemie operacyjnym Windows 64-bitowych jako natywną aplikację lub w emulatorze WOW64 (Windows 32-bit na Windows 64-bitowych). WOW64 jest środowiskiem zgodności, które umożliwia aplikacji 32-bitowy, do uruchomienia w systemie 64-bitowych. Emulator WOW64 znajduje się we wszystkich 64-bitowych wersjach systemu operacyjnego Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Uruchamianie 32-bitowego. 64-bitowych aplikacji na Windows  
 Wszystkie aplikacje, które są oparte na .NET Framework 1.0 i 1.1, są traktowane jako aplikacje 32-bitowy na 64-bitowym systemie operacyjnym i są zawsze wykonywane w ramach WOW64 i 32-bitowe środowisko uruchomieniowe języka wspólnego (CLR). 32-bitowych aplikacji, które są oparte na [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] lub nowsze wersje również uruchomić w emulatorze WOW64 na 64-bitowym.  
  
 Program Visual Studio instaluje 32-bitowej wersji środowiska CLR na x86 komputera i 32-bitowej wersji oraz odpowiednią wersję 64-bitowym CLR na komputerze Windows 64-bitowym. (Ponieważ program Visual Studio jest 32-bitowej aplikacji, podczas instalowania w systemie 64-bitowych, działa w emulatorze WOW64.)  
  
> [!NOTE]
>  Ze względu na projekt x86 emulacji i w podsystemie WOW64 dla rodziny procesorów Itanium, aplikacje są ograniczone do wykonania w jednym procesorze. Te czynniki zmniejszyć wydajność i skalowalność aplikacji .NET Framework 32-bitowych, działających w systemach opartych na procesorach Itanium. Firma Microsoft zaleca użycie [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)], który macierzysty obsługuje 64-bitowych systemów z procesorem Itanium, w celu zwiększenia wydajności i skalowalności.  
  
 Domyślnie po uruchomieniu aplikacji zarządzanej 64-bitowym na 64-bitowym systemie operacyjnym Windows można utworzyć obiekt nie więcej niż 2 gigabajty (GB). Jednak w [!INCLUDE[net_v45](../../includes/net-v45-md.md)], można zwiększyć ten limit.  Aby uzyskać więcej informacji, zobacz [ \<gcAllowVeryLargeObjects > element](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Wiele zestawów identycznie uruchomić zarówno 32-bitowe środowisko CLR, jak i 64-bitowe środowisko CLR. Jednak niektóre programy mogą zachowywać się różnie w zależności od środowiska CLR, jeśli zawierają one co najmniej jeden z następujących czynności:  
  
-   Struktury, które zawierają składowe, które zmiany rozmiaru, w zależności od platformy (na przykład dowolny typ wskaźnika).  
  
-   Arytmetyczny wskaźnik, obejmującą stałych rozmiarach.  
  
-   Nieprawidłowa platforma wywołania lub deklaracji COM, które używają `Int32` dla dojścia, zamiast `IntPtr`.  
  
-   Kod, który rzutuje `IntPtr` do `Int32`.  
  
 Aby uzyskać więcej informacji na temat portów 32-bitowej aplikacji do uruchomienia w 64-bitowe środowisko CLR, zobacz [Migrowanie 32-bitowego kodu zarządzanego do 64-bitowej](https://msdn.microsoft.com/library/ms973190.aspx).  
  
## <a name="general-64-bit-programming-information"></a>Ogólne informacje nt. programowania 64-bitowego  
 Ogólne informacje o programowaniu 64-bitowego na ten temat można znaleźć w następujących dokumentach:  
  
-   Aby uzyskać więcej informacji na temat 64-bitowej wersji środowiska CLR na 64-bitowym komputerze Windows zobacz [Centrum deweloperów .NET Framework](https://go.microsoft.com/fwlink/?LinkId=37079) w witrynie MSDN.  
  
-   W [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] dokumentacji, zobacz [przewodnik programowania w Windows 64-bitowych](https://go.microsoft.com/fwlink/p/?LinkId=253512).  
  
-   Aby uzyskać informacji dotyczących sposobu pobierania 64-bitowej wersji środowiska CLR, zobacz [.NET Framework Developer Center pobiera](https://go.microsoft.com/fwlink/?LinkId=50953) w witrynie MSDN.  
  
-   Aby uzyskać informacji na temat obsługi programu Visual Studio do tworzenia aplikacji 64-bitowych, zobacz [obsługi programu Visual Studio IDE 64-bitowych](https://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Obsługa kompilatora do tworzenia aplikacji 64-bitowych  
 Domyślnie, gdy używasz programu .NET Framework do tworzenia aplikacji na 32-bitowy lub 64-bitowy komputer, aplikacja zostanie uruchomiona na komputerze 64-bitowych, co aplikacja natywna (czyli nie w emulatorze WOW64). Poniższa tabela zawiera listę dokumentów, które wyjaśniają jak używać kompilatory programu Visual Studio do tworzenia aplikacji 64-bitowych, które będą uruchamiane jako natywny przez środowisko WOW64 lub obie.  
  
|Kompilator|— Opcja kompilatora|  
|--------------|---------------------|  
|Visual Basic|[/ platform (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/ platform (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Możesz utworzyć niezależne od platformy, aplikacje języka intermediate language (MSIL) firmy Microsoft przy użyciu **/CLR: Safe**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ zawiera kompilator osobne dla każdego 64-bitowym systemie operacyjnym. Aby uzyskać więcej informacji o tym, jak używać języka Visual C++ do tworzenia natywnych aplikacji działających na 64-bitowym systemie operacyjnym Windows, zobacz [programowanie 64-bitowe](https://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\)).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Określanie stanu pliku .exe lub pliku .dll  
 Aby określić, czy pliku .exe lub pliku dll jest przeznaczona do uruchamiania tylko na danej platformie lub w emulatorze WOW64, użyj [CorFlags.exe (narzędzie konwersji CorFlags)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) bez żadnych opcji. CorFlags.exe umożliwia również zmienić stan platformy pliku .exe lub .dll. Nagłówku CLR zestawu Visual Studio ma ustawiony numer wersji środowiska uruchomieniowego głównych do 2 i ustawiony numer wersji środowiska uruchomieniowego pomocnicza do 5. Aplikacje, które mają wersję pomocniczą środowiska uruchomieniowego, równa 0, są traktowane jako starsze aplikacje i są zawsze wykonywane w emulatorze WOW64.  
  
 Aby programowo wykonywać zapytania, .exe lub .dll, aby zobaczyć, czy jest przeznaczona do uruchamiania tylko na danej platformie lub w emulatorze WOW64, należy użyć <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metody.
