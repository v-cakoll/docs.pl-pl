---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: dff7e0c3eb696b9b18f4c4e59240a26c1cb9782c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408552"
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
 `-libpath`Opcja określa lokalizację zestawów, do których odwołuje się opcja [-Reference](reference.md) .  
  
 Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1. Bieżący katalog roboczy. Jest to katalog, z którego wywołano kompilator.  
  
2. Katalog systemowy środowiska uruchomieniowego języka wspólnego.  
  
3. Katalogi określone przez `-libpath` .  
  
4. Katalogi określone przez zmienną środowiskową LIB.  
  
 `-libpath`Opcja jest dodatkiem; określenie, że więcej niż raz dołącza do poprzednich wartości.  
  
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
- [Kompilator wiersza polecenia Visual Basic](index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
