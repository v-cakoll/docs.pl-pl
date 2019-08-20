---
title: -CodePage (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: c85cd8935bcefd1353707624052b62ee982f7b07
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69603053"
---
# <a name="-codepage-c-compiler-options"></a>-CodePage (C# opcje kompilatora)
Ta opcja określa, która strona kodowa ma być używana podczas kompilacji, jeśli wymagana Strona nie jest bieżącą domyślną stroną kodową systemu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 Identyfikator strony kodowej, który ma być używany dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator spróbuje najpierw zinterpretować wszystkie pliki źródłowe jako UTF-8. Jeśli pliki kodu źródłowego są w kodowaniu innym niż UTF-8 i są używane znaki inne niż 7-bitowe znaki ASCII, użyj opcji **-CodePage** , aby określić, która strona kodowa powinna być używana. **-CodePage** stosuje się do wszystkich plików kodu źródłowego w kompilacji.  
    
 Zobacz [GetCPInfo](/windows/desktop/api/winnls/nf-winnls-getcpinfo) , aby uzyskać informacje na temat sposobu znajdowania, które strony kodowe są obsługiwane w systemie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
