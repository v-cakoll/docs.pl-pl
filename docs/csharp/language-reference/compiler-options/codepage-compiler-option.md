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
ms.openlocfilehash: 59dc1abc3f678a4cf15543c11f9f200ff318ce8f
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876928"
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
 Kompilator spróbuje najpierw interpretować wszystkie pliki źródłowe w formacie UTF-8. Jeśli pliki kodu źródłowego są w kodowaniu innych niż UTF-8 i używać znaków innych niż 7-bitowe znaki ASCII, użyj **- strona kodowa** opcję, aby określić, stronę kodową, która będzie używana. **-codepage** ma zastosowanie do wszystkich plikach kodu źródłowego w kompilacji.  
    
 Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) informacji na temat można znaleźć kodu strony są obsługiwane w systemie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
