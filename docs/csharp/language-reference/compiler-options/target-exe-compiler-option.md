---
title: '-target: exe (opcje kompilatora C#)'
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 4a2d3ea2bda56caf6a16f52877ad36b3947357e8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43391113"
---
# <a name="-targetexe-c-compiler-options"></a>-target: exe (opcje kompilatora C#)
**-Target: exe** opcja powoduje, że kompilator, aby utworzyć plik wykonywalny (EXE), aplikacji konsoli.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Uwagi  
 **-Target: exe** opcja w praktyce jest domyślnie. Zostanie utworzony plik wykonywalny z rozszerzeniem .exe.  
  
 Użyj [-target: winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) do utworzenia pliku wykonywalnego programu Windows.  
  
 Chyba że określono inaczej, za pomocą [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) opcji Nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody.  
  
 Po określeniu w wierszu polecenia, wszystkie pliki, aż do następnego **-out** lub **-target: module** opcji są używane do tworzenia pliku .exe  
  
 Jeden i tylko jeden **Main** metoda jest wymagany w plikach źródłowych kodu, które są kompilowane do pliku .exe. [-Głównego](../../../csharp/language-reference/compiler-options/main-compiler-option.md) — opcja kompilatora pozwala określić, która klasa zawiera **Main** metodę, w przypadkach, gdy kod ma więcej niż jednej klasy za pomocą **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** stronę właściwości.  
  
3.  Modyfikowanie **typ danych wyjściowych** właściwości.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Przykład  
 Każda z następujących wierszy polecenia zostanie skompilowany `in.cs`, tworzenie `in.exe`:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [-target (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)
