---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: d713a63c9503581f38048fe79c559883dc96efd2
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50040137"
---
# <a name="-libpath"></a>-libpath
Określa lokalizację przywoływanych zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`dirList`|Wymagana. Rozdzielana średnikami lista katalogów dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w jednym bieżący katalog roboczy (katalog, z którego są wywołując kompilator) lub katalogu systemu wykonywalnych języka wspólnego. Jeśli nazwa katalogu zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").|  
  
## <a name="remarks"></a>Uwagi  
 `-libpath` Opcja określa lokalizację zestawów odwołuje się [— dokumentacja](../../../visual-basic/reference/command-line-compiler/reference.md) opcji.  
  
 Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1.  Bieżący katalog roboczy. Jest to katalog, w którym kompilator jest wywoływany.  
  
2.  Katalogu środowiska CLR systemu.  
  
3.  Katalogi określone przez `/libpath`.  
  
4.  Katalogi określone przez zmienną środowiskową LIB.  
  
 `-libpath` Opcja jest dodatku; Określanie on więcej niż jeden raz dołącza do dowolnych wartości wcześniejsze.  
  
 Użyj `-reference` do określenia odwołania do zestawu.  
  
|Aby ustawić/libpath — w programie Visual Studio zintegrowane środowisko projektowe|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **odwołania** kartę.<br />3.  Kliknij przycisk **odwoływać się do ścieżki...**  przycisku.<br />4.  W **ścieżki odwołania** okna dialogowego wprowadź nazwę katalogu, w **Folder:** pole.<br />5.  Kliknij przycisk **Dodaj Folder**.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` do tworzenia pliku .exe. Kompilator w katalogu roboczym, w katalogu głównym dysku C: i w katalogu nowych zestawów na dysku C: szuka odwołania do zestawu.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zestawy i globalna pamięć podręczna zestawów](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
