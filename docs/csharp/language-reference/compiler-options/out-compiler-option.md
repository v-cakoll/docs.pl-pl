---
title: -out (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
ms.openlocfilehash: ea371dc968c8d8bf1569d17531cf7f6faff1d315
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43418583"
---
# <a name="-out-c-compiler-options"></a>-out (opcje kompilatora C#)
**-Out** opcja określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku wyjściowego, utworzony przez kompilator.  
  
## <a name="remarks"></a>Uwagi  
 W wierszu polecenia jest możliwość określenia wielu plików wyjściowych dla kompilacji. Kompilator spodziewa się znaleźć pliki kodu co najmniej jeden źródłowy zgodnie z **-out** opcji. Następnie wszystkich plikach kodu źródłowego zostanie skompilowany w określony przez to plik wyjściowy **-out** opcji.  
  
 Podaj pełną nazwę i rozszerzenie pliku, który chcesz utworzyć.  
  
 Jeśli nie określisz nazwy pliku wyjściowego:  
  
-   .Exe zajmie się jego nazwy w pliku kodu źródłowego, który zawiera **Main** metody.  
  
-   Plik .dll lub moduł .netmodule potrwa nazwy z pierwszego pliku kodu źródłowego.  
  
 Plik kodu źródłowego, używana do kompilowania jednego pliku danych wyjściowych nie można użyć w tej samej kompilacji dla kompilacji inny plik danych wyjściowych.  
  
 Podczas produkowania wiele plików wyjściowych w kompilacji wiersza polecenia, pamiętać, że tylko jeden z plików wyjściowych może być zestaw, a określony tylko pierwszy plik wyjściowy (jawnie lub niejawnie za pomocą **-out**) może być zestaw .  
  
 Wszystkie moduły, utworzony jako część kompilacji stają się pliki skojarzone z dowolnego złożenia, również jest generowany w kompilacji. Użyj [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić manifest zestawu, aby wyświetlić skojarzone pliki.  
  
 Out — opcja kompilatora jest wymagana dla pliku exe jako obiekt docelowy zestaw przyjazny. Aby uzyskać więcej informacji, zobacz [przyjaznych zestawów](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** stronę właściwości.  
  
3.  Modyfikowanie **nazwy zestawu** właściwości.  
  
     Aby programowo ustawić tę opcję kompilatora: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> jest tylko do odczytu właściwość, która jest określana przez połączenie typu projektu (exe, biblioteki i tak dalej) i nazwę zestawu. Modyfikowanie jedną lub obie te właściwości będą należy ustawić nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 Skompilować `t.cs` i utworzyć plik wyjściowy `t.exe`, a także kompilacji `t2.cs` i utworzyć plik wyjściowy modułu `mymodule.netmodule`:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
