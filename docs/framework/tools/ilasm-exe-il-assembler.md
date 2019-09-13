---
title: Ilasm.exe (Asembler IL)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcc9ba5e379897247f50175603b1002d5688d215
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894689"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (Asembler IL)

Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL). (Aby uzyskać więcej informacji na temat IL, zobacz [zarządzany proces wykonywania](../../standard/managed-execution-process.md)). Można uruchomić wynikowy plik wykonywalny, który zawiera instrukcje języka IL i wymagane metadane, aby ustalić, czy kod w języku IL działa zgodnie z oczekiwaniami.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametry

| Argument | Opis |
| -------- | ----------- |
|`filename`|Nazwa pliku źródłowego il. Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL. Można dostarczyć wiele argumentów plików źródłowych w celu utworzenia pojedynczego pliku PE z *Ilasm. exe*. **Uwaga:** Należy upewnić się, że ostatnia linia kodu w pliku źródłowym il kończy się znakiem odstępu lub znakiem końca wiersza.|

| Opcja | Opis |
| ------ | ----------- |
|**/32bitpreferred**|Tworzy obraz 32-bitowy (PE32).|
|**/Alignment:** `integer`|Ustawia FileAlignment na wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.|
|**/APPCONTAINER**|Tworzy plik *. dll* lub *. exe* , który jest uruchamiany w kontenerze aplikacji systemu Windows jako dane wyjściowe.|
|**/arm**|Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.<br /><br /> Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/32bitpreferred**.|
|**/Base:** `integer`|Ustawia ImageBase na wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.|
|**/clock**|Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:<br /><br /> **Łączny przebieg**: Łączny czas poświęcony na wykonanie wszystkich konkretnych operacji.<br /><br /> **Uruchamianie**: Ładowanie i otwieranie pliku.<br /><br /> **Emitowanie MD**: Emitowanie metadanych.<br /><br /> **Odref do rozdzielczości def**: Rozpoznawanie odwołań do definicji w pliku.<br /><br /> **Generowanie pliku CEE**: Generowanie obrazu pliku w pamięci.<br /><br /> **Zapisywanie pliku PE**: Zapisywanie obrazu do pliku PE.|
|**/debug**[:**IMPL**&#124;**OPT**]|Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy). Tworzy plik PDB.<br /><br /> **/Debug** bez dodatkowych wartości wyłącza optymalizację JIT i używa punktów sekwencji z pliku PDB.<br /><br /> **Impl** wyłącza optymalizację JIT i używa niejawnych punktów sekwencji.<br /><br /> Opcja **opt** włącza optymalizację JIT i używa niejawnych punktów sekwencji.|
|**/DLL**|Tworzy plik *. dll* jako dane wyjściowe.|
|**/ENC:** `file`|Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.<br /><br /> Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.|
|**/exe**|Tworzy plik wykonywalny jako dane wyjściowe. Domyślnie włączone.|
|**/flags:** `integer`|Ustawia ImageFlags na wartość określoną przez `integer` w nagłówku środowiska uruchomieniowego języka wspólnego. Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją. Zobacz CorHdr. h, COMIMAGE_FLAGS, aby uzyskać listę prawidłowych wartości dla *liczby całkowitej*.|
|**/fold**|Składa identyczne treści metod w jedną.|
|/**HIGHENTROPYVA**|Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii. (Domyślnie dla **/APPCONTAINER**).|
|**/include:** `includePath`|Ustawia ścieżkę do wyszukiwania plików dołączonych `#include`do programu.|
|**/itanium**|Określa procesor Intel Itanium jako procesor docelowy.<br /><br /> Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/pe64**.|
|**/Key:** `keyFile`|Kompiluje `keyFile`ze silnym podpisem przy użyciu klucza prywatnego zawartego w. `filename`|
|**/Key** @`keySource`|Kompiluje `keySource`ze silnym podpisem przy użyciu klucza prywatnego, który został utworzony w. `filename`|
|**/listing**|Tworzy plik listy w standardowym wyjściu. Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.<br /><br /> Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.|
|**/MDV:** `versionString`|Ustawia ciąg wersji metadanych.|
|**/MSV:** `major`.`minor`|Ustawia wersję strumienia metadanych, gdzie `major` i `minor` są liczbami całkowitymi.|
|**/noautoinherit**|Wyłącza dziedziczenie domyślne <xref:System.Object> z gdy nie określono żadnej klasy bazowej.|
|**/nocorstub**|Powoduje pominięcie generowania procedury wejścia CORExeMain.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/Output:** `file.ext`|Określa nazwę i rozszerzenie pliku wyjściowego. Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego. Domyślnym rozszerzeniem jest *. exe*. W przypadku określenia opcji **/dll** domyślne rozszerzenie to *. dll*. **Uwaga:** Określanie **/Output**: plik. dll nie ustawia opcji **/dll** . Jeśli nie określisz **/dll**, wynik będzie plikiem wykonywalnym o nazwie Moja *plik. dll*.|
|**/optimize**|Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie. Na przykład, `br` do `br.s`.|
|**/pe64**|Tworzy obraz 64-bitowy (PE32+).<br /><br /> Jeśli żaden procesor docelowy nie zostanie określony, wartość domyślna `/itanium`to.|
|**/PDB**|Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.|
|**/quiet**|Określa tryb cichy; nie zgłasza postępów zestawu.|
|**/Resource:** `file.res`|Zawiera określony plik zasobów w \*formacie. res w pliku. *exe* lub *. dll* . Tylko jeden plik. res można określić przy użyciu opcji **/Resource** .|
|**/ssver:** `int`.`int`|Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT. Dla **/APPCONTAINER** i **/ARM** minimalny numer wersji to 6,02.|
|**/Stack:** `stackSize`|Ustawia wartość SizeOfStackReserve w opcjonalnym nagłówku NT na `stackSize`.|
|**/stripreloc**|Określa, że nie są potrzebne relokacje podstawowe.|
|**/SUBSYSTEM:** `integer`|Ustawia podsystem na wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją. Aby uzyskać listę prawidłowych wartości dla `integer`programu, zobacz Winnt. h, IMAGE_SUBSYSTEM.|
|**/x64**|Określa 64-bitowy procesor firmy AMD jako procesor docelowy.<br /><br /> Jeśli nie określono liczby bitów obrazu, wartość domyślna to **/pe64**.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> Wszystkie opcje programu *Ilasm. exe* nie uwzględniają wielkości liter i są rozpoznawane przez pierwsze trzy litery. Na przykład **/lis** jest odpowiednikiem **/Listing** i **/res**: myresfile. res jest równoważne **/Resource**: myresfile. res. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/Output**:*plik. ext* jest odpowiednikiem **/Output**=*pliku. ext*.

## <a name="remarks"></a>Uwagi

Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL. Korzystając z *Ilasm. exe*, deweloperzy narzędzi i kompilatorów mogą skoncentrować się na generowaniu Il i metadanych bez konieczności wydawania kodu Il w formacie pliku PE.

Podobnie jak w przypadku innych kompilatorów przeznaczonych dla środowiska uruchomieniowego, takich jak C# i Visual Basic, *Ilasm. exe* nie tworzy pośrednich plików obiektów i nie wymaga etapów konsolidacji do utworzenia pliku PE.

Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego. Dzięki temu kod zarządzany zapisany w dowolnym z tych języków programowania może być odpowiednio wyrażony w asemblerze IL i kompilowany przy użyciu *Ilasm. exe*.

> [!NOTE]
> Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.

Programu *Ilasm. exe* można użyć w połączeniu z jego narzędziem towarzyszącym [*Ildasm. exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm. exe* pobiera plik PE zawierający kod IL i tworzy plik tekstowy odpowiedni jako dane wejściowe do *Ilasm. exe*. Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i uruchomieniu danych wyjściowych za pomocą *Ildasm. exe*wynikowy plik tekstowy Il może być edytowany ręcznie w celu dodania brakujących atrybutów. Następnie można uruchomić ten plik tekstowy za pomocą *Ilasm. exe* , aby utworzyć końcowy plik wykonywalny.

Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).

Aby te połączone użycie *Ildasm. exe* i *Ilasm. exe* były możliwie precyzyjne, domyślnie asembler nie zastępuje krótkich kodowań dla długich, które mogą zostać naliczone w źródłach Il (lub mogą być emitowane przez inny kompilator). Użyj opcji **/Optimize** , aby zastąpić krótkie kodowania, gdy jest to możliwe.

> [!NOTE]
> *Ildasm. exe* działa tylko na plikach na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse. gramatyki w Windows SDK.

## <a name="version-information"></a>Informacje o wersji

Począwszy od .NET Framework 4,5, można dołączyć atrybut niestandardowy do implementacji interfejsu za pomocą kodu podobnego do poniższego:

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

Począwszy od .NET Framework 4,5, można określić dowolny obiekt typu obiekt, który ma być zorganizowany, przy użyciu jego pierwotnej reprezentacji binarnej, jak pokazano w poniższym kodzie:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse. gramatyki w Windows SDK.

## <a name="examples"></a>Przykłady

Następujące polecenie składa plik IL *myTestFile.Il* i tworzy wykonywalny *myTestFile. exe*.

```console
ilasm myTestFile
```

Następujące polecenie składa plik IL *myTestFile.Il* i tworzy plik *dll* *myTestFile. dll*.

```console
ilasm myTestFile /dll
```

Następujące polecenie składa plik IL *myTestFile.Il* i tworzy plik *dll* *myNewTestFile. dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Poniższy przykład kodu pokazuje niezwykle prostą aplikację, która wyświetla "Hello world!" do konsoli programu. Można skompilować ten kod, a następnie użyć narzędzia [*Ildasm. exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) do wygenerowania pliku Il.

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#. Ten kod można skompilować do zestawu za pomocą narzędzia asemblera IL. Przykłady IL i C# Code wyświetlają "Hello World!" do konsoli programu.

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [*Ildasm. exe* (Il dezasembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
