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
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105094"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (Asembler IL)

Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL). (Aby uzyskać więcej informacji na temat il, zobacz [Managed Execution Process](../../standard/managed-execution-process.md).) Można uruchomić wynikowy plik wykonywalny, który zawiera IL i wymagane metadane, aby ustalić, czy IL działa zgodnie z oczekiwaniami.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametry

| Argument | Opis |
| -------- | ----------- |
|`filename`|Nazwa pliku źródłowego il. Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL. W celu wytworzenia pojedynczego pliku PE z *plikiem Ilasm.exe*można podać wiele argumentów pliku źródłowego. **Uwaga:** Upewnij się, że ostatni wiersz kodu w pliku źródłowym .il ma znak końcowy lub znak końca wiersza.|

| Opcja | Opis |
| ------ | ----------- |
|**/32bitpreferred**|Tworzy obraz 32-bitowy (PE32).|
|**/wyrównanie:**`integer`|Ustawia wyrównanie pliku na wartość `integer` określoną w nagłówku OPCJONALNY NT. Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.|
|**/appcontainer**|Tworzy plik *dll* lub exe, który działa w kontenerze aplikacji systemu Windows jako dane *wyjściowe.*|
|**/ramię**|Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.<br /><br /> Jeśli nie określono bitowości obrazu, wartość domyślna to **/32bitprepreferred**.|
|**/baza:**`integer`|Ustawia ImageBase na wartość `integer` określoną w nagłówku OPCJONALNY NT. Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.|
|**/zegar**|Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:<br /><br /> **Całkowita liczba uruchomionych:** całkowity czas spędzony na wykonywaniu wszystkich określonych operacji, które następują.<br /><br /> **Uruchamianie:** Ładowanie i otwieranie pliku.<br /><br /> **Emitowanie MD:** Emitowanie metadanych.<br /><br /> **Ref to Def Rozdzielczość:** Rozwiązywanie odwołań do definicji w pliku.<br /><br /> **Generowanie plików CEE**: Generowanie obrazu pliku w pamięci.<br /><br /> **Pisanie plików PE:** Zapisywanie obrazu w pliku PE.|
|**/debug**[:**IMPL**&#124;**OPT**]|Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy). Tworzy plik PDB.<br /><br /> **/debug** bez dodatkowej wartości wyłącza optymalizację JIT i używa punktów sekwencji z pliku PDB.<br /><br /> **IMPL** wyłącza optymalizację JIT i używa niejawnych punktów sekwencji.<br /><br /> **OPT** umożliwia optymalizację JIT i używa niejawnych punktów sekwencji.|
|**/dll**|Tworzy plik *dll* jako dane wyjściowe.|
|**/enc:**`file`|Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.<br /><br /> Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.|
|**/exe**|Tworzy plik wykonywalny jako dane wyjściowe. Domyślnie włączone.|
|**/flags:**`integer`|Ustawia ImageFlags do wartości `integer` określonej w nagłówku środowiska wykonawczego języka wspólnego. Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją. Zobacz CorHdr.h, COMIMAGE_FLAGS listę prawidłowych wartości dla *liczby całkowitej*.|
|**/złożyć**|Składa identyczne treści metod w jedną.|
|/**wysoka poziomtropywy**|Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii. (Domyślnie dla **/appcontainer**.)|
|**/include:**`includePath`|Ustawia ścieżkę wyszukiwania plików dołączonych do `#include`programu .|
|**/itanium**|Określa procesor Intel Itanium jako procesor docelowy.<br /><br /> Jeśli nie określono bitowości obrazu, wartością domyślną jest **/pe64**.|
|**/key:**`keyFile`|Kompiluje `filename` się z silnym podpisem `keyFile`przy użyciu klucza prywatnego zawartego w pliku .|
|**/key:** @`keySource`|Kompiluje `filename` z silnym podpisem przy `keySource`użyciu klucza prywatnego produkowanego w .|
|**/aukcja**|Tworzy plik listy w standardowym wyjściu. Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.<br /><br /> Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.|
|**/mdv:**`versionString`|Ustawia ciąg wersji metadanych.|
|**/msv:** `major`.`minor`|Ustawia wersję strumienia metadanych, gdzie `major` i `minor` są liczby całkowite.|
|**/noautoinherit**|Wyłącza domyślne <xref:System.Object> dziedziczenie, gdy nie określono żadnej klasy podstawowej.|
|**/nocorstub**|Powoduje pominięcie generowania procedury wejścia CORExeMain.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/wyjście:**`file.ext`|Określa nazwę i rozszerzenie pliku wyjściowego. Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego. Domyślnym rozszerzeniem jest *.exe*. Jeśli określisz opcję **/dll,** domyślnym rozszerzeniem jest *.dll*. **Uwaga:** Określenie **/output**:myfile.dll nie ustawia opcji **/dll.** Jeśli nie określisz **/dll**, wynikiem będzie plik wykonywalny o nazwie *myfile.dll*.|
|**/optymalizacja**|Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie. Na przykład `br` `br.s`do .|
|**/pe64**|Tworzy obraz 64-bitowy (PE32+).<br /><br /> Jeśli nie określono żadnego procesora docelowego, wartością domyślną jest `/itanium`.|
|**/pdb**|Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.|
|**/cichy**|Określa tryb cichy; nie zgłasza postępów zestawu.|
|**/zasób:**`file.res`|Zawiera określony plik \*zasobu w formacie .res w wynikowym pliku *exe* lub *dll.* Za pomocą opcji **/resource** można określić tylko jeden plik .res.|
|**/ssver:** `int`.`int`|Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT. Dla **/appcontainer** i **/arm** minimalny numer wersji to 6.02.|
|**/stos:**`stackSize`|Ustawia wartość SizeOfStackReserve w nagłówku `stackSize`NT Optional na .|
|**/stripreloc**|Określa, że nie są potrzebne relokacje podstawowe.|
|**/podsystem:**`integer`|Ustawia podsystem na wartość `integer` określoną w nagłówku NT Opcjonalne. Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją. Zobacz winnt.h, IMAGE_SUBSYSTEM listę prawidłowych wartości `integer`dla .|
|**/x64**|Określa 64-bitowy procesor firmy AMD jako procesor docelowy.<br /><br /> Jeśli nie określono bitowości obrazu, wartością domyślną jest **/pe64**.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> Wszystkie opcje *ilasm.exe* są niewrażliwe na wielkość liter i rozpoznawane przez pierwsze trzy litery. Na przykład **/lis** jest odpowiednikiem **/listing** i **/res**:myresfile.res jest odpowiednikiem **/resource**:myresfile.res. Opcje określające argumenty akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output**:*file.ext* jest odpowiednikiem **pliku /output**=*file.ext*.

## <a name="remarks"></a>Uwagi

Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL. Za pomocą *Ilasm.exe*, narzędzia i kompilator deweloperzy mogą skoncentrować się na IL i generowania metadanych bez zajmowania się emitowania IL w formacie PE.

Podobnie jak inne kompilatory, które są przeznaczone dla środowiska wykonawczego, takie jak C# i Visual Basic, *Ilasm.exe* nie generuje plików obiektów pośrednich i nie wymaga etapu łączenia do utworzenia pliku PE.

Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego. Dzięki temu kod zarządzany napisany w dowolnym z tych języków programowania może być odpowiednio wyrażony w IL Assembler i skompilowany z *Ilasm.exe*.

> [!NOTE]
> Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.

Program *Ilasm.exe* można używać w połączeniu z narzędziem towarzyszącym [*Ildasm.exe*](ildasm-exe-il-disassembler.md). *Ildasm.exe* pobiera plik PE, który zawiera kod IL i tworzy plik tekstowy odpowiedni jako wejście do *Ilasm.exe*. Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i uruchomieniu danych wyjściowych za pośrednictwem *pliku Ildasm.exe*wynikowy plik tekstowy IL może być ręcznie edytowany w celu dodania brakujących atrybutów. Następnie można uruchomić ten plik tekstowy za pośrednictwem *pliku Ilasm.exe,* aby utworzyć ostateczny plik wykonywalny.

Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).

Aby to połączone użycie *Ildasm.exe* i *Ilasm.exe* było jak najbardziej dokładne, domyślnie asembler nie zastępuje krótkich kodowania dla długich, które mogły być napisane w źródłach IL (lub które mogą być emitowane przez inny kompilator). Użyj opcji **/optimize,** aby zastąpić krótkie kodowania tam, gdzie to możliwe.

> [!NOTE]
> *Ildasm.exe* działa tylko na plikach na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Aby uzyskać więcej informacji na temat gramatyki il, zobacz asmparse.grammar pliku w windows SDK.

## <a name="version-information"></a>Informacje o wersji

Począwszy od programu .NET Framework 4.5, można dołączyć atrybut niestandardowy do implementacji interfejsu przy użyciu kodu podobnego do następującego:

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

Począwszy od programu .NET Framework 4.5, można określić dowolny obiekt BLOB (binarny duży obiekt) przy użyciu jego surowej reprezentacji binarnej, jak pokazano w poniższym kodzie:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Aby uzyskać więcej informacji na temat gramatyki il, zobacz asmparse.grammar pliku w windows SDK.

## <a name="examples"></a>Przykłady

Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik wykonywalny *myTestFile.exe*.

```console
ilasm myTestFile
```

Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik *dll* *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Następujące polecenie składa plik IL *myTestFile.il* i tworzy plik *.dll* *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Poniższy przykład kodu pokazuje niezwykle prostą aplikację, która wyświetla "Hello World!" w konsoli. Można skompilować ten kod, a następnie użyć narzędzia [*Ildasm.exe*](ildasm-exe-il-disassembler.md) do wygenerowania pliku IL.

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

Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#. Ten kod można skompilować do zestawu przy użyciu narzędzia IL Assembler. Zarówno IL i C# kod przykłady wyświetlają "Hello World!" w konsoli.

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

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [*Ildasm.exe* (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
