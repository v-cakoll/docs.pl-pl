---
title: -codepage (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 7cbd3ec1b2d134106c6c9429341f5603444dac27
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693985"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (opcje kompilatora C#)
Ta opcja określa, które stronę kodową do użycia podczas kompilacji, jeśli strona wymagany jest bieżący domyślną stroną kodową systemu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 Identyfikator stronę kodową dla wszystkich plikach kodu źródłowego w kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilujesz jeden lub więcej plików kodu źródłowego, które nie zostały utworzone do użycia z domyślną stroną kodową na komputerze, możesz użyć **- strona kodowa** opcję, aby określić, stronę kodową, która będzie używana. **-codepage** ma zastosowanie do wszystkich plikach kodu źródłowego w kompilacji.  
  
 Jeśli pliki kodu źródłowego zostały utworzone za pomocą tej samej strony kodowej, która działa na komputerze lub w plikach kodu źródłowego zostały utworzone przy użyciu standardu UNICODE lub UTF-8, należy stosować **- strona kodowa**.  
  
 Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informacji na temat można znaleźć kodu strony są obsługiwane w systemie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
