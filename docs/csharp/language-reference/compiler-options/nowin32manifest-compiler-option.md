---
title: -nowin32manifest (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602714"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (C# opcje kompilatora)
Użyj opcji **-nowin32manifest** , aby nakazać kompilatorowi nie osadzenie żadnego manifestu aplikacji w pliku wykonywalnym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, aplikacja będzie podlegać wirtualizacji w systemie Windows Vista, o ile nie podajesz manifestu aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.  
  
 W programie Visual Studio Ustaw tę opcję na stronie **właściwości aplikacji** , wybierając opcję **Utwórz aplikację bez manifestu** na liście rozwijanej **manifestu** . Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektuC#()](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Aby uzyskać więcej informacji na temat tworzenia manifestu, zobacz [-C# WIN32MANIFEST (opcje kompilatora)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
