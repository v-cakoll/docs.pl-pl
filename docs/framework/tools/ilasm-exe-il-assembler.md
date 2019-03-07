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
ms.openlocfilehash: 5b73a98542dfc6fa68e79655bc5538cf005e4636
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492592"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (Asembler IL)

Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL). (Aby uzyskać więcej informacji dotyczących języka IL, zobacz [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) Można uruchomić wynikowy plik wykonywalny, który zawiera instrukcje języka IL i wymagane metadane, aby ustalić, czy kod w języku IL działa zgodnie z oczekiwaniami.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametry

| Argument | Opis |
| -------- | ----------- |
|`filename`|Nazwa pliku źródłowego il. Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL. Wiele argumentów plików źródłowych, można go dostarczyć w celu wygenerowania pojedynczego pliku PE za pomocą *Ilasm.exe*. **Uwaga:** Należy upewnić się, że ostatnia linia kodu w pliku źródłowym il kończy się znakiem odstępu lub znakiem końca wiersza.|

| Opcja | Opis |
| ------ | ----------- |
|**/32bitpreferred**|Tworzy obraz 32-bitowy (PE32).|
|**/ Alignment:** `integer`|Ustawia dla właściwości FileAlignment wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.|
|**/ appcontainer**|Tworzy *.dll* lub *.exe* pliku, który jest uruchamiany w kontenerze aplikacji Windows jako dane wyjściowe.|
|**/ARM**|Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.<br /><br /> Jeśli nie liczby bitów obrazu jest określony, wartością domyślną jest **/32bitpreferred**.|
|**uwzględniają:** `integer`|Ustawia dla właściwości ImageBase wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.|
|**/Clock**|Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:<br /><br /> **Łączna liczba wykonywania**: Całkowity czas wykonywania wszystkich określonych operacji, które należy wykonać.<br /><br /> **Uruchamianie**: Ładowanie i otwarcie pliku.<br /><br /> **Emitowanie MD**: Emitowanie metadanych.<br /><br /> **REF zamiana**: Zamiana odwołań na definicje w pliku.<br /><br /> **Generowanie pliku CEE**: Trwa generowanie obrazu pliku w pamięci.<br /><br /> **PE pliku zapisywania**: Zapisywanie obrazu do pliku PE.|
|**/debug**[:**IMPL**&#124;**OPT**]|Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy). Tworzy plik PDB.<br /><br /> **/ debug** bez dodatkowych wartości wyłącza optymalizację JIT i używa sekwencji punktów z pliku PDB.<br /><br /> **IMPL** wyłącza optymalizację JIT i używa niejawnej sekwencji punktów.<br /><br /> **Zgłoszenie zgody na uczestnictwo** włącza optymalizację JIT i używa niejawnej sekwencji punktów.|
|**/ dll**|Tworzy *.dll* pliku jako dane wyjściowe.|
|**ENC:** `file`|Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.<br /><br /> Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.|
|**/exe**|Tworzy plik wykonywalny jako dane wyjściowe. Domyślnie włączone.|
|**/ Flags:** `integer`|Ustawia dla właściwości ImageFlags wartość określoną przez `integer` w nagłówku środowiska uruchomieniowego języka wspólnego. Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją. Zobacz sekcję CorHdr.h, COMIMAGE_FLAGS, aby uzyskać listę prawidłowych wartości dla *całkowitą*.|
|**/fold**|Składa identyczne treści metod w jedną.|
|/**highentropyva**|Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii. (Domyślne dla **/appcontainer**.)|
|**/ include:** `includePath`|Ustawia ścieżkę wyszukiwania plików dołączonych za pomocą `#include`.|
|**/Itanium**|Określa procesor Intel Itanium jako procesor docelowy.<br /><br /> Jeśli nie liczby bitów obrazu jest określony, wartością domyślną jest **/pe64**.|
|**następujący/key:** `keyFile`|Kompiluje `filename` za pomocą silnego podpisu, używając klucza prywatnego zawartego w `keyFile`.|
|**/key:** @`keySource`|Kompiluje `filename` za pomocą mocnej sygnatury przy użyciu klucza prywatnego utworzonego w lokalizacji `keySource`.|
|**/ wystawienie**|Tworzy plik listy w standardowym wyjściu. Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.<br /><br /> Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.|
|**MDV:** `versionString`|Ustawia ciąg wersji metadanych.|
|**/msv:** `major`.`minor`|Ustawia wersję strumienia metadanych, gdzie `major` i `minor` są liczbami całkowitymi.|
|**/noautoinherit**|Wyłącza domyślne dziedziczenie z <xref:System.Object> gdy określono nie ma klasy podstawowej.|
|**/nocorstub**|Powoduje pominięcie generowania procedury wejścia CORExeMain.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/ Output:** `file.ext`|Określa nazwę i rozszerzenie pliku wyjściowego. Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego. Domyślnym rozszerzeniem jest *.exe*. Jeśli określisz **/dll** opcji domyślnym rozszerzeniem jest *.dll*. **Uwaga:** Określanie **/output**: mój_plik.dll nie powoduje ustawienia **/dll** opcji. Jeśli nie określisz **/dll**, wynikiem będzie plik wykonywalny o nazwie *mój_plik.dll*.|
|**/optimize**|Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie. Na przykład `br` do `br.s`.|
|**/pe64**|Tworzy obraz 64-bitowy (PE32+).<br /><br /> Jeśli procesor docelowy nie jest określony, wartością domyślną jest `/itanium`.|
|**/ PDB**|Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.|
|**/quiet**|Określa tryb cichy; nie zgłasza postępów zestawu.|
|**/ Resource:** `file.res`|Określony zasób znajduje się plik w \*formatem res w wynikowym *.exe* lub *.dll* pliku. Za pomocą można określić tylko jeden plik res **/Resource** opcji.|
|**ssver:** `int`.`int`|Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT. Aby uzyskać **/appcontainer** i **/arm** minimalny numer wersji to 6.02.|
|**/Stack:** `stackSize`|Ustawia wartość SizeOfStackReserve w opcjonalnym nagłówku NT równą `stackSize`.|
|**/stripreloc**|Określa, że nie są potrzebne relokacje podstawowe.|
|**Opcja/Subsystem:** `integer`|Ustawia dla opcji subsystem wartość określoną przez `integer` w opcjonalnym nagłówku NT. Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją. Zobacz opis pliku winnt.h, IMAGE_SUBSYSTEM, aby uzyskać listę prawidłowych wartości dla `integer`.|
|**/x64**|Określa 64-bitowy procesor firmy AMD jako procesor docelowy.<br /><br /> Jeśli nie liczby bitów obrazu jest określony, wartością domyślną jest **/pe64**.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> Wszystkie opcje *Ilasm.exe* jest rozróżniana wielkość liter i rozpoznawane na podstawie pierwszych trzech liter. Na przykład **/lis** jest odpowiednikiem **/listing** i **/res —**: mój_plik_zasobów.res jest równoważna **/Resource**: mój_plik_zasobów.res. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output**:*plik.roz* jest odpowiednikiem **/output**=*plik.roz*.

## <a name="remarks"></a>Uwagi

Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL. Za pomocą *Ilasm.exe*, deweloperzy narzędzi i kompilatorów mogą skupić się na generowania IL i metadanych bez emitowaniem IL w formacie pliku PE.

Podobnie jak inne kompilatory, przeznaczonych dla środowiska uruchomieniowego, takich jak C# i Visual Basic *Ilasm.exe* nie tworzy plików obiektów pośrednich i nie wymaga etapu łączenia, aby utworzyć plik PE.

Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego. Dzięki temu kod zarządzany napisany w każdym z tych języków programowania może być odpowiednio wyrażany w programie IL Assembler i kompilowany przy użyciu *Ilasm.exe*.

> [!NOTE]
> Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.

Możesz użyć *Ilasm.exe* w połączeniu z jego pomocniczym narzędziem [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* przyjmuje plik PE, który zawiera kod IL i tworzy plik tekstowy odpowiedni jako wejście do *Ilasm.exe*. Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i przetworzeniu danych wyjściowych za pomocą *Ildasm.exe*, wynikowy plik tekstowy IL może być ręcznie edytowany w celu dodania brakujących atrybutów. Następnie możesz uruchomić ten plik za pomocą *Ilasm.exe* aby wygenerować ostateczny plik wykonywalny.

Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).

Aby to mieszane *Ildasm.exe* i *Ilasm.exe* możliwie domyślnie dokładny asembler nie podstawić krótkie kodowanie dla długich te, które zostały napisane w źródłach IL (lub które mogło zostać wyemitowane przez inny kompilator). Użyj **/ optimize** opcję, aby podstawić krótkie kodowanie tam gdzie to możliwe.

> [!NOTE]
> *Ildasm.exe* operuje tylko na plikach zapisanych na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Aby uzyskać więcej informacji dotyczących gramatyki języka IL, zobacz opis pliku asmparse.grammar w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Informacje o wersji

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], można dołączyć atrybut niestandardowy do implementacji interfejsu używając kodu podobnego do następującego:

```
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

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], można określić umownego organizatora BLOB (duży obiekt binarny) za pomocą jego nieprzetworzonej reprezentacji binarnej, jak pokazano w poniższym kodzie:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Aby uzyskać więcej informacji dotyczących gramatyki języka IL, zobacz opis pliku asmparse.grammar w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Przykłady

Poniższe polecenie składa plik IL *myTestFile.il* i tworzy plik wykonywalny *myTestFile.exe*.

```console
ilasm myTestFile
```

Poniższe polecenie składa plik IL *myTestFile.il* i tworzy *.dll* pliku *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Poniższe polecenie składa plik IL *myTestFile.il* i tworzy *.dll* pliku *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

W poniższym przykładzie kodu pokazano bardzo prostą aplikację, która wyświetla "Hello World!" w konsoli. Można skompilować ten kod, a następnie użyć [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) tool do wygenerowania pliku IL.

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

Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#. Ten kod można skompilować do zestawu za pomocą narzędzia asemblera IL. Zarówno IL i C# przykłady kodu wyświetlić "Hello World!" w konsoli.

```
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
- [*Ildasm.exe* (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)
- [Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
