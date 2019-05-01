---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e36e9187ab8c9c2b4950a66ff8ff3fc93adbd9c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774832"
---
# <a name="-win32icon"></a>-win32icon
Wstawia plik .ico, w pliku wyjściowym. Ten plik .ico, który reprezentuje plik wyjściowy w **Eksploratora plików**.  
  
## <a name="syntax"></a>Składnia  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`filename`|Plik .ico, należy dodać do pliku wyjściowego. Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.|  
  
## <a name="remarks"></a>Uwagi  
 Plik .ico, który można utworzyć przy użyciu kompilatora zasobów Windows firmy Microsoft (RC). Kompilator zasobów jest wywoływane, gdy kompilujesz program Visual C++; plik .ico, który jest tworzony z pliku .rc. `-win32icon` i `-win32resource` opcje wykluczają się wzajemnie.  
  
 Zobacz [- linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów, lub [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) można dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów. Zobacz [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować plik res.  
  
|Aby ustawić - win32icon w środowisku IDE programu Visual Studio|  
|---|  
|1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **aplikacji** kartę.<br />3.  Zmodyfikuj wartość w **ikonę** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `In.vb` i dołącza plik .ico `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
