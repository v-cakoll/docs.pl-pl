---
title: -nowarn (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 13bb50366d9c19751ef3387baf809ab69e27b5dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662629"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (opcje kompilatora C#)
**- Nowarn** opcja umożliwia pomijanie kompilatora wyświetlanie co najmniej jedno ostrzeżenie. Oddziel wiele numerów ostrzeżeń przecinkami.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Argumenty  
 `number1`, `number2`  
 Numery ostrzeżeń, które kompilator, aby pominąć.  
  
## <a name="remarks"></a>Uwagi  
 Należy określić tylko część numeryczna identyfikatora ostrzeżenia. Na przykład, jeśli chcesz pominąć CS0028, można określić `-nowarn:28`.  
  
 Kompilator będzie po cichu ignorować numery ostrzeżeń, przekazana do `-nowarn` , które były prawidłowe w poprzednich wersjach, ale zostały usunięte z kompilatora. Na przykład CS0679 jest prawidłowe w kompilator programu Visual Studio .NET 2002, ale później został usunięty.  
  
 Następujące ostrzeżenia nie może być pominięty przy `-nowarn` opcji:  
  
- Kompilatora (poziom 1) ostrzeżenie CS2002  
  
- Kompilatora (poziom 1) ostrzeżenie CS2023  
  
- Kompilatora (poziom 1) ostrzeżenie CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz **właściwości** strony dla projektu. Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Kliknij przycisk **kompilacji** stronę właściwości.  
  
3. Modyfikowanie **Pomiń ostrzeżenia** właściwości.  
  
 Aby dowiedzieć się, jak programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
- [Błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md)
