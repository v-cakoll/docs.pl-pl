---
title: -platformy (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 4455167577871cc6251c248d20e32f04ce11410e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671593"
---
# <a name="-platform-visual-basic"></a>-platformy (Visual Basic)
Określa, którą platformy wersję środowiska uruchomieniowego języka wspólnego (CLR) można uruchomić pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`x86`|Kompiluje zestawu do uruchomienia przez środowisko CLR 32-bitowy, x86 zgodny.|  
|`x64`|Kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.|  
|`Itanium`|Kompiluje zestaw do uruchomienia w 64-bitowym CLR na komputerze z procesorem Itanium.|  
|`arm`|Kompiluje zestaw do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Kompiluje zestaw można uruchomić na dowolnej platformie. Aplikacja jest uruchamiana jako aplikacja 32-bitowego na 32-bitowe wersje systemu Windows i jako aplikacji 64-bitowych w 64-bitowych wersjach systemu Windows. Ta flaga jest wartością domyślną.|  
|`anycpu32bitpreferred`|Kompiluje zestaw można uruchomić na dowolnej platformie. Aplikacja jest uruchamiana jako aplikacja 32-bitowa w 32-bitowych i 64-bitowych wersjach systemu Windows. Ta flaga jest prawidłowy tylko dla plików wykonywalnych (. Z rozszerzeniem EXE) i wymaga [!INCLUDE[net_v45](~/includes/net-v45-md.md)].|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `-platform` opcję, aby określić typ procesora przeznaczone dla pliku wyjściowego.  
  
 Ogólnie rzecz biorąc zestawów .NET Framework, napisany w języku Visual Basic uruchomi się takie same, niezależnie od platformy. Jednakże istnieją przypadki, które zachowują się inaczej, na różnych platformach. Następujące typowe przypadki są:  
  
-   Struktury, które zawierają składowe, które zmiany rozmiaru, w zależności od platformy, takie jak dowolny typ wskaźnika.  
  
-   Arytmetyczny wskaźnik, obejmującą stałych rozmiarach.  
  
-   Nieprawidłowa platforma wywołania lub deklaracji COM, które używają `Integer` dla dojścia, zamiast <xref:System.IntPtr>.  
  
-   Rzutowanie <xref:System.IntPtr> do `Integer`.  
  
-   Za pomocą platformy wywołania lub Usługa międzyoperacyjna modelu COM ze składnikami, które nie istnieją na wszystkich platformach.  
  
 **— Platforma** opcji ograniczą niektóre problemy, jeśli wiesz, że wprowadzono założenia dotyczące architektury, kod będzie działał na. W szczególności:  
  
-   Jeśli zdecydujesz się na docelowe platformy 64-bitowej, a aplikacja jest uruchamiana na komputerze 32-bitowym, komunikat o błędzie jest znacznie wcześniej i bardziej celem problem niż błąd występujący bez korzystania z tego przełącznika.  
  
-   Jeśli ustawisz `x86` flagi opcję i później uruchomieniu aplikacji na komputerze 64-bitowym, aplikacja zostanie uruchomiona w ramach podsystemu WOW zamiast działające natywnie.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
-   Zestawy skompilowane z `-platform:x86` zostanie wykonana w 32-bitowe środowisko CLR, uruchamianie w emulatorze WOW64.  
  
-   Pliki wykonywalne skompilowany przy użyciu `-platform:anycpu` zostanie wykonana w 64-bitowe środowisko CLR.  
  
-   Biblioteki DLL są kompilowane przy użyciu `-platform:anycpu` zostaną wykonane zgodnie z tym samym CLR jako proces, do którego on ładowany.  
  
-   Pliki wykonywalne, które są kompilowane przy użyciu `-platform:anycpu32bitpreferred` zostanie wykonana w 32-bitowe środowisko CLR.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia aplikacji do uruchamiania w 64-bitowej wersji systemu Windows, zobacz [aplikacji 64-bitowych](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Aby ustawić - platform w środowisku IDE programu Visual Studio  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt, otwórz **projektu** menu, a następnie kliknij przycisk **właściwości**.  
  
2.  Na **skompilować** kartę, zaznacz lub wyczyść **Preferuj 32-bitowe** pole wyboru lub w **Procesora docelowego** listy, wybierz wartość.  
  
     Aby uzyskać więcej informacji, zobacz [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób używania `-platform` — opcja kompilatora.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Zobacz także
- [/ TARGET (Visual Basic)](target.md)
- [Kompilator wiersza polecenia programu Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
