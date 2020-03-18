---
title: -nowarn (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606617"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (Opcje kompilatora C#)
Opcja **-nowarn** umożliwia wyłączenie kompilatora z wyświetlania co najmniej jednego ostrzeżenia. Oddziel wiele numerów ostrzegawczych przecinkiem.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Liczba (s) ostrzeżenie, które mają kompilator pominąć.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko numeryczne część identyfikatora ostrzeżenia. Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.  
  
 Kompilator będzie dyskretnie ignorować numery ostrzeżeń przekazywane do, `-nowarn` które były prawidłowe w poprzednich wersjach, ale które zostały usunięte z kompilatora. Na przykład CS0679 był prawidłowy w kompilatorze w programie Visual Studio .NET 2002, ale został następnie usunięty.  
  
 Opcja ta nie może zostać `-nowarn` wygaszona przez następujące ostrzeżenia:  
  
- Ostrzeżenie o kompilatorze (poziom 1) CS2002  
  
- Ostrzeżenie o kompilatorze (poziom 1) CS2023  
  
- Ostrzeżenie o kompilatorze (poziom 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij stronę **Właściwości kompilacji.**  
  
3. Zmodyfikuj właściwość **Pomiń ostrzeżenia.**  
  
 Aby uzyskać informacje dotyczące programowego ustawiania tej <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>opcji kompilatora, zobacz .  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
- [Błędy kompilatora Języka C#](../compiler-messages/index.md)
