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
ms.openlocfilehash: 7db975909f498a0b84e7405a12a8f8ec1e2dd34b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216859"
---
# <a name="-lib-c-compiler-options"></a>-lib (opcje kompilatora C#)
**-Lib** opcji określa lokalizację zestawy, do których odwołuje się za pomocą klasy [— odwołanie (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) opcji.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-lib:dir1[,dir2]  
```  
  
## <a name="arguments"></a>Argumenty  
 `dir1`  
 Katalog dla kompilatora do przeszukania Jeśli przywoływany zestaw nie znajduje się w bieżący katalog roboczy (katalogu, z którego są wywoływanie kompilatora) lub w katalogu systemowym środowisko uruchomieniowe języka wspólnego firmy.  
  
 `dir2`  
 Jeden lub więcej dodatkowych katalogów do przeszukania pod kątem odwołań do zestawu. Nazwy katalogów dodatkowe przecinkami i bez biały znak między nimi.  
  
## <a name="remarks"></a>Uwagi  
 Kompilator szuka odwołań do zestawu, które nie są w pełni kwalifikowana w następującej kolejności:  
  
1.  Bieżący katalog roboczy. To jest katalog, z którego jest wywoływany przez kompilator.  
  
2.  Katalogu środowiska CLR systemu.  
  
3.  Katalogi określone przez **-lib**.  
  
4.  Katalogi określonej przez zmienną środowiskową LIB.  
  
 Użyj **— odwołanie** do określenia odwołania do zestawu.  
  
 **-lib** dodatku; Określanie on więcej niż raz dołącza wszystkie wcześniejsze wartości.  
  
 Zamiast **-lib** ma na celu kopiowanie do katalogu roboczego wszystkie wymagane zestawy; ta umożliwia po prostu przekaż nazwę zestawu **— odwołanie**. Następnie można usunąć zestawów z katalogu roboczego. Ponieważ ścieżka do zestawu zależnego nie jest określona w manifeście zestawu, aplikacja może zostać uruchomiona na komputerze docelowym i Znajdź i użyć zestawu w globalnej pamięci podręcznej zestawów.  
  
 Ponieważ kompilator może odwoływać się do zestawu nie oznacza, że środowisko uruchomieniowe języka wspólnego będzie mógł odnaleźć i załadować zestawu w czasie wykonywania. Zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../framework/deployment/how-the-runtime-locates-assemblies.md) szczegółowe informacje na temat jak wyszukuje środowiska uruchomieniowego dla zestawów występujących w odwołaniach.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe.  
  
2.  Kliknij przycisk **ścieżkę odwołania** strony właściwości.  
  
3.  Zmodyfikuj zawartość pola listy.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.ReferencePath%2A>.  
  
## <a name="example"></a>Przykład  
 Kompiluj t2.cs do utworzenia pliku .exe. Kompilator będzie szukać w katalogu roboczego i w katalogu głównym dysku c. odwołania do zestawów.  
  
```console  
csc -lib:c:\ -reference:t2.dll t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
