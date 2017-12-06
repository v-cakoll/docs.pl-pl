---
title: -codepage (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1e17622256ca6a0344797ba16e007ba6feb8f873
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="codepage-c-compiler-options"></a>/codepage (opcje kompilatora C#)
Ta opcja określa, które stronę kodową do używania podczas kompilacji, jeśli wymagane strony nie jest bieżącym domyślna strona kodowa systemu.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/codepage:id  
```  
  
## <a name="arguments"></a>Argumenty  
 `id`  
 Identyfikator strony kodowej do użycia dla wszystkich plików kodu źródłowego w kompilacji.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli kompilacja jeden lub więcej plików kodu źródłowego, które nie zostały utworzone do użycia na domyślną stronę kodową na komputerze, możesz użyć **/CODEPAGE** opcję, aby określić stronę kodową, która będzie używana. **/ CodePage** ma zastosowanie do wszystkich plików kodu źródłowego w sieci kompilacji.  
  
 Jeśli zostały utworzone pliki kodu źródłowego za pomocą tego samego stronę kodową, która działa na komputerze lub jeśli pliki kodu źródłowego zostały utworzone z UNICODE lub UTF-8, należy stosować **/CODEPAGE**.  
  
 Zobacz [GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) informacji na temat znajdowania które kodu strony są obsługiwane w tym systemie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
