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
ms.openlocfilehash: b689a4bf0d8a1e57bf36f8ded7f2c9308f241670
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527306"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (opcje kompilatora C#)
**- Noconfig** opcji informuje kompilator, nie można skompilować przy użyciu pliku csc.rsp, który jest na terenie i ładowane z tym samym katalogu co plik csc.exe.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Uwagi  
 Pliku csc.rsp odwołuje się do wszystkich zestawów, które są dostarczane z programem .NET Framework. Rzeczywiste odwołań, które środowisko projektowe programu Visual Studio .NET zawiera zależą od typu projektu.  
  
 Można zmodyfikować pliku csc.rsp i określ opcje dodatkowe kompilatora, które powinny być uwzględnione w każdej kompilacji z wiersza polecenia przy użyciu csc.exe (z wyjątkiem **- noconfig** opcji).  
  
 Kompilator przetwarza opcje przekazywane do **csc** ostatnie polecenie. W związku z tym dowolnej opcji w wierszu polecenia zastępuje ustawienie opcji tego samego pliku csc.rsp.  
  
 Jeśli nie chcesz, aby kompilator, aby wyszukać i użyj ustawień w pliku csc.rsp, określ **- noconfig**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
