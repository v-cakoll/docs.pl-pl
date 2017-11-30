---
title: -nowin32manifest (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowin32manifest
helpviewer_keywords:
- nowin32manifest compiler option [C#]
- -nowin32manifest compiler option [C#]
- /nowin32manifest compiler option [C#]
ms.assetid: 6f06365b-b87b-46a2-b187-b3bfeaf4862d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e0d4697e0e14c84c4bc642521cf4f9cdf6a4ed6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nowin32manifest-c-compiler-options"></a>/nowin32manifest (opcje kompilatora C#)
Użyj **/nowin32manifest** opcję, aby poinstruować kompilatora nie do osadzania manifestu żadnych aplikacji w pliku wykonywalnego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/nowin32manifest  
```  
  
## <a name="remarks"></a>Uwagi  
 Gdy ta opcja jest używana, aplikacja podlegać wirtualizacji w systemie Windows Vista dopiero po podaniu manifest aplikacji w pliku zasobów Win32 lub w późniejszym kroku kompilacji.  
  
 W programie Visual Studio, ustaw tę opcję **aplikacji właściwości** strony, wybierając **Utwórz aplikację bez manifestu** opcji **manifestu** listy rozwijanej. Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Aby uzyskać więcej informacji o tworzeniu manifestu, zobacz [/win32manifest (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/win32manifest-compiler-option.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
