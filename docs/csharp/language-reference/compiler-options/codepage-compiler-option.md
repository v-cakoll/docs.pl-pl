---
title: -codepage (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
ms.openlocfilehash: 3352e7fc446ace391540360a3b6b36d604ca5f13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173760"
---
# <a name="-codepage-c-compiler-options"></a>-codepage (Opcje kompilatora C#)
Ta opcja określa, która strona kodowa ma być używana podczas kompilacji, jeśli wymagana strona nie jest bieżącą domyślną stroną kodową systemu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 Identyfikator strony kodowej do użycia dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator najpierw spróbuje zinterpretować wszystkie pliki źródłowe jako UTF-8. Jeśli pliki kodu źródłowego są w kodowaniu innym niż UTF-8 i używają znaków innych niż 7-bitowe znaki ASCII, użyj opcji **-codepage,** aby określić, która strona kodowa ma być używana. **-codepage** ma zastosowanie do wszystkich plików kodu źródłowego w kompilacji.  

 Zobacz [GetCPInfo,](/windows/desktop/api/winnls/nf-winnls-getcpinfo) aby uzyskać informacje na temat znajdowania stron kodowych, które są obsługiwane w systemie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
