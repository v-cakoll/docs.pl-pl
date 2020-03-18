---
title: -noconfig (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602741"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (Opcje kompilatora C#)
Opcja **-noconfig** informuje kompilator, aby nie kompilował z plikiem csc.rsp, który znajduje się i ładował z tego samego katalogu co plik csc.exe.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik csc.rsp odwołuje się do wszystkich zestawów dostarczanych z platformą .NET Framework. Rzeczywiste odwołania, które zawiera środowisko programistyczne programu Visual Studio .NET, zależą od typu projektu.  
  
 Można zmodyfikować plik csc.rsp i określić dodatkowe opcje kompilatora, które powinny być zawarte w każdej kompilacji z wiersza polecenia z csc.exe (z wyjątkiem opcji **-noconfig).**  
  
 Kompilator przetwarza opcje przekazane do polecenia **csc** ostatnio. W związku z tym każda opcja w wierszu polecenia zastępuje ustawienie tej samej opcji w pliku csc.rsp.  
  
 Jeśli nie chcesz, aby kompilator szukał i używał ustawień w pliku csc.rsp, określ **-noconfig**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
