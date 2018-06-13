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
ms.openlocfilehash: 5505971ad9a6920124dd4d8c12642a5e4e346322
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214095"
---
# <a name="-bugreport-c-compiler-options"></a>-bugreport (opcje kompilatora C#)
Określa, czy informacje o debugowaniu powinna zostać umieszczona w pliku w celu późniejszej analizy.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-bugreport:file  
```  
  
## <a name="arguments"></a>Argumenty  
 `file`  
 Nazwa pliku, który ma zawierać raport o usterce.  
  
## <a name="remarks"></a>Uwagi  
 **- Bugreport** opcja określa, że następujące informacje powinny być umieszczone w `file`:  
  
-   Kopiowanie wszystkich plików kodu źródłowego w kompilacji.  
  
-   Lista opcje kompilatora używane w kompilacji.  
  
-   Informacje o wersji o kompilatora, czas wykonywania i systemu operacyjnego.  
  
-   Zestawy występujące w odwołaniach i modułów, zapisany jako cyfr szesnastkowych, z wyjątkiem zestawy, które są dostarczane z programu .NET Framework i zestawu SDK.  
  
-   Kompilator output, jeśli istnieje.  
  
-   Opis problemu, który pojawi się monit o.  
  
-   Opis sposobu uważasz, że problem należy ustalić, który pojawi się monit o.  
  
 Jeśli ta opcja jest używana z **- errorreport: wiersz** lub **- errorreport: wysyłanie**, informacje w pliku będą wysyłane do firmy Microsoft Corporation.  
  
 Ponieważ kopię wszystkich plików kodu źródłowego zostaną umieszczone w `file`, należy odtworzyć kod podejrzanych wada najkrótszy program możliwe.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
 Zwróć uwagę, że zawartość wygenerowanego pliku uwidaczniać kodu źródłowego, co może spowodować ujawnienie informacji przypadkowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [-errorreport (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/errorreport-compiler-option.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
