---
title: -lib (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /lib
helpviewer_keywords:
- lib compiler option [C#]
- -lib compiler option [C#]
- /lib compiler option [C#]
ms.assetid: b0efcc88-e8aa-4df4-a00b-8bdef70b7673
ms.openlocfilehash: c140a49de0503da1e59396f14ac1aee4c1d7d1a6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511208"
---
# <a name="-lib-c-compiler-options"></a>-lib (opcje kompilatora C#)
**-Lib** opcja określa lokalizację zestawów, do których odwołuje się poprzez [— odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) opcji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Katalog dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w bieżącym katalogu roboczym (katalog, z którego są wywołując kompilator) lub w katalogu systemu wykonywalnych języka wspólnego.  
  
 `dir2`  
 Jeden lub więcej dodatkowych katalogów do przeszukania pod kątem odwołań do zestawów. Rozdziel nazwy dodatkowym katalogiem, za pomocą przecinka i bez biały znak między nimi.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator wyszukuje odwołania do zestawów, które nie są w pełni kwalifikowane w następującej kolejności:  
  
1.  Bieżący katalog roboczy. Jest to katalog, w którym kompilator jest wywoływany.  
  
2.  Katalogu środowiska CLR systemu.  
  
3.  Katalogi określone przez **-lib**.  
  
4.  Katalogi określone przez zmienną środowiskową LIB.  
  
 Użyj **— dokumentacja** do określenia odwołania do zestawu.  
  
 **-lib** dodatku; Określanie on więcej niż jeden raz dołącza do dowolnych wartości wcześniejsze.  
  
 Alternatywa dla użycia **-lib** jest skopiowanie do katalogu roboczego wszystkie wymagane zestawy; temu będzie można po prostu przekazać nazwę zestawu, aby **— dokumentacja**. Następnie można usunąć zestawów z katalogu roboczego. Ponieważ nie określono ścieżki do zależnego zestawu w manifeście zestawu, aplikacja może zostać uruchomiona na komputerze docelowym i znajdzie i używać zestawu w globalnej pamięci podręcznej.  
  
 Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że środowisko uruchomieniowe języka wspólnego będzie można znaleźć i załadować zestawu w czasie wykonywania. Zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../framework/deployment/how-the-runtime-locates-assemblies.md) szczegółowe informacje na temat jak środowisko uruchomieniowe wyszukuje przywoływanych zestawów.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **stron właściwości** okno dialogowe.  
  
2.  Kliknij przycisk **ścieżka odwołań** stronę właściwości.  
  
3.  Zmodyfikuj zawartość pola listy.  
  
 Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Przykład  
 Skompiluj t2.cs do tworzenia pliku .exe. Kompilator wyszuka w katalogu roboczym i w katalogu głównym dysku c. odwołania do zestawu.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
