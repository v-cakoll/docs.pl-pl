---
title: -target:library (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606394"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target:library (Opcje kompilatora C#)
Opcja **-target:library** powoduje, że kompilator tworzy bibliotekę łączy dynamicznych (DLL), a nie plik wykonywalny (EXE).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Uwagi  
 DLL zostanie utworzona z rozszerzeniem .dll.  
  
 O ile nie określono inaczej z opcją [-out,](./out-compiler-option.md) nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.  
  
 Po określeniu w wierszu polecenia wszystkie pliki do następnej opcji **-out** lub **-target:module** są używane do tworzenia pliku dll.  
  
 Podczas tworzenia pliku dll metoda [główna](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Output type.**  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.OutputType%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 `in.cs`Kompiluj `in.dll`, tworząc:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [-target (Opcje kompilatora C#)](./target-compiler-option.md)
- [Opcje kompilatora Języka C#](./index.md)
