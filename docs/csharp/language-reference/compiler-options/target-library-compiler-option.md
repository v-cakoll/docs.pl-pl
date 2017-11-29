---
title: '-docelowych: library (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e66e2edd86dc4a1302b23dab07226a5d56cb79b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetlibrary-c-compiler-options"></a>/target:library (opcje kompilatora C#)
**/Target: Library** opcja powoduje, że kompilator, aby utworzyć biblioteki dołączanej (dynamicznie DLL) zamiast pliku wykonywalnego (EXE).  
  
## <a name="syntax"></a>Składnia  
  
```console  
/target:library  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik DLL, który zostanie utworzony z rozszerzeniem dll.  
  
 Jeżeli nie określono inaczej z [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.  
  
 Jeśli określona w wierszu polecenia, wszystkie pliki do następnej **/out** lub **/target: module** opcji są używane do tworzenia pliku dll.  
  
 Podczas tworzenia pliku .dll [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda nie jest wymagana.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **Output typu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs`, tworzenie `in.dll`:  
  
```console  
csc /target:library in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ TARGET (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
