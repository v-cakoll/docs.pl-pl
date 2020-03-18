---
title: -target:winexe (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 981f1b0b6ca9f708bb022a3662ab181a4f472040
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606378"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target:winexe (Opcje kompilatora C#)
Opcja **-target:winexe** powoduje, że kompilator tworzy plik wykonywalny (EXE), program Windows.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>Uwagi  
 Plik wykonywalny zostanie utworzony z rozszerzeniem .exe. Program systemu Windows to taki, który zapewnia interfejs użytkownika z biblioteki .NET Framework lub interfejsów API systemu Windows.  
  
 Użyj [-target:exe,](./target-exe-compiler-option.md) aby utworzyć aplikację konsoli.  
  
 O ile nie określono inaczej z opcją [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [metodę Main.](../../programming-guide/main-and-command-args/index.md)  
  
 Po określeniu w wierszu polecenia wszystkie pliki do następnej opcji **-out** lub [-target](./target-compiler-option.md) są używane do tworzenia programu systemu Windows.  
  
 Jedna i tylko jedna **metoda główna** jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe. Opcja [-main](./main-compiler-option.md) umożliwia określenie, która klasa zawiera **Main,** w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Output type.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj `in.cs` w programie windowsowym:  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)
