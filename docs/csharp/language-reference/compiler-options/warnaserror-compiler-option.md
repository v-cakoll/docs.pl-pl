---
title: -warnaserror (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503478"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror (Opcje kompilatora C#)
Opcja **-warnaserror+** traktuje wszystkie ostrzeżenia jako błędy  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszelkie komunikaty, które zwykle są zgłaszane jako ostrzeżenia są zgłaszane jako błędy, a proces kompilacji jest zatrzymany (nie są tworzone żadne pliki wyjściowe).  
  
 Domyślnie **-warnaserror-** jest w mocy, co powoduje ostrzeżenia, aby nie zapobiec generowaniu pliku wyjściowego. **-warnaserror**, który jest taki sam jak **-warnaserror +**, powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Opcjonalnie, jeśli chcesz, aby tylko kilka określonych ostrzeżeń było traktowanych jako błędy, możesz określić oddzieloną przecinkami listę numerów ostrzeżeń, które należy traktować jako błędy. Zestaw wszystkich ostrzeżeń nullability można określić za pomocą skrótu **nullable.**
  
 Użyj [-warn,](./warn-compiler-option.md) aby określić poziom ostrzeżeń, które mają być wyświetlane przez kompilator. Użyj [-nowarn,](./nowarn-compiler-option.md) aby wyłączyć niektóre ostrzeżenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Zmodyfikuj **właściwości Treat Warnings As Errors.**  
  
 Aby programowo ustawić tę opcję <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `in.cs` i mają kompilator a nie wyświetlać żadnych ostrzeżeń:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
