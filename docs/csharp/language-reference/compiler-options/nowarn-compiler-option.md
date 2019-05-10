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
ms.openlocfilehash: b455a2f719e7350c51cf4a1f095d4669529d0e5e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592813"
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
