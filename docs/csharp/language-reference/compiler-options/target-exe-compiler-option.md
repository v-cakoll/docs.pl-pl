---
title: '-docelowych: exe (opcje kompilatora C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b66ab51b30e17ab2f34f88158c3f6095e185468d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="targetexe-c-compiler-options"></a>/target:exe (opcje kompilatora C#)
**/Target: exe** opcja powoduje, że kompilator, aby utworzyć pliku wykonywalnego (EXE), aplikacji konsolowej.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/target:exe  
```  
  
## <a name="remarks"></a>Uwagi  
 **/Target: exe** opcja jest włączona domyślnie. Będzie można utworzyć pliku wykonywalnego z rozszerzeniem .exe.  
  
 Użyj [/target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu dla systemu Windows.  
  
 Chyba że określono inaczej [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Jeśli określona w wierszu polecenia, wszystkie pliki do następnej **/out** lub **/target: module** opcji są używane do tworzenia pliku .exe  
  
 Jeden i tylko jeden **Main** metody jest wymagane pliki kodu źródłowego, które są łączone w pliku .exe. [/Main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) — opcja kompilatora pozwala określić, która klasa zawiera **Main** metody w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **Output typu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Każdy z następujących wierszy polecenia zostanie skompilowany `in.cs`, tworzenie `in.exe`:  
  
```console  
csc /target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [/ TARGET (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
