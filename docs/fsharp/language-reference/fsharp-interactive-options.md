---
title: Opcje interakcyjne F#
description: 'Więcej informacji na temat opcji wiersza polecenia obsługiwane przez narzędzia F # Interactive, fsi.exe.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 45ed12e63a440ce176947cbfca189781c8675e10
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="f-interactive-options"></a>Opcje interakcyjne F#

> [!NOTE]
W tym artykule opisano obecnie środowisko dla systemu Windows tylko.  Będzie ona ulegną.

W tym temacie opisano opcje wiersza polecenia obsługiwane przez narzędzia F # Interactive, `fsi.exe`. F # Interactive akceptuje wiele z tych samych opcji wiersza polecenia jako kompilator języka F #, ale również zawierać niektóre dodatkowe opcje.

## <a name="using-f-interactive-for-scripting"></a>Przy użyciu interakcyjne F # dla skryptów
F # Interactive, `fsi.exe`, można uruchomić interakcyjnego lub można uruchomić z wiersza polecenia do uruchomienia skryptu. Składnia wiersza polecenia

```
> fsi.exe [options] [ script-file [arguments] ]
```

Rozszerzenie pliku plikach skryptu języka F # jest `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabela Opcje interakcyjne F #
W poniższej tabeli przedstawiono opcje obsługiwane przez narzędzia F # Interactive. Te opcje można ustawić w wierszu polecenia lub za pomocą środowiska IDE programu Visual Studio. Aby ustawić te opcje w programie Visual Studio IDE, otwórz **narzędzia** menu, wybierz opcję **opcje...** , następnie rozwiń węzeł **narzędzia F #** a następnie wybierz węzeł **F # Interactive**.

W przypadku, gdy są wyświetlane w F # Interactive argumentów opcji, elementy listy są oddzielone średnikami (`;`).

|Opcja|Opis|
|------|-----------|
|**--**|Używanych w celu poinstruowania F # Interactive do Traktuj pozostałe argumenty jak argumenty wiersza polecenia F # program lub skrypt, które jest dostępne w kodzie za pomocą listy **elementu fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**-codepage:&lt;int&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Dane wyjściowe, ostrzeżenia i komunikaty o błędach w kolorze.|
|**--crossoptimize**[**+**&#124;**-**]|Włącz lub wyłącz optymalizacje między modułami.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debugowania:**[**pełne**&#124;**pdbonly**&#124;**przenośne**&#124;**osadzone**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**pełne**&#124;**pdbonly**&#124;**przenośne**&#124;**osadzone**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**— Zdefiniuj:&lt;ciągu&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--deterministyczne**[**+**&#124;**-**]|Tworzy zestaw deterministyczne (w tym identyfikator GUID wersji modułu i sygnatura czasowa).|
|**--exec**|Nakazuje interakcyjne F # można zamknąć po załadowaniu plików lub uruchamianie pliku skryptu w wierszu polecenia.|
|**--fullpaths**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Włącza lub wyłącza pętli zdarzenia Windows Forms. Domyślnie włączone.|
|**--help**<br /><br />**-?**|Umożliwia wyświetlenie składnia wiersza polecenia i krótki opis każdej z nich.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**— obciążenia:&lt;filename&gt;**|Kompiluje kod źródłowy danego podczas uruchamiania i ładuje skompilowanych konstrukcje F # do sesji. Jeśli docelowe źródło zawiera dyrektywy skryptów, takich jak **#use** lub **#load**, należy użyć **--użyj** lub **#use** zamiast **--załadować** lub **#load**.|
|**--mlcompatibility**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--noframework**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md)|
|**-nologo**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--nowarn:&lt;ostrzeżenie listy&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**-preferreduilang:&lt;lang&gt;**| Określa nazwę preferowanego języka wyjściowego kultury (np. es-ES, ja-JP). |
|**--quiet**|Pomiń F # Interactive przez dane wyjściowe do **stdout** strumienia.|
|**--quotations-debug**|Określa, że dodatkowe informacje o debugowaniu powinien wysyłanego dla wyrażeń, które pochodzą z literałów cytatu F # i odzwierciedlone definicje. Informacje debugowania są dodawane do niestandardowych atrybutów węzła drzewa wyrażenia F #. Zobacz [kodu ofert](code-quotations.md) i [Expr.customattributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Włącz lub wyłącz uzupełniania po naciśnięciu tabulatora w trybie interaktywnym.|
|**--odwołania:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Uniemożliwia blokowanie przez proces narzędzia F # Interactive odwołań.|
|**--simpleresolution**|Usuwa odwołania do zestawów przy użyciu reguł opartych na katalogu, a nie rozpoznawania narzędzia MSBuild.|
|**--tailcalls**[**+**&#124;**-**]|Włącza lub wyłącza użycie instrukcji IL tail, co powoduje, że ramka stosu zostanie ponownie tail funkcji cyklicznej. Ta opcja jest domyślnie włączona.|
|**--targetprofile:&lt;ciągu&gt;**|Określa profil platformy docelowej tego zestawu. Prawidłowe wartości to mscorlib, netcore lub krótkich nazw netstandard.  Wartość domyślna to mscorlib.|
|**— Użyj:&lt;filename&gt;**|Określa, że interpreter do używania danego pliku przy uruchamianiu jako początkowych danych wejściowych.|
|**--utf8output**|Taka sama jak fsc.exe — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**— Ostrzeżenie:&lt;poziom ostrzeżeń&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](compiler-options.md).|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje kompilatora](compiler-options.md)|Zawiera opis opcji wiersza polecenia dostępnych dla kompilator języka F # **fsc.exe**.|
