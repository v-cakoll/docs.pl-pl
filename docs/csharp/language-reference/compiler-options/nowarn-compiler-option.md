---
title: -nowarn (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2784e63b7c1e67b32fc448b4b112ad0252b1abd9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (opcje kompilatora C#)
**- Nowarn** opcja pozwala pominąć kompilatora przy wyświetlaniu co najmniej jedno ostrzeżenie. Wiele numerów ostrzeżeń, które należy oddzielić przecinkami.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Numery ostrzeżeń, które kompilator, aby pominąć.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko numeryczna część identyfikatora ostrzeżenie. Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.  
  
 Kompilator będzie dyskretne ignorowanie numerów ostrzeżeń, które przekazany do `-nowarn` , które były nieprawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora. Na przykład CS0679 jest prawidłowe w kompilatorze w Visual Studio .NET 2002, ale później został usunięty.  
  
 Nie można pominąć następujące ostrzeżenia przez `-nowarn` opcji:  
  
-   Kompilator CS2002 ostrzegawcze (poziom 1)  
  
-   Kompilator CS2023 ostrzegawcze (poziom 1)  
  
-   Kompilator CS2029 ostrzegawcze (poziom 1)  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz **właściwości** strony dla projektu. Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Modyfikowanie **pomijania ostrzeżeń** właściwości.  
  
 Aby dowiedzieć się, jak ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)  
 [Błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md)
