---
title: '-docelowych: exe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 515359b7a8a76e20896389b308df34db03f3798d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-targetexe-c-compiler-options"></a>-docelowych: exe (opcje kompilatora C#)
**-Docelowych: exe** opcja powoduje, że kompilator, aby utworzyć pliku wykonywalnego (EXE), aplikacji konsolowej.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Uwagi  
 **-Docelowych: exe** opcja jest włączona domyślnie. Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe.  
  
 Użyj [-docelowych: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu dla systemu Windows.  
  
 Chyba że określono inaczej [— limit](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Kiedy określona w wierszu polecenia, wszystkie pliki do następnej **-out** lub **-docelowych: moduł** opcji są używane do tworzenia pliku .exe  
  
 Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe. [— Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) — opcja kompilatora pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **Output typu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Każdy z następujących wierszy polecenia zostanie skompilowany `in.cs`, tworzenie `in.exe`:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [-docelowego (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
