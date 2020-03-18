---
title: -bugreport (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 0989678be070910c410d71717fe66679e1b70557
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69603079"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (Opcje kompilatora C#)
Określa, że informacje debugowania powinny być umieszczane w pliku do późniejszej analizy.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Nazwa pliku, który ma zawierać raport o błędzie.  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-bugreport** określa, że następujące informacje `file`powinny być umieszczone w:  
  
- Kopia wszystkich plików kodu źródłowego w kompilacji.  
  
- Lista opcji kompilatora używanych w kompilacji.  
  
- Informacje o wersji kompilatora, czasu wykonywania i systemu operacyjnego.  
  
- Odwołuje się do zestawów i modułów, zapisane jako cyfry szesnastkowe, z wyjątkiem zestawów, które są dostarczany z .NET Framework i SDK.  
  
- Dane wyjściowe kompilatora, jeśli istnieje.  
  
- Opis problemu, do którego zostaniesz poproszony.  
  
- Opis tego, jak twoim zdaniem problem powinien zostać rozwiązany, o który zostaniesz poproszony.  
  
 Jeśli ta opcja jest używana z **-errorreport:prompt** lub **-errorreport:send,** informacje w pliku zostaną wysłane do firmy Microsoft Corporation.  
  
 Ponieważ kopia wszystkich plików kodu źródłowego `file`zostanie umieszczona w , można odtworzyć podejrzewaną wadę kodu w jak najkrótszym programie.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
 Należy zauważyć, że zawartość wygenerowanego pliku uwidacznia ją kodem źródłowym, co może spowodować nieumyślne ujawnienie informacji.  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [-errorreport (Opcje kompilatora C#)](./errorreport-compiler-option.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
