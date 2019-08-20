---
title: '-target: Library (C# opcje kompilatora)'
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606394"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target: Library (C# opcje kompilatora)
Opcja **-target: Library** powoduje, że kompilator tworzy bibliotekę dołączaną dynamicznie (dll), a nie plik wykonywalny (exe).  
  
## <a name="syntax"></a>Składnia  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Uwagi  
 Biblioteka DLL zostanie utworzona z rozszerzeniem dll.  
  
 O ile nie określono inaczej z opcją [-out](./out-compiler-option.md) , nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.  
  
 W przypadku określenia w wierszu polecenia wszystkie pliki do następnej lub docelowej opcji **modułu** są używane do tworzenia pliku dll.  
  
 Podczas kompilowania pliku DLL Metoda [Main](../../programming-guide/main-and-command-args/index.md) nie jest wymagana.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę właściwości **aplikacji** .  
  
3. Zmodyfikuj właściwość **typu danych wyjściowych** .  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.OutputType%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj `in.cs`, Utwórz `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [-Target (C# opcje kompilatora)](./target-compiler-option.md)
- [Opcje kompilatora C#](./index.md)
