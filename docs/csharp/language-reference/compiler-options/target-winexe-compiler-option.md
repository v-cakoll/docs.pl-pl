---
title: '-target: winexe (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: f77137e3cc2f734435d3b1d391a303fcd3e16332
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520279"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target: winexe (opcje kompilatora C#)
**-Target: winexe** opcja powoduje, że kompilator, aby utworzyć plik wykonywalny (EXE), Windows program.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Zostanie utworzony plik wykonywalny z rozszerzeniem .exe. Windows program to taki, który zapewnia interfejs użytkownika z biblioteki .NET Framework lub za pomocą interfejsów API systemu Win32.  
  
 Użyj [-target: exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) do tworzenia aplikacji konsolowej.  
  
 Chyba że określono inaczej, za pomocą [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Po określeniu w wierszu polecenia, wszystkie pliki, aż do następnej **-się** lub [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji są używane do tworzenia programu Windows.  
  
 Jeden i tylko jeden **Main** metoda jest wymagany w plikach źródłowych kodu, które są kompilowane do pliku .exe. [-Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) pozwala określić, która klasa zawiera **Main** metodę, w przypadkach, gdy kod ma więcej niż jednej klasy za pomocą **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** stronę właściwości.  
  
3.  Modyfikowanie **typ danych wyjściowych** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` do programu Windows:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [-target (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
