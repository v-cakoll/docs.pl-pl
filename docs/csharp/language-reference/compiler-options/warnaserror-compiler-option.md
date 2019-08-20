---
title: -warnaserror — (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606253"
---
# <a name="-warnaserror-c-compiler-options"></a>-warnaserror — (C# opcje kompilatora)
Opcja **-warnaserror — +** traktuje wszystkie ostrzeżenia jako błędy  
  
## <a name="syntax"></a>Składnia  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy, a proces kompilacji jest zatrzymany (nie skompilowano plików wyjściowych).  
  
 Domyślnie **— warnaserror — —** obowiązuje, co powoduje, że ostrzeżenia nie uniemożliwiają generowania pliku wyjściowego. **-warnaserror —** , która jest taka sama jak **-warnaserror — +** , powoduje, że ostrzeżenia są traktowane jako błędy.  
  
 Opcjonalnie, jeśli chcesz, aby tylko kilka określonych ostrzeżeń było traktowane jako błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które będą traktowane jako błędy.  
  
 Użyj [-warn](./warn-compiler-option.md) , aby określić poziom ostrzeżeń, które mają być wyświetlane w kompilatorze. Użyj [-nowarn](./nowarn-compiler-option.md) , aby wyłączyć niektóre ostrzeżenia.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Zmodyfikuj właściwość **Traktuj ostrzeżenia jako błędy** .  
  
 Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` i czy kompilator nie wyświetli żadnych ostrzeżeń:  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
