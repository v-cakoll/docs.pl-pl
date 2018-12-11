---
title: Opcje interakcyjne F#
description: Więcej informacji na temat opcji wiersza polecenia obsługiwane przez F# Interactive, fsi.exe.
ms.date: 05/16/2016
ms.openlocfilehash: cca1ef6671878acb1b837d6590139d5de7b7167d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128157"
---
# <a name="f-interactive-options"></a>Opcje interakcyjne F#

> [!NOTE]
> W tym artykule opisano aktualnie środowisko Windows tylko.  Będzie inaczej.

W tym temacie opisano opcje wiersza polecenia obsługiwane przez F# Interactive, `fsi.exe`. F#Interactive akceptuje wiele tych samych opcji wiersza polecenia jako F# kompilatora, ale akceptuje również pewne dodatkowe opcje.

## <a name="using-f-interactive-for-scripting"></a>Za pomocą F# interaktywne dla skryptów
F#Interaktywny, `fsi.exe`, może być uruchamiane interaktywnie lub można je uruchomić z wiersza polecenia, aby uruchomić skrypt. Składnia wiersza polecenia

```
> fsi.exe [options] [ script-file [arguments] ]
```

Rozszerzenie pliku F# pliki skryptów jest `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabela F# interaktywnych opcji
W poniższej tabeli przedstawiono opcje obsługiwane przez F# interakcyjne. Te opcje można ustawić w wierszu polecenia lub za pośrednictwem środowiska IDE programu Visual Studio. Aby ustawić te opcje w programie Visual Studio IDE, otwórz **narzędzia** menu, wybierz opcję **opcje...** , następnie rozwiń  **F# narzędzia** a następnie wybierz węzeł  **F# Interactive**.

Gdzie są wyświetlane w F# opcji Interactive argumentów, elementy listy są oddzielone średnikami (`;`).

|Opcja|Opis|
|------|-----------|
|**--**|Używany w celu poinstruowania F# Interactive o traktowaniu pozostałych argumentów jako argumentów wiersza polecenia, aby F# programu lub skryptu, który jest dostępny w kodzie za pomocą listy **fsi.CommandLineArgs**.|
|**--checked**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**-codepage:&lt;int&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--consolecolors**[**+**&#124;**-**]|Dane wyjściowe, ostrzeżenia i komunikaty o błędach są oznaczone kolorem.|
|**--crossoptimize**[**+**&#124;**-**]|Włącza lub wyłącza optymalizacje między modułami.|
|**--debug**[**+**&#124;**-**]<br /><br />**--debugowania:**[**pełną**&#124;**pdbonly**&#124;**przenośne**&#124;**osadzonego**]<br /><br />**-g**[**+**&#124;**-**]<br /><br />**-g:**[**pełne**&#124;**pdbonly**&#124;**przenośne**&#124;**osadzone**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**— Zdefiniuj:&lt;ciągu&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--deterministyczne**[**+**&#124;**-**]|Tworzy zestaw deterministyczny (w tym identyfikator GUID wersji modułu i sygnaturę czasową).|
|**--exec**|Powoduje, że F# interaktywnego, aby zakończyło po ładowaniu plików lub uruchamiania pliku skryptu podanego w wierszu polecenia.|
|**--fullpaths**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--gui**[**+**&#124;**-**]|Włącza lub wyłącza pętlę zdarzeń Windows Forms. Wartość domyślna jest ustawiona.|
|**--help**<br /><br />**-?**|Umożliwia wyświetlenie składnia wiersza polecenia i krótkiego opisu każdej opcji.|
|**--lib:&lt;folder-list&gt;**<br /><br />**-I:&lt;folder-list&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**— obciążenia:&lt;nazwy pliku&gt;**|Kompiluje podany kod źródłowy przy uruchamianiu i ładuje skompilowane F# konstrukcji do sesji. Jeśli docelowe źródło zawiera dyrektywy wykonywania skryptów, takie jak **#use** lub **#load**, należy użyć **— użyj** lub **#use** zamiast **— obciążenia** lub **#load**.|
|**--mlcompatibility**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--noframework**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md)|
|**nologo —**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**-nowarn:&lt;ostrzeżenie listy&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--optimize**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**preferreduilang —:&lt;lang&gt;**| Określa nazwę preferowanego języka wyjściowego kultury (na przykład, es-ES, ja-JP). |
|**--quiet**|Pomiń F# Interactive danych wyjściowych do **stdout** strumienia.|
|**--quotations-debug**|Określa, że dodatkowe informacje dotyczące debugowania powinny być emitowane dla wyrażeń, które są uzyskiwane z F# literałów oferty i odbitych definicje. Informacje debugowania są dodawane do atrybutów niestandardowych F# węzła drzewa wyrażeń. Zobacz [kodu ofert](code-quotations.md) i [Expr.customattributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--readline**[**+**&#124;**-**]|Włącz lub wyłącz zakończenie karty w trybie interaktywnym.|
|**— odwołania:&lt;nazwy pliku&gt;**<br /><br />**-r:&lt;nazwy pliku&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--shadowcopyreferences**[**+**&#124;**-**]|Zapobiega odwołań z blokowany przez F# procesu interaktywnego.|
|**--simpleresolution**|Usuwa odwołania do zestawów za pomocą reguł opartych na katalog, a nie rozdzielczości MSBuild.|
|**--tailcalls**[**+**&#124;**-**]|Włącza lub wyłącza korzystanie z fragmentarycznej instrukcji IL, co powoduje, że ramek stosu, można użyć ponownie dla funkcji cyklicznych. Ta opcja jest domyślnie włączona.|
|**--targetprofile:&lt;ciągu&gt;**|Określa profil platformy docelowej tego zestawu. Prawidłowe wartości to mscorlib, netcore lub netstandard.  Wartość domyślna to mscorlib.|
|**— Użyj:&lt;nazwy pliku&gt;**|Informuje interpreter używania danego pliku podczas uruchamiania jako początkowych danych wejściowych.|
|**--utf8output**|Tak samo jak opcja kompilatora fsc.exe. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**— Ostrzeżenie:&lt;poziom ostrzeżeń&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|
|**--warnaserror**[**+**&#124;**-**]:**&lt;int-list&gt;**|Taki sam jak **fsc.exe** — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [opcje kompilatora](compiler-options.md).|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje kompilatora](compiler-options.md)|W tym artykule opisano opcje wiersza polecenia dostępne dla F# kompilatora, **fsc.exe**.|
