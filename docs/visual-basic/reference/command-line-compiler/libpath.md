---
title: -libpath
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cff59d9b406045b4522d3a7d6e85528513214635
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-libpath"></a>-libpath
Określa lokalizację zestawów występujących w odwołaniach.  
  
## <a name="syntax"></a>Składnia  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`dirList`|Wymagany. Rozdzielana średnikami lista katalogów dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w jednym bieżący katalog roboczy (katalogu, z którego są wywoływanie kompilatora) lub środowisko uruchomieniowe języka wspólnego w katalogu systemowym. Jeśli nazwa katalogu zawiera spację, nazwę należy ująć w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-libpath` Opcji określa lokalizację zestawów odwołuje się [— odwołanie](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.  
  
 Kompilator szuka odwołań do zestawu, które nie są w pełni kwalifikowana w następującej kolejności:  
  
1.  Bieżący katalog roboczy. To jest katalog, z którego jest wywoływany przez kompilator.  
  
2.  Katalogu środowiska CLR systemu.  
  
3.  Katalogi określone przez `/libpath`.  
  
4.  Katalogi określonej przez zmienną środowiskową LIB.  
  
 `-libpath` Jest opcja dodawania; Określanie on więcej niż raz dołącza wszystkie wcześniejsze wartości.  
  
 Użyj `-reference` do określenia odwołania do zestawu.  
  
|Aby ustawić/libpath w programie Visual Studio zintegrowane środowisko deweloperskie|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **odwołania** kartę.<br />3.  Kliknij przycisk **ścieżek odwołania...** przycisku.<br />4.  W **ścieżek odwołania** okna dialogowego wprowadź nazwę katalogu w **Folder:** pole.<br />5.  Kliknij przycisk **dodać Folder**.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` do utworzenia pliku .exe. Kompilator w katalogu roboczym, w katalogu głównym dysku C: i w katalogu zestawy nowego dysku C: szuka odwołań do zestawu.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
