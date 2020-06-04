---
title: -target
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 0ab28d55b2426a4efda112ab84da5e790909d565
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403073"
---
# <a name="-target-visual-basic"></a>-Target (Visual Basic)

Określa format danych wyjściowych kompilatora.

## <a name="syntax"></a>Składnia

```console
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}
```

## <a name="remarks"></a>Uwagi

Poniższa tabela zawiera podsumowanie efektu `-target` opcji.

|**Opcja**|**Zachowanie**|
|----------------|------------------|
|`-target:exe`|Powoduje, że kompilator tworzy wykonywalną aplikację konsolową.<br /><br /> Jest to opcja domyślna, gdy nie `-target` określono żadnej opcji. Plik wykonywalny jest tworzony z rozszerzeniem. exe.<br /><br /> O ile nie określono inaczej z `-out` opcją, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedurę.<br /><br /> Tylko jedna `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. Użyj `-main` opcji kompilatora, aby określić, która Klasa zawiera `Sub Main` procedurę.|
|`-target:library`|Powoduje, że kompilator tworzy bibliotekę dołączaną dynamicznie (DLL).<br /><br /> Plik biblioteki dołączanej dynamicznie jest tworzony z rozszerzeniem dll.<br /><br /> O ile nie określono inaczej z `-out` opcją, nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego.<br /><br /> Podczas kompilowania biblioteki DLL `Sub Main` procedura nie jest wymagana.|
|`-target:module`|Powoduje, że kompilator generuje moduł, który można dodać do zestawu.<br /><br /> Plik wyjściowy jest tworzony z rozszerzeniem modułu.<br /><br /> Środowisko uruchomieniowe języka wspólnego .NET nie może załadować pliku, który nie ma zestawu. Można jednak dołączyć taki plik do manifestu zestawu zestawu przy użyciu `-reference` .<br /><br /> Gdy kod w jednym module odwołuje się do typów wewnętrznych w innym module, oba moduły muszą być włączone do manifestu zestawu przy użyciu `-reference` .<br /><br /> Opcja [-addmodule](addmodule.md) Importuje metadane z modułu.|
|`-target:winexe`|Powoduje, że kompilator tworzy wykonywalną aplikację opartą na systemie Windows.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem. exe. Aplikacja oparta na systemie Windows to taka, która udostępnia interfejs użytkownika z biblioteki klas .NET Framework lub interfejsów API systemu Windows.<br /><br /> O ile nie określono inaczej z `-out` opcją, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedurę.<br /><br /> Tylko jedna `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. W przypadkach, gdy kod zawiera więcej niż jedną klasę, która ma `Sub Main` procedurę, użyj `-main` opcji kompilatora, aby określić, która Klasa zawiera `Sub Main` procedurę|
|`-target:appcontainerexe`|Powoduje, że kompilator tworzy wykonywalną aplikację opartą na systemie Windows, która musi być uruchomiona w kontenerze aplikacji. To ustawienie jest przeznaczone do użycia dla aplikacji ze sklepu Windows 8. x.<br /><br /> Ustawienie **appcontainerexe** ustawia bit w polu charakterystyki [przenośnego pliku wykonywalnego](/windows/desktop/Debug/pe-format) . Ten bit wskazuje, że aplikacja musi być uruchomiona w kontenerze aplikacji. Gdy ten bit jest ustawiony, występuje błąd, jeśli `CreateProcess` Metoda próbuje uruchomić aplikację poza kontenerem aplikacji. Poza tym ustawieniem bitu **-target: appcontainerexe** jest odpowiednikiem **-target: winexe**.<br /><br /> Plik wykonywalny jest tworzony z rozszerzeniem. exe.<br /><br /> O ile nie określono inaczej przy użyciu `-out` opcji, nazwa pliku wyjściowego przyjmuje nazwę pliku wejściowego, który zawiera `Sub Main` procedurę.<br /><br /> Tylko jedna `Sub Main` procedura jest wymagana w plikach kodu źródłowego, które są kompilowane w pliku. exe. Jeśli kod zawiera więcej niż jedną klasę, która ma `Sub Main` procedurę, użyj `-main` opcji kompilatora, aby określić, która Klasa zawiera `Sub Main` procedurę|
|`-target:winmdobj`|Powoduje, że kompilator tworzy plik pośredni, który można przekonwertować na środowisko wykonawcze systemu Windows plik binarny (. winmd). Plik. winmd może być używany przez programy JavaScript i C++, a także do programów języka zarządzanego.<br /><br /> Plik pośredni jest tworzony przy użyciu rozszerzenia. winmdobj.<br /><br /> O ile nie określono inaczej przy użyciu `-out` opcji, nazwa pliku wyjściowego przyjmuje nazwę pierwszego pliku wejściowego. `Sub Main`Procedura nie jest wymagana.<br /><br /> Plik. winmdobj jest przeznaczony do użycia jako dane wejściowe <xref:Microsoft.Build.Tasks.WinMDExp> narzędzia eksportu w celu utworzenia pliku metadanych (WinMD) systemu Windows. Plik WinMD ma rozszerzenie WINMD i zawiera zarówno kod z oryginalnej biblioteki, jak i definicje WinMD, które są używane w języku JavaScript, C++ i środowisko wykonawcze systemu Windows.|

O ile nie zostanie określony `-target:module` , `-target` powoduje dodanie .NET Framework manifestu zestawu do pliku wyjściowego.

Każde wystąpienie programu VBC. exe tworzy co najwyżej jeden plik wyjściowy. Jeśli określisz opcję kompilatora, taką jak `-out` lub `-target` więcej niż jeden raz, ostatni proces kompilatora zostanie włączony. Informacje o wszystkich plikach w kompilacji są dodawane do manifestu. Wszystkie pliki wyjściowe z wyjątkiem tych utworzonych za pomocą `-target:module` zawierają metadane zestawu w manifeście. Użyj [Ildasm. exe (Il dezasembler)](../../../framework/tools/ildasm-exe-il-disassembler.md) do wyświetlania metadanych w pliku wyjściowym.

Krótka forma `-target` to `-t` .

### <a name="to-set--target-in-the-visual-studio-ide"></a>Aby ustawić element docelowy w środowisku IDE programu Visual Studio

1. Zaznaczono projekt w **Eksplorator rozwiązań**. W menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **aplikacja** .

3. Zmodyfikuj wartość w polu **Typ aplikacji** .

## <a name="example"></a>Przykład

Poniższy kod kompiluje `in.vb` , tworząc `in.dll` :

```console
vbc -target:library in.vb
```

## <a name="see-also"></a>Zobacz też

- [Kompilator wiersza polecenia Visual Basic](index.md)
- [-main](main.md)
- [-out (Visual Basic)](out.md)
- [-Reference (Visual Basic)](reference.md)
- [-addmodule](addmodule.md)
- [-moduleassemblyname](moduleassemblyname.md)
- [Zestawy w środowisku .NET](../../../standard/assembly/index.md)
- [Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)
