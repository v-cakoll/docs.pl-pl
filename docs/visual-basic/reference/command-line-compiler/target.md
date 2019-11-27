---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: bd79d95a18fb1935d97fff2d1b2c7767752b9765
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351715"
---
# <a name="-target-visual-basic"></a>-Target (Visual Basic)

Określa format danych wyjściowych kompilatora.

## <a name="syntax"></a>Składnia

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Uwagi

Poniższa tabela zawiera podsumowanie efektu opcji `-target`.

|**Zaznaczyć**|**Domyślnie**|
|----------------|------------------|
|`-target:exe`|Powoduje, że kompilator tworzy wykonywalną aplikację konsolową.<br /><br /> Jest to opcja domyślna, gdy nie określono opcji `-target`. Plik wykonywalny jest tworzony z rozszerzeniem. exe.<br /><br /> O ile nie określono inaczej z opcją `/out`, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera procedurę `Sub Main`.<br /><br /> Tylko jedna procedura `Sub Main` jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. Użyj opcji kompilatora `-main`, aby określić, która Klasa zawiera procedurę `Sub Main`.|
|`-target:library`|Powoduje, że kompilator tworzy bibliotekę dołączaną dynamicznie (DLL).<br /><br /> Plik biblioteki dołączanej dynamicznie jest tworzony z rozszerzeniem dll.<br /><br /> O ile nie określono inaczej z opcją `-out`, nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.<br /><br /> Podczas kompilowania biblioteki DLL procedura `Sub Main` nie jest wymagana.|
|`-target:module`|Powoduje, że kompilator generuje moduł, który można dodać do zestawu.<br /><br /> Plik wyjściowy jest tworzony z rozszerzeniem modułu.<br /><br /> Środowisko uruchomieniowe języka wspólnego .NET nie może załadować pliku, który nie ma zestawu. Można jednak dołączyć taki plik do manifestu zestawu przy użyciu `-reference`.<br /><br /> Gdy kod w jednym module odwołuje się do typów wewnętrznych w innym module, oba moduły muszą być włączone do manifestu zestawu przy użyciu `-reference`.<br /><br /> Opcja [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) Importuje metadane z modułu.|
|`-target:winexe`|Powoduje, że kompilator tworzy wykonywalną aplikację opartą na systemie Windows.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem. exe. Aplikacja oparta na systemie Windows to taka, która udostępnia interfejs użytkownika z biblioteki klas .NET Framework lub interfejsów API systemu Windows.<br /><br /> O ile nie określono inaczej z opcją `-out`, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera procedurę `Sub Main`.<br /><br /> Tylko jedna procedura `Sub Main` jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. W przypadkach, gdy kod zawiera więcej niż jedną klasę, która ma procedurę `Sub Main`, użyj opcji kompilatora `-main`, aby określić, która Klasa zawiera procedurę `Sub Main`|
|`-target:appcontainerexe`|Powoduje, że kompilator tworzy wykonywalną aplikację opartą na systemie Windows, która musi być uruchomiona w kontenerze aplikacji. To ustawienie jest przeznaczone do użycia dla aplikacji ze sklepu Windows 8. x.<br /><br /> Ustawienie **appcontainerexe** ustawia bit w polu charakterystyki [przenośnego pliku wykonywalnego](/windows/desktop/Debug/pe-format) . Ten bit wskazuje, że aplikacja musi być uruchomiona w kontenerze aplikacji. Gdy ten bit jest ustawiony, występuje błąd, jeśli metoda `CreateProcess` próbuje uruchomić aplikację poza kontenerem aplikacji. Poza tym ustawieniem bitu **-target: appcontainerexe** jest odpowiednikiem **-target: winexe**.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem. exe.<br /><br /> O ile nie określono inaczej przy użyciu opcji `-out`, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera procedurę `Sub Main`.<br /><br /> Tylko jedna procedura `Sub Main` jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. Jeśli kod zawiera więcej niż jedną klasę, która ma procedurę `Sub Main`, użyj opcji kompilatora `-main`, aby określić, która Klasa zawiera procedurę `Sub Main`|
|`-target:winmdobj`|Powoduje, że kompilator tworzy plik pośredni, który można przekonwertować na środowisko wykonawcze systemu Windows plik binarny (. winmd). Plik. winmd może być używany przez JavaScript i C++ programy, oprócz programów języka zarządzanego.<br /><br /> Plik pośredni jest tworzony przy użyciu rozszerzenia. winmdobj.<br /><br /> O ile nie określono inaczej przy użyciu opcji `-out`, nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. Procedura `Sub Main` nie jest wymagana.<br /><br /> Plik winmdobj jest przeznaczony do użycia jako dane wejściowe dla narzędzia eksportu <xref:Microsoft.Build.Tasks.WinMDExp> do tworzenia pliku metadanych (WinMD) systemu Windows. Plik WinMD ma rozszerzenie WINMD i zawiera zarówno kod z oryginalnej biblioteki, jak i definicje WinMD, które są używane w języku JavaScript C++, i środowisko wykonawcze systemu Windows.|

O ile nie określono `-target:module`, `-target` powoduje dodanie manifestu zestawu .NET Framework do pliku wyjściowego.

Każde wystąpienie programu VBC. exe tworzy co najwyżej jeden plik wyjściowy. Jeśli określisz opcję kompilatora, taką jak `-out` lub `-target` więcej niż jeden raz, ostatni proces kompilatora zostanie włączony. Informacje o wszystkich plikach w kompilacji są dodawane do manifestu. Wszystkie pliki wyjściowe z wyjątkiem tych utworzonych za pomocą `-target:module` zawierają metadane zestawu w manifeście. Użyj [Ildasm. exe (Il dezasembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania metadanych w pliku wyjściowym.

Krótka forma `-target` jest `-t`.

### <a name="to-set--target-in-the-visual-studio-ide"></a>Aby ustawić element docelowy w środowisku IDE programu Visual Studio

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **aplikacja** .

3. Zmodyfikuj wartość w polu **Typ aplikacji** .

## <a name="example"></a>Przykład

Poniższy kod kompiluje `in.vb`, tworząc `in.dll`:

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)
- [-Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
