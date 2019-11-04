---
title: Opcje interakcyjne F#
description: Dowiedz się więcej na temat opcji wiersza polecenia F# obsługiwanych przez program Interactive, FSI. exe.
ms.date: 05/16/2016
ms.openlocfilehash: e4ce0f3f76a7be803942e4b403e5fa6543a09e54
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425316"
---
# <a name="f-interactive-options"></a>Opcje interakcyjne F#

> [!NOTE]
> W tym artykule opisano obecnie tylko środowisko dla systemu Windows.  Zostanie on ponownie zapisany.

W tym temacie opisano opcje wiersza polecenia obsługiwane przez F# program Interactive, `fsi.exe`. F#Interaktywnie akceptuje wiele z tych samych opcji wiersza polecenia co F# kompilator, ale również akceptuje pewne dodatkowe opcje.

## <a name="using-f-interactive-for-scripting"></a>Korzystanie F# z programu Interactive for scripting

F#Interaktywny, `fsi.exe`, może być uruchamiany interakcyjnie lub można go uruchomić z poziomu wiersza polecenia, aby uruchomić skrypt. Składnia wiersza polecenia jest

```console
> fsi.exe [options] [ script-file [arguments] ]
```

Rozszerzenie pliku dla F# plików skryptów jest `.fsx`.

## <a name="table-of-f-interactive-options"></a>Tabela opcji F# interaktywnych

Poniższa tabela zawiera podsumowanie opcji obsługiwanych przez F# program interaktywny. Można ustawić te opcje w wierszu polecenia lub w środowisku IDE programu Visual Studio. Aby ustawić te opcje w środowisku IDE programu Visual Studio, otwórz menu **Narzędzia** , wybierz pozycję **Opcje...** , rozwiń węzeł  **F# narzędzia** i wybierz pozycję  **F# interaktywny**.

Gdzie listy pojawiają F# się w argumentach opcji interaktywnych, elementy listy są oddzielone średnikami (`;`).

|Opcja|Opis|
|------|-----------|
|**--**|Służy do Poinstruuj F# interaktywnie, aby traktować pozostałe argumenty jako argumenty wiersza F# polecenia do programu lub skryptu, do którego można uzyskać dostęp w kodzie przy użyciu listy **FSI. CommandLineArgs —** .|
|**--Checked**[ **+** &#124; **-** ]|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--CodePage:&lt;int&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--consolecolors**[ **+** &#124; **-** ]|Wyświetla ostrzeżenia i komunikaty o błędach w kolorze.|
|**--crossoptimize**[ **+** &#124; **-** ]|Włączać lub wyłączać optymalizacje między modułami.|
|**--Debug**[ **+** &#124; **-** ]<br /><br />**--Debug:** [**pełna**&#124;**pdbonly**&#124;**Portable**&#124;**Embedded**]<br /><br />**-g**[ **+** &#124; **-** ]<br /><br />**-g:** [**pełne**&#124;**pdbonly**&#124;**przenośne**&#124;**Embedded**]|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--define:&lt;ciąg&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--deterministyczny**[ **+** &#124; **-** ]|Tworzy deterministyczny zestaw (w tym identyfikator GUID i sygnaturę czasową wersji modułu).|
|**--exec**|Instruuje F# interaktywny, aby wyjść po załadowaniu plików lub uruchomieniu pliku skryptu podanym w wierszu polecenia.|
|**--fullpaths —**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--GUI**[ **+** &#124; **-** ]|Włącza lub wyłącza pętlę zdarzeń Windows Forms. Wartość domyślna jest włączona.|
|**--Pomoc**<br /><br />**-?**|Służy do wyświetlania składni wiersza polecenia i krótkiego opisu każdej opcji.|
|**--lib:&lt;listy folderów&gt;**<br /><br />**-I:&lt;listy folderów&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--Load:&lt;filename&gt;**|Kompiluje dany kod źródłowy przy uruchamianiu i ładuje skompilowane F# konstrukcje do sesji. Jeśli źródło docelowe zawiera dyrektywy skryptów, takie jak **#use** lub **#load**, należy użyć polecenia **--use** lub **#use** zamiast **--Load** lub **#load**.|
|**--mlcompatibility**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--noframework**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md)|
|**--nologo**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--nowarn:&lt;list ostrzeżeń&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--Optymalizuj**[ **+** &#124; **-** ]|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--preferreduilang:&lt;lang&gt;**| Określa nazwę preferowanej kultury języka wyjściowego (na przykład es-ES, ja-JP). |
|**--quiet**|Pomijaj F# interaktywne dane wyjściowe do strumienia **stdout** .|
|**--Cytaty-debugowanie**|Określa, że powinny być emitowane dodatkowe informacje o debugowaniu dla wyrażeń, F# które pochodzą z literałów cudzysłowu i odbitej definicji. Informacje debugowania są dodawane do atrybutów niestandardowych węzła drzewa F# wyrażenia. Zobacz [cytaty kodu](code-quotations.md) i [expr. CustomAttributes —](https://msdn.microsoft.com/library/eb89943f-5f5b-474e-b125-030ca412edb3).|
|**--ReadLine**[ **+** &#124; **-** ]|Włącza lub wyłącza uzupełnianie kart w trybie interaktywnym.|
|**--Reference:&lt;filename&gt;**<br /><br />**-r:&lt;filename&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--shadowcopyreferences**[ **+** &#124; **-** ]|Uniemożliwia blokowanie odwołań przez proces F# interaktywny.|
|**--simpleresolution**|Rozwiązuje odwołania do zestawów przy użyciu reguł opartych na katalogu, a nie rozpoznawania MSBuild.|
|**--tailcalls**[ **+** &#124; **-** ]|Włącza lub wyłącza użycie instrukcji "tail IL", która powoduje, że ramka stosu będzie ponownie używana na potrzeby funkcji cyklicznych. Ta opcja jest domyślnie włączona.|
|**--targetprofile:&lt;ciąg&gt;**|Określa Profil platformy docelowej tego zestawu. Prawidłowe wartości to mscorlib, Core lub standard.  Wartość domyślna to mscorlib.|
|**--Użyj:&lt;filename&gt;**|Instruuje interpretera, aby używał danego pliku przy uruchamianiu jako początkowej danych wejściowych.|
|**--utf8output —**|Analogicznie jak opcja kompilatora Urząd nadzoru. exe. Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--WARN:&lt;poziom ostrzeżeń&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--warnaserror —** [ **+** &#124; **-** ]|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|
|**--warnaserror —** [ **+** &#124; **-** ]: **&lt;int-list&gt;**|Analogicznie jak opcja kompilatora **Urząd nadzoru. exe** . Aby uzyskać więcej informacji, zobacz [Opcje kompilatora](compiler-options.md).|

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----|-----------|
|[Opcje kompilatora](compiler-options.md)|Opisuje opcje wiersza polecenia dostępne dla F# kompilatora, **Urząd nadzoru. exe**.|
