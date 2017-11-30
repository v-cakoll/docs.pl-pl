---
title: Ilasm.exe (Asembler IL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4b95f3d70c7329efd1affcb333ac6eee08cc29d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (Asembler IL)

Program IL Assembler generuje przenośny plik wykonywalny (PE) na podstawie języka pośredniego (IL). (Aby uzyskać więcej informacji dotyczących IL, zobacz [proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md).) Można uruchomić wynikowy plik wykonywalny, który zawiera instrukcje języka IL i wymagane metadane, aby ustalić, czy kod w języku IL działa zgodnie z oczekiwaniami.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a>Parametry

| Argument | Opis |
| -------- | ----------- |
|`filename`|Nazwa pliku źródłowego il. Ten plik zawiera dyrektywy deklaracji metadanych i symboliczne instrukcje języka IL. Używanie wielu argumentów pliku źródłowego mogą być dostarczane do produkcji pojedynczy plik PE z *Ilasm.exe*. **Uwaga:** upewnij się, że ostatni wiersz kodu w pliku źródłowym .il ma biały spacji lub znaku końca wiersza.|

| Opcja | Opis |
| ------ | ----------- |
|**/32bitpreferred**|Tworzy obraz 32-bitowy (PE32).|
|**/ Alignment:**`integer`|Ustawia wartość określoną przez FileAlignment `integer` w nagłówku NT opcjonalne. Jeśli dyrektywa języka IL .alignment została określona w pliku, ta opcja zastępuje ją.|
|**/appcontainer**|Tworzy *.dll* lub *.exe* pliku, który jest uruchamiany w kontenerze aplikacji systemu Windows jako dane wyjściowe.|
|**/ARM**|Określa procesor Advanced RISC Machine (ARM) jako procesor docelowy.<br /><br /> Jeśli liczba bitów nie obrazu jest określony, wartością domyślną jest **/32bitpreferred**.|
|**/ base:**`integer`|Ustawia wartość określoną przez Baza obrazu `integer` w nagłówku NT opcjonalne. Jeśli dyrektywa języka IL .imagebase została określona w pliku, ta opcja zastępuje ją.|
|**/Clock**|Mierzy i raportuje następujące czasy kompilacji (w milisekundach) dla określonego pliku źródłowego il:<br /><br /> **Łączna liczba Uruchom**: całkowity czas poświęcony na wykonywanie kolejnych określonej operacji.<br /><br /> **Uruchamianie**: ładowanie i otworzyć plik.<br /><br /> **Emitowanie MD**: emitowania metadanych.<br /><br /> **Odwołanie do rozpoznawania Def**: rozpoznawania odwołań do definicji w pliku.<br /><br /> **Generowanie pliku CEE**: generowanie pliku obrazu w pamięci.<br /><br /> **Zapisywanie pliku PE**: zapisywania obraz pliku PE.|
|**/ debug**[:**IMPL**&#124; **OPT**]|Dołącza informacje o debugowaniu (zmienne lokalne, nazwy argumentów i numery wierszy). Tworzy plik PDB.<br /><br /> **/ debug** bez dodatkowych wartości powoduje wyłączenie optymalizację JIT i korzysta z pliku PDB punkty sekwencji.<br /><br /> **IMPL** wyłącza optymalizację JIT i używa punktów niejawne sekwencji.<br /><br /> **OPT** włącza optymalizację JIT i używa punktów niejawne sekwencji.|
|**/ dll**|Tworzy *.dll* pliku jako dane wyjściowe.|
|**/ENC:**`file`|Tworzy plik różnic Edytuj-i-Kontynuuj z określonego pliku źródłowego.<br /><br /> Ten argument jest tylko do użytku akademickiego i nie jest obsługiwany w użytku komercyjnym.|
|**/exe**|Tworzy plik wykonywalny jako dane wyjściowe. Domyślnie włączone.|
|**/ flags:**`integer`|Ustawia wartość określoną przez ImageFlags `integer` w nagłówku środowiska uruchomieniowego języka wspólnego. Jeśli dyrektywa języka IL .corflags została określona w pliku, ta opcja zastępuje ją. Zobacz CorHdr.h, COMIMAGE_FLAGS, aby uzyskać listę prawidłowych wartości dla *całkowitą*.|
|**/fold**|Składa identyczne treści metod w jedną.|
|/**highentropyva**|Tworzy wyjściowy plik wykonywalny, który obsługuje generowanie losowe układów przestrzeni adresowej (ASLR) o wysokiej entropii. (Wartość domyślna **/appcontainer**.)|
|**/ include:**`includePath`|Ustawia ścieżkę wyszukiwania plików uwzględnionych w `#include`.|
|**/Itanium**|Określa procesor Intel Itanium jako procesor docelowy.<br /><br /> Jeśli liczba bitów nie obrazu jest określony, wartością domyślną jest **/pe64**.|
|**/ klucz:**`keyFile`|Kompiluje `filename` za pomocą mocnej sygnatury przy użyciu klucza prywatnego zawarte w `keyFile`.|
|**następujący/key:** @`keySource`|Kompiluje `filename` za pomocą mocnej sygnatury utworzony przy użyciu klucza prywatnego w `keySource`.|
|**/ wystawienie**|Tworzy plik listy w standardowym wyjściu. Jeśli ta opcja zostanie pominięta, plik listy nie zostanie utworzony.<br /><br /> Ten parametr nie jest obsługiwany w programie .NET Framework 2.0 i nowszych.|
|**/MDV:**`versionString`|Ustawia ciąg wersji metadanych.|
|**/mSv:** `major`.`minor`|Ustawia wersję strumienia metadanych, gdy `major` i `minor` są liczbami całkowitymi.|
|**/noautoinherit**|Wyłącza domyślnej dziedziczenia z <xref:System.Object> gdy został określony parametr klasy podstawowej.|
|**/nocorstub**|Powoduje pominięcie generowania procedury wejścia CORExeMain.|
|**/ nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/ output:**`file.ext`|Określa nazwę i rozszerzenie pliku wyjściowego. Domyślnie nazwa pliku wyjściowego jest taka sama jak nazwa pierwszego pliku źródłowego. To domyślne rozszerzenie *.exe*. Jeśli określisz **/dll** opcja, to domyślne rozszerzenie *.dll*. **Uwaga:** określanie **/output**: myfile.dll nie ustawia **/dll** opcji. Jeśli nie określisz **/dll**, wynikiem będzie pliku wykonywalnego o nazwie *myfile.dll*.|
|**/ optimize**|Optymalizuje długie instrukcje, co powoduje zamianę ich na krótkie. Na przykład `br` do `br.s`.|
|**/pe64**|Tworzy obraz 64-bitowy (PE32+).<br /><br /> Jeśli nie procesor docelowy jest określony, wartością domyślną jest `/itanium`.|
|**/ PDB**|Tworzy plik PDB bez włączania śledzenia informacji o debugowaniu.|
|**/ quiet**|Określa tryb cichy; nie zgłasza postępów zestawu.|
|**/ Resource:**`file.res`|Zawiera plik zasobu określonego w \*format .res w wynikowym *.exe* lub *.dll* pliku. Za pomocą można określić tylko jeden plik .res **/Resource** opcji.|
|**/ssver:** `int`.`int`|Ustawia numer wersji podsystemu w opcjonalnym nagłówku NT. Aby uzyskać **/appcontainer** i **/arm** numer wersji jest 6.02.|
|**/ stack:**`stackSize`|Ustawia wartość SizeOfStackReserve w nagłówku NT opcjonalne `stackSize`.|
|**/stripreloc**|Określa, że nie są potrzebne relokacje podstawowe.|
|**Opcja/Subsystem:**`integer`|Ustawia wartość określoną przez podsystem `integer` w nagłówku NT opcjonalne. Jeśli dyrektywa języka IL .subsystem została określona w pliku, to polecenie zastępuje ją. Zobacz pliku winnt.h, IMAGE_SUBSYSTEM, aby uzyskać listę prawidłowych wartości dla `integer`.|
|**/x64**|Określa 64-bitowy procesor firmy AMD jako procesor docelowy.<br /><br /> Jeśli liczba bitów nie obrazu jest określony, wartością domyślną jest **/pe64**.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

> [!NOTE]
> Wszystkie opcje *Ilasm.exe* bez uwzględniania wielkości liter i jest rozpoznawana przez pierwsze trzy litery. Na przykład **/lis** jest odpowiednikiem **/wyświetlania** i **/res**: myresfile.res jest odpowiednikiem **/Resource**: myresfile.res. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output**:*file.ext* jest odpowiednikiem **/output**=*file.ext*.

## <a name="remarks"></a>Uwagi

Program IL Assembler umożliwia dostawcom narzędzi projektowanie i implementowanie generatorów języka IL. Przy użyciu *Ilasm.exe*, deweloperzy narzędzi i kompilatora może skupić się na generowaniu IL i metadanych nie jest związana z emitowanie IL w formacie pliku PE.

Podobnie jak inne kompilatory, które odnoszą się do środowiska wykonawczego, takich jak C# i Visual Basic *Ilasm.exe* nie tworzy plików pośrednich obiektu i nie wymaga połączeń etap do utworzenia pliku PE.

Program IL Assembler może wyrazić wszystkie istniejące metadane i funkcje IL języków programowania, które są przeznaczone dla środowiska uruchomieniowego. Dzięki temu zarządzany kod napisany w dowolnej z tych języków programowania odpowiednio wyrażane w asembler IL i skompilowane przy użyciu *Ilasm.exe*.

> [!NOTE]
> Kompilacja może się nie powieść, jeśli ostatni wiersz kodu w pliku źródłowym il nie kończy się znakiem odstępu ani znakiem końca wiersza.

Można użyć *Ilasm.exe* w połączeniu z jego Narzędzie Pomocnik [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* przyjmuje plik PE zawierający kod IL i tworzy plik tekstowy właściwe jako dane wejściowe *Ilasm.exe*. Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po kompilowania kodu i uruchamiania danych wyjściowych za pomocą *Ildasm.exe*, wynikowy plik tekstowy IL można edytowane ręcznie dodać brakujące atrybuty. Następnie możesz uruchomić ten plik za pomocą *Ilasm.exe* wygenerowało końcowego pliku wykonywalnego.

Tej techniki można również użyć, aby utworzyć pojedynczy plik PE z kilku plików PE, oryginalnie utworzonych przez różne kompilatory.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).

Aby to mieszane *Ildasm.exe* i *Ilasm.exe* to domyślnie precyzyjne asemblera nie zastępuje krótkich kodowań na potrzeby długich te zostały zapisane w swoich źródeł IL (lub które mogą być emitowane przez kompilator innego). Użyj **/ optimize** opcję, aby zastąpić krótkich kodowania, tam gdzie to możliwe.

> [!NOTE]
> *Ildasm.exe* działa tylko na pliki na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse.grammar w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Informacje o wersji

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], możesz dołączyć atrybutu niestandardowego do implementacji interfejsu przy użyciu kodu podobne do następujących:

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

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], można określić dowolne kierowanie obiektów BLOB (duży obiekt binarny) przy użyciu binarna reprezentacja raw, jak pokazano w poniższym kodzie:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Aby uzyskać więcej informacji na temat gramatyki IL, zobacz plik asmparse.grammar w [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Przykłady

Polecenie składana pliku IL *myTestFile.il* i tworzy plik wykonywalny *myTestFile.exe*.

```console
ilasm myTestFile
```

Polecenie składana pliku IL *myTestFile.il* i tworzy *.dll* pliku *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Polecenie składana pliku IL *myTestFile.il* i tworzy *.dll* pliku *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Poniższy przykładowy kod przedstawia bardzo prostą aplikację, która wyświetla "Witaj świecie!" w konsoli. Można skompilować ten kod, a następnie użyć [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) narzędzie do generowania pliku IL.

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

Poniższy przykład kodu w języku IL odpowiada poprzedniemu przykładowi kodu w języku C#. Ten kod można kompilować w zespół przy użyciu narzędzia asembler IL. Przykłady kodu IL jak C# wyświetlić "Witaj świecie!" w konsoli.

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

[Narzędzia](../../../docs/framework/tools/index.md)  
[*Ildasm.exe* (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)  
[Wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
