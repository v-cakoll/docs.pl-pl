---
title: -LIB (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606821"
---
# <a name="-lib-c-compiler-options"></a>-LIB (C# opcje kompilatora)
Opcja **-lib** określa lokalizację zestawów, do których odwołuje się opcja [-Reference (C# opcje kompilatora)](./reference-compiler-option.md) .  
  
## <a name="syntax"></a>Składnia  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Katalog dla kompilatora, który ma być używany w przypadku, gdy w bieżącym katalogu roboczym nie znaleziono zestawu, którego dotyczy odwołanie, lub w katalogu systemowym środowiska uruchomieniowego języka wspólnego.  
  
 `dir2`  
 Co najmniej jeden katalog dodatkowych do przeszukania w celu odwołania do zestawu. Oddzielaj dodatkowe nazwy katalogów przecinkami i bez odstępów między nimi.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1. Bieżący katalog roboczy. Jest to katalog, z którego wywołano kompilator.  
  
2. Katalog systemowy środowiska uruchomieniowego języka wspólnego.  
  
3. Katalogi określone przez **-lib**.  
  
4. Katalogi określone przez zmienną środowiskową LIB.  
  
 Użyj **parametru-reference** , aby określić odwołanie do zestawu.  
  
 **-lib** jest dodatkiem; określenie go więcej niż raz dołącza do dowolnych wcześniejszych wartości.  
  
 Alternatywą dla użycia **-lib** jest skopiowanie do katalogu roboczego wszystkich wymaganych zestawów; umożliwi to po prostu przekazanie nazwy zestawu do **odwołania**. Następnie można usunąć zestawy z katalogu roboczego. Ponieważ ścieżka do zestawu zależnego nie została określona w manifeście zestawu, aplikacja może zostać uruchomiona na komputerze docelowym i będzie znajdować się w niej zestaw w globalnej pamięci podręcznej zestawów.  
  
 Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że środowisko uruchomieniowe języka wspólnego będzie mogło znaleźć i załadować zestaw w czasie wykonywania. Zobacz [, jak środowisko uruchomieniowe lokalizuje zestawy](../../../framework/deployment/how-the-runtime-locates-assemblies.md) , aby uzyskać szczegółowe informacje o tym, jak środowisko uruchomieniowe wyszukuje przywoływane zestawy.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwórz okno dialogowe **strony właściwości** projektu.  
  
2. Kliknij stronę właściwości **Ścieżka odwołania** .  
  
3. Zmodyfikuj zawartość pola listy.  
  
 Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>tę opcję kompilatora, zobacz.  
  
## <a name="example"></a>Przykład  
 Kompiluj t2.cs, aby utworzyć plik. exe. Kompilator będzie szukać w katalogu roboczym i w katalogu głównym dysku C na potrzeby odwołań do zestawów.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Zobacz także

- [Opcje kompilatora C#](./index.md)
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
