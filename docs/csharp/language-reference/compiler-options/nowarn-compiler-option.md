---
title: -nowarn (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606617"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# opcje kompilatora)
Opcja **-nowarn** pozwala pominąć kompilator z wyświetlania jednego lub kilku ostrzeżeń. Oddziel wiele numerów ostrzeżeń przecinkami.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Liczba ostrzeżeń, które kompilator ma pominąć.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko liczbowe części identyfikatora ostrzeżenia. Na przykład jeśli chcesz pominąć CS0028, możesz określić `-nowarn:28`.  
  
 Kompilator zignoruje w sposób cichy odpowiednie numery `-nowarn` ostrzeżeń, które były prawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora. Na przykład CS0679 był prawidłowy w kompilatorze w Visual Studio .NET 2002, ale został następnie usunięty.  
  
 Następujące ostrzeżenia nie mogą być pomijane przez `-nowarn` opcję:  
  
- Ostrzeżenie kompilatora (poziom 1) CS2002  
  
- Ostrzeżenie kompilatora (poziom 1) CS2023  
  
- Ostrzeżenie kompilatora (poziom 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** dla projektu. Aby uzyskać szczegółowe informacje, zobacz [stronę Kompilacja, ProjektantC#projektu ()](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij stronę właściwości **kompilacja** .  
  
3. Zmodyfikuj właściwość **Pomijaj ostrzeżenia** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>tę opcję kompilatora, zobacz.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Błędy kompilatora C#](../compiler-messages/index.md)
