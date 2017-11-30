---
title: '-docelowych: winexe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
caps.latest.revision: "11"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e155c64689f34c89443c7ff0a3dee38d6c190fcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetwinexe-c-compiler-options"></a>/target:winexe (opcje kompilatora C#)
**/Target: winexe** opcji powoduje, że kompilator do utworzenia pliku wykonywalnego (EXE), program systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/target:winexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe. Windows program to taki, który udostępnia interfejs użytkownika z biblioteki .NET Framework lub z interfejsami API Win32.  
  
 Użyj [/target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) do tworzenia aplikacji konsoli.  
  
 Chyba że określono inaczej [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Jeśli określona w wierszu polecenia, wszystkie pliki, aż do następnego **/out** lub [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji są używane do tworzenia programu systemu Windows.  
  
 Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe. [/Main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **Output typu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs` do programu systemu Windows:  
  
```console  
csc /target:winexe in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ TARGET (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
