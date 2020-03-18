---
title: -out (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: 6c8408c0c613e361dae0c1db19f854e9421ca467
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70970376"
---
# <a name="-out-c-compiler-options"></a>-out (Opcje kompilatora C#)
Opcja **-out** określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku wyjściowego utworzonego przez kompilator.  
  
## <a name="remarks"></a>Uwagi  
 W wierszu polecenia można określić wiele plików wyjściowych dla kompilacji. Kompilator oczekuje, że znajdzie jeden lub więcej plików kodu źródłowego po opcji **-out.** Następnie wszystkie pliki kodu źródłowego zostaną skompilowane do pliku wyjściowego określonego przez tę opcję **wyjścia.**  
  
 Określ pełną nazwę i rozszerzenie pliku, który chcesz utworzyć.  
  
 Jeśli nazwa pliku wyjściowego nie zostanie określona:  
  
- .exe bierze swoją nazwę od pliku kodu źródłowego, który zawiera **Main** metody.  
  
- Nazwa pliku .dll lub .netmodule będzie pochodzić od pierwszego pliku kodu źródłowego.  
  
 Plik kodu źródłowego używany do kompilowania jednego pliku wyjściowego nie może być używany w tej samej kompilacji do kompilacji innego pliku wyjściowego.  
  
 Podczas tworzenia wielu plików wyjściowych w kompilacji wiersza polecenia, należy pamiętać, że tylko jeden z plików wyjściowych może być zestawem i że tylko pierwszy plik wyjściowy określony (niejawnie lub jawnie z **-out)** może być zestawem.  
  
 Wszystkie moduły produkowane w ramach kompilacji stają się plikami skojarzonymi z dowolnym zestawem również wyprodukowanym w kompilacji. Użyj [programu ildasm.exe,](../../../framework/tools/ildasm-exe-il-disassembler.md) aby wyświetlić manifest zestawu, aby wyświetlić skojarzone pliki.  
  
 Opcja kompilatora -out jest wymagana, aby exe był obiektem docelowym zestawu znajomego. Aby uzyskać więcej informacji, zobacz [Zestawy znajomych](../../../standard/assembly/friend.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz stronę **Właściwości** projektu.  
  
2. Kliknij stronę **właściwości Application.**  
  
3. Zmodyfikuj właściwość **Nazwa zestawu.**  
  
     Aby ustawić tę opcję kompilatora programowo: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> jest właściwością tylko do odczytu, która jest określana przez kombinację typu projektu (exe, library i tak dalej) i nazwę zestawu. Modyfikowanie jednej lub obu tych właściwości będzie konieczne, aby ustawić nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 Skompiluj `t.cs` `t.exe`i utwórz `t2.cs` plik wyjściowy, `mymodule.netmodule`a także zbuduj i utwórz plik wyjściowy modułu:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zespoły znajomych](../../../standard/assembly/friend.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
