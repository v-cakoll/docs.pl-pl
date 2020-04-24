---
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: a6226b73d5d5d4d48a71afe39e8a546019d4c0bc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352344"
---
# <a name="-platform-visual-basic"></a>-Platforma (Visual Basic)
Określa, która wersja platformy środowiska uruchomieniowego języka wspólnego (CLR) może uruchomić plik wyjściowy.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`x86`|Kompiluje zestaw do uruchomienia przez 32-bitowe środowisko CLR zgodne z architekturą x86.|  
|`x64`|Kompiluje zestaw do uruchomienia przez 64-bitowe środowisko CLR na komputerze, który obsługuje zestaw instrukcji AMD64 lub EM64T.|  
|`Itanium`|Kompiluje zestaw do uruchomienia przez 64-bitowe środowisko CLR na komputerze z procesorem Itanium.|  
|`arm`|Kompiluje zestaw do uruchomienia na komputerze z procesorem ARM (Advanced RISC Machine).|  
|`anycpu`|Kompiluje zestaw do uruchomienia na dowolnej platformie. Aplikacja będzie działać jako aplikacja 32-bitowa w 32-bitowych wersjach systemu Windows i jako aplikacja 64-bitowa w systemie 64-bitowe wersje systemu Windows. Ta flaga jest wartością domyślną.|  
|`anycpu32bitpreferred`|Kompiluje zestaw do uruchomienia na dowolnej platformie. Aplikacja będzie działać jako aplikacja 32-bitowa na 32-bitowych i 64-bitowych wersjach systemu Windows. Ta flaga jest prawidłowa tylko dla plików wykonywalnych (. EXE) i wymaga .NET Framework 4,5.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `-platform` opcji, aby określić typ procesora docelowego dla pliku wyjściowego.  
  
 Ogólnie rzecz biorąc, zestawy .NET Framework, które zapisały w Visual Basic, będą uruchamiane niezależnie od platformy. Jednak istnieją sytuacje, które zachowują się inaczej na różnych platformach. Te typowe przypadki są następujące:  
  
- Struktury zawierające elementy członkowskie, które zmieniają rozmiar w zależności od platformy, takie jak dowolny typ wskaźnika.  
  
- Arytmetyczny wskaźnik obejmujący stałe rozmiary.  
  
- Nieprawidłowe wywołanie platformy lub deklaracje COM, `Integer` które są używane do <xref:System.IntPtr>obsługi zamiast.  
  
- <xref:System.IntPtr> Rzutowanie `Integer`na.  
  
- Użycie wywołania platformy lub międzyoperacyjności modelu COM ze składnikami, które nie istnieją na wszystkich platformach.  
  
 Opcja **-platform** ogranicza niektóre problemy, Jeśli wiesz, że masz założeń dotyczących architektury, w której kod będzie uruchamiany. Są to:  
  
- Jeśli zdecydujesz się na użycie platformy 64-bitowej, a aplikacja jest uruchamiana na komputerze 32-bitowym, komunikat o błędzie jest bardzo wcześniejszy i jest bardziej ukierunkowany na problem niż błąd, który wystąpi bez użycia tego przełącznika.  
  
- Jeśli ustawisz `x86` flagę dla opcji, a aplikacja zostanie uruchomiona na komputerze 64-bitowym, aplikacja zostanie uruchomiona w podsystemie WOW zamiast uruchamiać natywnie.  
  
 W 64-bitowym systemie operacyjnym Windows:  
  
- Zestawy skompilowane `-platform:x86` z programem będą wykonywane na 32-bitowym CLR uruchomionym w emulatorze WOW64.  
  
- Pliki wykonywalne skompilowane `-platform:anycpu` z użyciem zostaną wykonane na 64-bitowym środowisku CLR.  
  
- Biblioteka DLL skompilowana z programem `-platform:anycpu` zostanie wykonana w tym samym środowisku CLR co proces, w którym został załadowany.  
  
- Pliki wykonywalne, które są `-platform:anycpu32bitpreferred` kompilowane przy użyciu, zostaną wykonane na 32-bitowym CLR.  
  
 Aby uzyskać więcej informacji na temat sposobu tworzenia aplikacji do uruchamiania w 64-bitowej wersji systemu Windows, zobacz [64-bitowe aplikacje](../../../framework/64-bit-apps.md).  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a>Aby ustawić platformę w środowisku IDE programu Visual Studio  
  
1. W **Eksplorator rozwiązań**wybierz projekt, otwórz menu **projekt** , a następnie kliknij przycisk **Właściwości**.  
  
2. Na karcie **kompilacja** zaznacz lub wyczyść pole wyboru **Preferuj 32-bitowe** , lub na liście **docelowy procesor CPU** wybierz wartość.  
  
     Aby uzyskać więcej informacji, zobacz [Strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład ilustruje sposób użycia opcji `-platform` kompilatora.  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [-Target (Visual Basic)](target.md)
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
