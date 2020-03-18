---
title: -nowin32manifest (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
ms.openlocfilehash: 8820410bfdbce2f9986605f37af4d14957471126
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602714"
---
# <a name="-nowin32manifest-c-compiler-options"></a>-nowin32manifest (Opcje kompilatora C#)
Użyj opcji **-nowin32manifest,** aby poinstruować kompilator, aby nie osadzał żadnego manifestu aplikacji w pliku wykonywalnym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowin32manifest  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, aplikacja będzie podlegać wirtualizacji w systemie Windows Vista, chyba że podasz manifest aplikacji w pliku zasobu Win32 lub podczas późniejszego kroku kompilacji.  
  
 W programie Visual Studio ustaw tę opcję na stronie **Właściwości aplikacji,** wybierając opcję **Utwórz aplikację bez manifestu** na liście rozwijanej **Manifest.** Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Aby uzyskać więcej informacji na temat tworzenia manifestu, zobacz [-win32manifest (Opcje kompilatora C#)](./win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
