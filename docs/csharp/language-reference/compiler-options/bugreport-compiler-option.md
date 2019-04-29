---
title: -bugreport (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /bugreport
helpviewer_keywords:
- /bugreport compiler option [C#]
- -bugreport compiler option [C#]
- bugreport compiler option [C#]
ms.assetid: f39665e3-4f6f-4357-88a2-3274c7bec0c1
ms.openlocfilehash: 63d64acc0d0a1ed90a722db75b467bd3ce5f260e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663014"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (opcje kompilatora C#)
Określa, że informacje o debugowaniu należy umieścić w pliku do późniejszej analizy.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Nazwa pliku który ma zawierać raport o usterce.  
  
## <a name="remarks"></a>Uwagi  
 **- Bugreport** opcja określa, że następujące informacje powinny być umieszczone w `file`:  
  
- Kopiowanie wszystkich plików kodu źródłowego w kompilacji.  
  
- Lista opcji kompilatora, używane w kompilacji.  
  
- Informacje o wersji dotyczące kompilatora, w czasie wykonywania i w systemie operacyjnym.  
  
- Zestawy referencyjne i moduły, zapisane jako cyfra szesnastkowa, z wyjątkiem zestawów, które są dostarczane z .NET Framework i zestaw SDK.  
  
- Kompilator dane wyjściowe, jeśli istnieje.  
  
- Opis problemu, który zostanie wyświetlony monit dla.  
  
- Opis sposobu Twoim zdaniem ten problem należy ustalić, który zostanie wyświetlony monit dla.  
  
 Jeśli ta opcja jest używana z **- errorreport: wiersz** lub **- errorreport: wysyłanie**, informacje w pliku będą wysyłane do firmy Microsoft Corporation.  
  
 Ponieważ kopię wszystkich plikach kodu źródłowego zostaną umieszczone w `file`, należy odtworzyć kod potencjalnie złośliwych programów wada najkrótszej program możliwe.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
 Należy zauważyć, że zawartość pliku wygenerowanego udostępnienia kodu źródłowego, co może spowodować ujawnienie informacji przypadkowego.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [-errorreport (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
