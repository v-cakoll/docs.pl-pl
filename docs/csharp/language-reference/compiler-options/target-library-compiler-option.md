---
title: '-docelowych: library (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 39f6ad5839f7ca12b023502a3fc1ccde52e70899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-targetlibrary-c-compiler-options"></a>-docelowych: library (opcje kompilatora C#)
**-Docelowa: Biblioteka** opcja powoduje, że kompilator, aby utworzyć biblioteki dołączanej (dynamicznie DLL), zamiast pliku wykonywalnego (EXE).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik DLL, który zostanie utworzony z rozszerzeniem dll.  
  
 Chyba że określono inaczej [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.  
  
 Kiedy określona w wierszu polecenia, wszystkie pliki do następnej **-out** lub **— docelowych: moduł** opcji są używane do tworzenia pliku dll.  
  
 Podczas tworzenia pliku .dll [Main](../../../csharp/programming-guide/main-and-command-args/index.md) — metoda nie jest wymagana.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **Output typu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs`, tworzenie `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-docelowego (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
