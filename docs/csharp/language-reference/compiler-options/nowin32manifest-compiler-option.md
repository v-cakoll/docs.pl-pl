---
title: -nowin32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 357bc0dbe261a5d55b958fa0e8256920f050356d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516866"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (opcje kompilatora C#)
Użyj **-nowin32manifest** opcję, aby poinstruować kompilator, nie można osadzić manifest dowolnej aplikacji w pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, aplikacja będzie wirtualizacji w systemie Windows Vista, chyba że zapewniasz manifest aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.  
  
 W programie Visual Studio, należy ustawić tę opcję w **właściwość aplikacji** strony, wybierając **tworzenie aplikacji bez manifestu** opcji **manifestu** listy rozwijanej. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [-win32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
