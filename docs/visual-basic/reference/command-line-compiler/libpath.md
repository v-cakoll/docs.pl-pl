---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 9a5822a097828f818da020735c3822e86eb3236b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716638"
---
# <a name="-libpath"></a>-libpath
Określa lokalizację przywoływanych zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`dirList`|Wymagany. Rozdzielana średnikami lista katalogów, które mają być używane przez kompilator, jeśli zestaw, do którego się odwoływano, nie został znaleziony w bieżącym katalogu roboczym (katalog, z którego prowadzisz kompilator) lub katalog systemowy środowiska uruchomieniowego języka wspólnego. Jeśli nazwa katalogu zawiera spację, należy ująć ją w cudzysłów ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-libpath` Opcja określa lokalizację zestawów, do których odwołuje się opcja [-Reference](../../../visual-basic/reference/command-line-compiler/reference.md) .  
  
 Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1. Bieżący katalog roboczy. Jest to katalog, z którego wywołano kompilator.  
  
2. Katalog systemowy środowiska uruchomieniowego języka wspólnego.  
  
3. Katalogi określone przez `-libpath`.  
  
4. Katalogi określone przez zmienną środowiskową LIB.  
  
 `-libpath` Opcja jest dodatkiem; określenie go więcej niż raz dołącza do dowolnych wcześniejszych wartości.  
  
 Użyj `-reference` , aby określić odwołanie do zestawu.  
  
|Aby ustawić-LIBPATH w zintegrowanym środowisku programistycznym programu Visual Studio|  
|---|  
|1. zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **odwołania** .<br />3. kliknij przycisk **ścieżki odwołania...** .<br />4. w oknie dialogowym **ścieżki odwołań** wprowadź nazwę katalogu w polu **folder:** .<br />5. kliknij pozycję **Dodaj folder**.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` się w celu utworzenia pliku. exe. Kompilator przeszukuje katalog roboczy, w katalogu głównym dysku C: i w nowym katalogu zestawów dysku C: na potrzeby odwołań do zestawu.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też

- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
