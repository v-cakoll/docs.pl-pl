---
title: Aplikacje 64-bitowe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [C++], 64-bit
- 64-bit applications [C++]
- 64-bit programming [C++]
ms.assetid: fd4026bc-2c3d-4b27-86dc-ec5e96018181
caps.latest.revision: "53"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1ee85512cde0ce50e6a5c34cc5f6acc531c24bc0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="64-bit-applications"></a>Aplikacje 64-bitowe
Podczas kompilowania aplikacji można określić, czy ma być uruchamiany w systemie Windows 64-bitowym systemie operacyjnym jako natywnych aplikacji lub w emulatorze WOW64 (32-bitowego w systemie Windows 64-bitowe). WOW64 jest środowisko zgodności, które umożliwia 32-bitowej aplikacji do uruchomienia w 64-bitowym systemie. WOW64 jest uwzględniona we wszystkich wersjach 64-bitowego systemu operacyjnego Windows.  
  
## <a name="running-32-bit-vs-64-bit-applications-on-windows"></a>Uruchomiona 32-bitowej wersji programu vs. Aplikacje 64-bitowe w systemie Windows  
 Wszystkie aplikacje, które są wbudowane w program .NET Framework 1.0 lub 1.1 są traktowane jako 32-bitowej aplikacji na 64-bitowym systemie operacyjnym i są zawsze wykonywane w ramach WOW64 i 32-bitowe środowisko uruchomieniowe języka wspólnego (CLR). 32-bitowych aplikacji, które są wbudowane w [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)] lub nowsze wersje również uruchomić w emulatorze WOW64 w systemach 64-bitowych.  
  
 Visual Studio instaluje 32-bitowej wersji środowiska CLR na x86 komputera i 32-bitowej wersji i odpowiednich 64-bitowej wersji środowiska CLR na komputerze 64-bitowego systemu Windows. (Ponieważ Visual Studio jest 32-bitowej aplikacji, gdy jest zainstalowany w 64-bitowym systemie, zostanie uruchomiony w emulatorze WOW64.)  
  
> [!NOTE]
>  Z powodu projektu x86 emulacji i podsystemu WOW64 rodziny procesora Itanium, aplikacje są ograniczone do wykonania w jednym procesorze. Te czynniki zmniejszyć wydajność i skalowalność aplikacji .NET Framework 32-bitowe, które działają w systemach opartych na architekturze Itanium. Firma Microsoft zaleca użycie [!INCLUDE[net_v40_long](../../includes/net-v40-long-md.md)], która obejmuje macierzystą obsługę 64-bitowego dla systemów opartych na procesorze Itanium, aby zwiększyć wydajność i skalowalność.  
  
 Domyślnie po uruchomieniu zarządzanej aplikacji 64-bitowym na 64-bitowym systemie operacyjnym Windows, można utworzyć obiektu nie więcej niż 2 gigabajty (GB). Jednak w [!INCLUDE[net_v45](../../includes/net-v45-md.md)], możesz zwiększyć ten limit.  Aby uzyskać więcej informacji, zobacz [ \<gcallowverylargeobjects — > elementu](../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md).  
  
 Wiele zestawów Uruchom identycznie zarówno CLR 32-bitowe i 64-bitowym CLR. Jednak niektóre programy mogą zachowywać się inaczej, w zależności od środowiska CLR, jeśli zawierają one przynajmniej jednej z następujących czynności:  
  
-   Struktury zawierające elementy członkowskie, które zmiany rozmiaru w zależności od platformy (na przykład dowolny typ wskaźnika).  
  
-   Arytmetyki wskaźnika, który obejmuje stałą rozmiary.  
  
-   Nieprawidłowa platforma wywołania lub deklaracje COM, które używają `Int32` dla dojść zamiast `IntPtr`.  
  
-   Kod, który rzutuje `IntPtr` do `Int32`.  
  
 Aby uzyskać więcej informacji na temat portu 32-bitowej aplikacji na 64-bitowym CLR, zobacz [kodu zarządzanego migracji 32-bitowej do 64-bitowej](https://msdn.microsoft.com/library/ms973190.aspx).  
  
## <a name="general-64-bit-programming-information"></a>Ogólne informacje nt. programowania 64-bitowego  
 Aby uzyskać ogólne informacje o programowanie 64-bitowe można znaleźć w następujących dokumentach:  
  
-   Aby uzyskać więcej informacji na temat 64-bitowej wersji środowiska CLR na komputerze 64-bitowego systemu Windows, temacie [Centrum deweloperów .NET Framework](http://go.microsoft.com/fwlink/?LinkId=37079) w witrynie MSDN.  
  
-   W [!INCLUDE[winsdkshort](../../includes/winsdkshort-md.md)] dokumentacji, zobacz [przewodnik programowania w języku dla 64-bitowym systemie Windows](http://go.microsoft.com/fwlink/p/?LinkId=253512).  
  
-   Aby dowiedzieć się, jak pobrać 64-bitowej wersji środowiska CLR, zobacz [.NET Framework Developer Center pobiera](http://go.microsoft.com/fwlink/?LinkId=50953) w witrynie MSDN.  
  
-   Informacje dotyczące obsługi programu Visual Studio do tworzenia aplikacji 64-bitowych, zobacz [obsługi programu Visual Studio IDE 64-bitowych](http://msdn.microsoft.com/library/b08ff3ad-c6fd-468f-94d5-01a61aab6833).  
  
## <a name="compiler-support-for-creating-64-bit-applications"></a>Obsługa kompilatora do tworzenia aplikacji 64-bitowych  
 Domyślnie podczas tworzenia aplikacji na 32-bitowy lub 64-bitowym komputerze, za pomocą architektury .NET aplikacja będzie uruchamiana na komputerze 64-bitowych jako aplikacji natywnej (to znaczy nie w emulatorze WOW64). W poniższej tabeli wymieniono dokumenty, które wyjaśniono, jak używać kompilatory Visual Studio do tworzenia aplikacji 64-bitowych, które będą działać jako natywne WOW64, lub obie.  
  
|Kompilatora|— Opcja kompilatora|  
|--------------|---------------------|  
|Visual Basic|[/ platform (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/platform.md)|  
|Visual C#|[/ platform (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/platform-compiler-option.md)|  
|Visual C++|Możesz utworzyć niezależny od platformy, aplikacje język pośredni (MSIL) firmy Microsoft przy użyciu **/CLR: Safe**. Aby uzyskać więcej informacji, zobacz [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](/cpp/build/reference/clr-common-language-runtime-compilation).<br /><br /> Visual C++ obejmuje oddzielne kompilatora dla poszczególnych 64-bitowym systemie operacyjnym. Aby uzyskać więcej informacji o tym, jak używać programu Visual C++ do tworzenia natywnych aplikacji działających w 64-bitowym systemie operacyjnym Windows, temacie [64-bit — programowanie](http://msdn.microsoft.com/library/h2k70f3s\(v=vs.80\)).|  
  
## <a name="determining-the-status-of-an-exe-file-or-dll-file"></a>Określanie stanu pliku .exe lub pliku .dll  
 Aby określić, czy pliku .exe lub .dll jest przeznaczony do uruchamiania tylko na danej platformie lub w emulatorze WOW64, użyj [CorFlags.exe (narzędzie konwersji CorFlags)](../../docs/framework/tools/corflags-exe-corflags-conversion-tool.md) bez żadnych opcji. CorFlags.exe umożliwia również zmianę stanu platformy pliku .exe lub .dll. Nagłówku CLR zestawu Visual Studio ma ustawiony numer wersji głównej środowiska uruchomieniowego do 2 i ustawiony numer wersję pomocniczą środowiska uruchomieniowego do 5. Aplikacje, które mają wersję pomocniczą środowiska uruchomieniowego równa 0, są traktowane jako starsze aplikacje i są zawsze wykonywane w emulatorze WOW64.  
  
 Aby sprawdzić programowo .exe lub dll, aby zobaczyć, czy jest przeznaczony do uruchamiania tylko na danej platformie lub w emulatorze WOW64, użyj <xref:System.Reflection.Module.GetPEKind%2A?displayProperty=nameWithType> metody.
