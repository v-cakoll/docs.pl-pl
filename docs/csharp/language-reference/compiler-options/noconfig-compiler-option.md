---
title: -noconfig (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 96321de5982a79cb073b658a84e0e580dd466539
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (opcje kompilatora C#)
**- Noconfig** opcja informuje kompilator, aby nie kompilacji z pliku csc.rsp, który jest znajduje się w i załadowane z tym samym katalogu co plik csc.exe.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 Pliku csc.rsp odwołuje się do wszystkich zestawów, które są dostarczane z programu .NET Framework. Rzeczywiste odwołań, które zawiera środowisko projektowe Visual Studio .NET są zależne od typu projektu.  
  
 Można zmodyfikować pliku csc.rsp i określ opcje kompilatora dodatkowe, które powinny być uwzględnione w każdej kompilacji z wiersza polecenia z csc.exe (z wyjątkiem **- noconfig** opcja).  
  
 Kompilator przetwarza opcje przekazane do **csc** ostatniego polecenia. W związku z tym każda opcja, w wierszu polecenia zastępuje ustawienie opcji tego samego pliku csc.rsp.  
  
 Jeśli nie chcesz kompilatora, aby wyszukać i użyj ustawień w pliku csc.rsp, określ **- noconfig**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
