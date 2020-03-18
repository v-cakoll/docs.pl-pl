---
title: -target:exe (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /exe
helpviewer_keywords:
- target compiler options [C#], /target:exe
- /target compiler options [C#], /target:exe
- -target compiler options [C#], /target:exe
ms.assetid: bda5717d-1b91-4848-956b-fcf85c30e432
ms.openlocfilehash: 6087a64bea5a59bfcfc5372f6a9d6eb8b9c940cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606454"
---
# <a name="-targetexe-c-compiler-options"></a>-target:exe (Opcje kompilatora C#)
Opcja **-target:exe** powoduje, że kompilator tworzy plik wykonywalny (EXE), aplikację konsoli.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:exe  
```  
  
## <a name="remarks"></a>Uwagi  
 Opcja **-target:exe** obowiązuje domyślnie. Plik wykonywalny zostanie utworzony z rozszerzeniem .exe.  
  
 Użyj [-target:winexe,](./target-winexe-compiler-option.md) aby utworzyć plik wykonywalny programu Windows.  
  
 O ile nie określono inaczej z opcją [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera [metodę Main.](../../programming-guide/main-and-command-args/index.md)  
  
 Po określeniu w wierszu polecenia wszystkie pliki do następnej opcji **-out** lub **-target:module** są używane do tworzenia pliku exe  
  
 Jedna i tylko jedna **metoda główna** jest wymagana w plikach kodu źródłowego, które są kompilowane do pliku .exe. [Opcja -main](./main-compiler-option.md) kompilator pozwala określić, która klasa zawiera **Main** metody, w przypadkach, gdy kod ma więcej niż jedną klasę z **Main** metody.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Output type.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Każdy z następujących wierszy `in.cs`polecenia `in.exe`skompiluje , tworząc:  
  
```console  
csc -target:exe in.cs  
csc in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)
