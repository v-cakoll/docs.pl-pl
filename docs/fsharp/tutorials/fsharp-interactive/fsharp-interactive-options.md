---
title: Opcje interakcyjne F#
description: "Więcej informacji na temat opcji wiersza polecenia obsługiwane przez narzędzia F # Interactive, fsi.exe."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f9f3e39b-ce6c-41ff-991f-0625f46441ae
ms.openlocfilehash: a9b36a12aa9ffcfa26ea50d72d018a25f5f65243
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
|**--zaznaczone**[**+**&#124; **-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**-codepage:&lt;int&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**crossoptimize —**[**+**&#124; **-**]|Włącz lub wyłącz optymalizacje między modułami.|
|**--debug**[**+**&#124; **-**]<br /><br />**--debug:**[**pełne**&#124; **pdbonly**]<br /><br />**-g**[**+**&#124; **-**]<br /><br />**-g:**[**pełne**&#124; **pdbonly**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**— Zdefiniuj:&lt;ciągu&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**--exec**|Nakazuje interakcyjne F # można zamknąć po załadowaniu plików lub uruchamianie pliku skryptu w wierszu polecenia.|
|**fullpaths —**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**graficzny interfejs użytkownika —**[**+**&#124; **-**]|Włącza lub wyłącza pętli zdarzenia Windows Forms. Domyślnie włączone.|
|**— Pomoc**<br /><br />**-?**|Umożliwia wyświetlenie składnia wiersza polecenia i krótki opis każdej z nich.|
|**-lib:&lt;listy folderów&gt;**<br /><br />**-I:&lt;listy folderów&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**— obciążenia:&lt;filename&gt;**|Kompiluje kod źródłowy danego podczas uruchamiania i ładuje skompilowanych konstrukcje F # do sesji. Jeśli docelowe źródło zawiera dyrektywy skryptów, takich jak **#use** lub **#load**, należy użyć **--użyj** lub **#use** zamiast **--załadować** lub **#load**.|
|**--mlcompatibility**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**noframework —**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md)|
|**-nologo**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**--nowarn:&lt;ostrzeżenie listy&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**--zoptymalizować**[**+**&#124; **-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**-quiet**|Pomiń F # Interactive przez dane wyjściowe do **stdout** strumienia.|
|**--ofert debugowania**|Określa, że dodatkowe informacje o debugowaniu powinien wysyłanego dla wyrażeń, które pochodzą z literałów cytatu F # i odzwierciedlone definicje. Informacje debugowania są dodawane do niestandardowych atrybutów węzła drzewa wyrażenia F #. Zobacz [kodu ofert](../../language-reference/code-quotations.md) i [Expr.customattributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**readline —**[**+**&#124; **-**]|Włącz lub wyłącz uzupełniania po naciśnięciu tabulatora w trybie interaktywnym.|
|**--odwołania:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**tailcalls —**[**+**&#124; **-**]|Włącza lub wyłącza użycie instrukcji IL tail, co powoduje, że ramka stosu zostanie ponownie tail funkcji cyklicznej. Ta opcja jest domyślnie włączona.|
|**— Użyj:&lt;filename&gt;**|Określa, że interpreter do używania danego pliku przy uruchamianiu jako początkowych danych wejściowych.|
|**-utf8output**|Taka sama jak fsc.exe — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**— Ostrzeżenie:&lt;poziom ostrzeżeń&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**-warnaserror**[**+**&#124; **-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|
|**-warnaserror**[**+**&#124; **-** ]:**&lt;listy int&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [— opcje kompilatora](../../language-reference/compiler-options.md).|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje kompilatora](../../language-reference/compiler-options.md)|Zawiera opis opcji wiersza polecenia dostępnych dla kompilator języka F # **fsc.exe**.|
