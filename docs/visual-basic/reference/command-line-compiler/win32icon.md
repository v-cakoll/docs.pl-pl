---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: dc48a8f79aa04892c514917da00b8fd6489695b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593089"
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
  
 Zobacz [- linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) k odkazu plikiem zasobów .NET Framework lub [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) można dołączyć plik zasobu .NET Framework. Zobacz [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować plik res.  
  
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
