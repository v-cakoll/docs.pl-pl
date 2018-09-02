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
ms.openlocfilehash: 3ab52d541c169850f6ae7ba7e7cfded290f890e7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420622"
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
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
