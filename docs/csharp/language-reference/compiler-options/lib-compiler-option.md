---
title: -lib (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: 0c230147be055170ca015f27bd42bb096399405d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606821"
---
# <a name="-lib-c-compiler-options"></a>-lib (Opcje kompilatora C#)
Opcja **-lib** określa lokalizację zestawów, do których odwołuje się opcja [-reference (C# Compiler Options).](./reference-compiler-option.md)  
  
## <a name="syntax"></a>Składnia  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Katalog kompilatora, aby sprawdzić, czy nie można znaleźć zestawu, do którego istnieje odwołanie, w bieżącym katalogu roboczym (katalogu, z którego wywołujesz kompilator) lub w katalogu systemowym programu w czasie wykonywania języka wspólnego.  
  
 `dir2`  
 Co najmniej jeden dodatkowe katalogi do wyszukiwania w poszukiwaniu odwołań do zestawu. Oddziel dodatkowe nazwy katalogów przecinkiem i bez odstępu między nimi.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wyszukuje odwołania do zestawu, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1. Bieżący katalog roboczy. Jest to katalog, z którego jest wywoływany kompilator.  
  
2. Katalog systemu wykonywania języka wspólnego.  
  
3. Katalogi określone przez **-lib**.  
  
4. Katalogi określone przez zmienną środowiskową LIB.  
  
 Użyj **-reference,** aby określić odwołanie do złożenia.  
  
 **-lib** jest addytywny; określając go więcej niż jeden raz dołącza do wszelkich wcześniejszych wartości.  
  
 Alternatywą dla używania **-lib** jest skopiowanie do katalogu roboczego wymaganych zestawów; pozwoli to po prostu przekazać nazwę zestawu do **-reference**. Następnie można usunąć zestawy z katalogu roboczego. Ponieważ ścieżka do zestawu zależnego nie jest określona w manifeście zestawu, aplikację można uruchomić na komputerze docelowym i znajdzie i użyje zestawu w globalnej pamięci podręcznej zestawów.  
  
 Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że czas wykonywania języka wspólnego będzie mógł znaleźć i załadować zestaw w czasie wykonywania. Zobacz [Jak runtime lokalizuje zestawy,](../../../framework/deployment/how-the-runtime-locates-assemblies.md) aby uzyskać szczegółowe informacje na temat wyszukiwania w czasie wykonywania dla zestawów, do których istnieje odwołanie.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1. Otwieranie okna dialogowego **Strony właściwości** projektu.  
  
2. Kliknij stronę właściwości **Ścieżka odwołania.**  
  
3. Zmodyfikuj zawartość pola listy.  
  
 Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>kompilatora, zobacz .  
  
## <a name="example"></a>Przykład  
 Skompiluj t2.cs, aby utworzyć plik exe. Kompilator będzie wyglądał w katalogu roboczym i w katalogu głównym dysku C dla odwołań do zestawu.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
