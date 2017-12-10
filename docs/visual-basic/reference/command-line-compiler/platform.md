---
title: /platform (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
caps.latest.revision: "34"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4177b9da15bb89f37a7b3cbb27937e09d1c12635
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/09/2017
---
# <a name="platform-visual-basic"></a>/platform (Visual Basic)
Określa, która wersja platformy środowisko uruchomieniowe języka wspólnego (CLR) można uruchomić pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
/platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`x86`|Kompiluje z zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodna.|  
|`x64`|Kompiluje z zestawu do uruchomienia na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T przez 64-bitowym CLR.|  
|`Itanium`|Kompiluje z zestawu do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.|  
|`arm`|Kompiluje z zestawu do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja będzie działać jako aplikacja 32-bitowego w 32-bitowych wersjach systemu Windows i jako 64-bitowej aplikacji w 64-bitowych wersjach systemu Windows. Ta flaga jest wartością domyślną.|  
|`anycpu32bitpreferred`|Kompiluje używanemu zestawowi można uruchomić na dowolnej platformie. Aplikacja będzie działać jako aplikacja 32-bitowych na zarówno 32-bitowe i 64-bitowych wersjach systemu Windows. Ta flaga jest prawidłowa tylko dla plików wykonywalnych (. Wywołanie pliku EXE) i wymaga [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `/platform` opcję, aby określić typ procesora objęci pliku wyjściowego.  
  
 Ogólnie rzecz biorąc zestawy .NET Framework napisane w języku Visual Basic uruchomi się takie same, niezależnie od platformy. Istnieją jednak przypadki, które zachowują się inaczej na różnych platformach. Następujące typowe przypadki są:  
  
-   Struktury zawierające elementy członkowskie, które zmiany rozmiaru w zależności od platformy, takich jak dowolnego typu wskaźnika.  
  
-   Arytmetyki wskaźnika, który obejmuje stałą rozmiary.  
  
-   Nieprawidłowa platforma wywołania lub deklaracje COM, które używają `Integer` dla dojść zamiast <xref:System.IntPtr>.  
  
-   Rzutowanie <xref:System.IntPtr> do `Integer`.  
  
-   Przy użyciu platformy wywołania lub COM. ze składnikami, które nie istnieją na wszystkich platformach.  
  
 **/Platform** opcji będzie ograniczyć problemy, jeśli wiadomo, że zostały wykonane założenia o architekturze kodu zostanie uruchomiony na. W szczególności:  
  
-   Jeśli zdecydujesz się skorzystać z platformy 64-bitowe i uruchomieniu aplikacji na komputerze 32-bitowy, komunikat o błędzie jest znacznie wcześniej i bardziej celem problem niż błąd występujący bez użycia tego przełącznika.  
  
-   Jeśli ustawisz `x86` flagi opcji i następnie uruchomieniu aplikacji na komputerze 64-bitowym, aplikacja będzie działać w podsystemu WOW zamiast działać w sposób macierzysty.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
-   Zestawy są kompilowane przy użyciu `/platform:x86` będą wykonywane na 32-bitowego środowiska CLR uruchomione w emulatorze WOW64.  
  
-   Pliki wykonywalne skompilowane z `/platform:anycpu` będą wykonywane na 64-bitowym CLR.  
  
-   Biblioteki DLL są kompilowane przy użyciu `/platform:anycpu` będzie wykonywana na tej samej CLR jako proces, do którego ładowany.  
  
-   Pliki wykonywalne, które są kompilowane przy użyciu `/platform:anycpu32bitpreferred` będą wykonywane na 32-bitowym CLR.  
  
 Aby uzyskać więcej informacji dotyczących sposobu tworzenia aplikacji do uruchomienia w 64-bitowej wersji systemu Windows, zobacz [aplikacji 64-bitowych](../../../../docs/framework/64-bit-apps.md).  
  
### <a name="to-set-platform-in-the-visual-studio-ide"></a>Aby ustawić/platform w programie Visual Studio IDE  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, otwórz **projektu** menu, a następnie kliknij przycisk **właściwości**.  
  
     Aby uzyskać więcej informacji, zobacz [NIB: Zarządzanie właściwości projektu przy użyciu projektanta projektów](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).  
  
2.  Na **skompilować** karcie, zaznacz lub wyczyść **preferowane jest 32-bitowych** pole wyboru lub w **Procesora docelowej** listy, wybierz wartość.  
  
     Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia `/platform` — opcja kompilatora.  
  
```  
vbc /platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ TARGET (Visual Basic)](target.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](index.md)  
 [Kompilacja przykładów — wiersze poleceń](sample-compilation-command-lines.md)
