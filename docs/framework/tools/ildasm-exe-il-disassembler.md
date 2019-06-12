---
title: Ildasm.exe (Dezasembler IL)
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2239b73eb8418d469085ad72b8a28093146a1f6b
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025969"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Dezasembler IL)

Dezasembler IL jest narzędziem wspomagającym IL Assembler (*Ilasm.exe*). *Ildasm.exe* przyjmuje plików przenośnych plików wykonywalnych (PE), który zawiera kod języka pośredniego (IL) i tworzy plik tekstowy odpowiedni jako wejście do *Ilasm.exe*.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Poniższe opcje są dostępne dla *.exe*, *.dll*, *.obj*, *.lib*, i *winmd* plików.

| Opcja | Opis |
| ------ | ----------- |
|**/ out =** `filename`|Tworzy plik wyjściowy z określonym `filename`, zamiast wyświetlić wyniki w graficzny interfejs użytkownika.|
|**/rtf**|Generuje wyjście w formacie RTF. Nieprawidłowa z **/Text** opcji.|
|**/ Text**|Wyświetla wyniki w oknie konsoli, a nie w graficznym interfejsie użytkownika czy plik wyjściowy.|
|**polecenia**|Generuje wyjście w formacie HTML. Prawidłowy **/output** opcja dotyczy tylko.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

Następujące dodatkowe opcje są dostępne dla *.exe*, *.dll*, i *winmd* plików.

| Opcja | Opis |
| ------ | ----------- |
|**/bytes**|Pokazuje rzeczywiste bajty w formacie szesnastkowym, jak mówi instrukcja.|
|**/caverbal**|Generuje obiekty typu blob niestandardowych atrybutów w formie słownej. Domyślnie jest to forma binarna.|
|**/LineNum**|Dołącza odwołania do oryginalnych wierszy źródłowych.|
|**/nobar**|Pomija wyskakujące okienko ze wskaźnikiem postępu dezasemblera.|
|**/noca**|Pomija wyjście niestandardowych atrybutów.|
|**/project**|Wyświetla metadane, pojawi się tak, jak dla kodu zarządzanego, a nie jej natywnego środowiska wykonawczego Windows. Jeśli `PEfilename` nie jest metadanych Windows (*winmd*) pliku, ta opcja nie ma wpływu. Zobacz [Obsługa programu .NET Framework dla aplikacji Windows Store i środowiska wykonawczego Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Dezasembluje tylko typy publiczne i elementy członkowskie. Odpowiednikiem **/visibility:PUB**.|
|**/quoteallnames**|Umieszcza wszystkie nazwy w pojedynczym cudzysłowie.|
|**/raweh**|Wyświetla klauzule obsługi błędów w pierwotnej formie.|
|**/ Source**|Wyświetla wiersze z oryginalnego źródła jako komentarze.|
|**/tokens**|Wyświetla tokeny metadanych klas i składowych.|
|**visibility:** `vis`[+`vis`...]|Dezasembluje tylko typy lub elementy członkowskie o określonej widoczności. Poniżej przedstawiono prawidłowe wartości dla `vis`:<br /><br /> **PUB** — publiczny<br /><br /> **PRI** — prywatny<br /><br /> **Rozproszona** — rodzina<br /><br /> **ASM** — zestawu<br /><br /> **FAA** — Rodzina i zestaw<br /><br /> **FOA** — Rodzina lub zestaw<br /><br /> **PSC** — zasięg prywatny<br /><br /> Aby uzyskać definicje tych modyfikatorów widoczności, zobacz <xref:System.Reflection.MethodAttributes> i <xref:System.Reflection.TypeAttributes>.|

Poniższe opcje są prawidłowe dla *.exe*, *.dll*, i *winmd* plików dla pliku lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/ all**|Określa kombinację **/header**, **/bytes**, **/stats**, **/classlist**, i **/tokens** Opcje.|
|**/classlist**|Dołącza listę klas zdefiniowanych w module.|
|**/ kreska**|Używa deklaracji przekazującej klasy.|
|**/headers**|Dołącza informacje nagłówka pliku do wyjścia.|
|**/ item:** `class`[ **::** `member`[`(sig`]]|W zależności od określonego argumentu dezasembluje następujące obiekty:<br /><br /> -Dezasembluje określoną klasę `class`.<br />-Dezasembluje określoną klasę `member` z `class`.<br />-Dezasembluje `member` z `class` o określonej sygnaturze `sig`. Format `sig` jest:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Uwaga** w programie .NET Framework w wersjach 1.0 i 1.1, `sig` musi następować nawias zamykający: `(sig)`. Począwszy od programu Net Framework 2.0, nawias zamykający musi zostać pominięty: `(sig`.|
|**/noil**|Wyłącza wyjście kodu zestawu IL.|
|**/ stats**|Zawiera dane statystyczne dotyczące obrazu.|
|**/typelist**|Generuje pełną listę typów, aby zachować kolejność typów w rundzie.|
|**/unicode**|Używa kodowania Unicode danych wyjściowych.|
|**/UTF8**|Używa kodowania UTF-8 danych wyjściowych. Domyślne jest ANSI.|

Poniższe opcje są prawidłowe dla *.exe*, *.dll*, *.obj*, *.lib*, i *winmd* pliki plik lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/METADATA**[=`specifier`]|Wyświetla metadane, gdzie `specifier` jest:<br /><br /> **MDHEADER** — Wyświetla informacje nagłówka metadanych i rozmiary.<br /><br /> **SZESNASTKOWY** — Pokaż informacji i szesnastkowo słownie.<br /><br /> **CSV** — Wyświetla liczbę rekordów i rozmiar stosu.<br /><br /> **UNREX** — Wyświetla nierozpoznane obiekty zewnętrzne.<br /><br /> **Schemat** — zawierają informacje o nagłówku i schematu metadanych.<br /><br /> **NIEPRZETWORZONE** — Pokaż tabele surowych metadanych.<br /><br /> **STOSY** — Wyświetla surowe stosy.<br /><br /> **Sprawdź poprawność** — Waliiduje spójność metadanych.<br /><br /> Można określić **/metadata** wiele razy z różnymi wartościami dla `specifier`.|

Poniższe opcje są prawidłowe dla *.lib* plików dla pliku lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/objectfile**=`filename`|Wyświetla metadane pojedynczego pliku obiektu w określonej bibliotece.|

> [!NOTE]
> Wszystkie opcje *Ildasm.exe* jest rozróżniana wielkość liter i rozpoznawane na podstawie pierwszych trzech liter. Na przykład **/quo** jest odpowiednikiem **/quoteallnames**. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output:** *filename* jest odpowiednikiem **/output =** *filename*.

## <a name="remarks"></a>Uwagi

*Ildasm.exe* operuje tylko na plikach PE na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Plik tekstowy produkowane przez *Ildasm.exe* mogą być używane jako wejście do asemblera IL (*Ilasm.exe*). Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i przetworzeniu jego wyjścia przez *Ildasm.exe*, wynikowy plik tekstowy IL może być ręcznie edytowany w celu dodania brakujących atrybutów. Następnie można przetworzyć ten plik tekstowym Asemblerem IL, aby wygenerować ostateczny plik wykonywalny.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).  

Można użyć domyślnego graficznego interfejsu użytkownika dezasemblera IL, aby wyświetlić metadane i zdezasemblowany kod jakiegokolwiek istniejącego pliku PE w hierarchicznym widoku drzewa. Aby użyć graficznego interfejsu użytkownika, wpisz **ildasm** w wierszu polecenia bez podawania *PEfilename* argument lub żadnych opcji. Z **pliku** menu, możesz przejść do pliku PE, który chcesz załadować do *Ildasm.exe*. Aby zapisać metadane i dezasemblowany kod wyświetlone dla wybranego PE, zaznacz **zrzutu** polecenia **pliku** menu. Aby zapisać hierarchiczny widok drzewa, wybierz **Zrzuć widok drzewa** polecenia **pliku** menu. Aby uzyskać szczegółowy poradnik na potrzeby ładowania pliku do *Ildasm.exe* i interpretowanie danych wyjściowych, zobacz *Ildasm.exe* samouczek, znajduje się w folderze Samples, dostarczany z Windows Software Development Kit (SDK ).

Jeśli podasz *Ildasm.exe* z *PEfilename* argument, który zawiera osadzone zasoby, narzędzie wygeneruje wiele plików wyjściowych: plik tekstowy, który zawiera kod IL i dla każdego z osadzonych zarządzanych zasób, plik Resource wygenerowany przy użyciu nazwy zasobu z metadanych. Jeśli w jest osadzony niezarządzany zasób *PEfilename*, generowany jest plik res, przy użyciu nazwy pliku określonej dla wyjścia IL za **/output** opcji.

> [!NOTE]
> *Ildasm.exe* pokazuje tylko opisy metadanych dla *.obj* i *.lib* plików wejściowych. Kod IL dla tych typów plików nie jest dezasemblowany.

Możesz uruchomić *Ildasm.exe* za pośrednictwem an.exe lub *.dll* plik, aby określić, czy plik jest zarządzany. Jeśli plik nie jest zarządzany, narzędzie wyświetli komunikat informujący, że plik nie ma prawidłowego nagłówka środowiska uruchomieniowego języka wspólnego i nie może zostać zdezasemblowany. Jeśli plik jest zarządzany, narzędzie zostanie uruchomione pomyślnie.

## <a name="version-information"></a>Informacje o wersji

Począwszy od programu .NET Framework 4.5 *Ildasm.exe* obsługuje nierozpoznane skierowane obiekty typu BLOB (duży obiekt binarny) przez wyświetlanie surowej zawartości binarnej. Na przykład, poniższy kod przedstawia sposób wyświetlania skierowanego obiektu typu BLOB, wygenerowanego przez program C#.

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Począwszy od programu .NET Framework 4.5 *Ildasm.exe* Wyświetla atrybuty, które są stosowane do implementacji interfejsu, jak pokazano w poniższym fragmencie *Ildasm.exe* dane wyjściowe:

```
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a>Przykłady

Następujące polecenie powoduje, że metadane i kod dezasemblowany dla pliku PE `MyHello.exe` do wyświetlenia w *Ildasm.exe* domyślne graficznego interfejsu użytkownika.

```console
ildasm myHello.exe
```

Następujące polecenie dezasembluje plik `MyFile.exe` i zapisuje wynikowy tekst z asemblera IL w pliku *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Następujące polecenie dezasembluje plik `MyFile.exe` i wyświetla wynikowy tekst z asemblera IL w oknie konsoli.

```console
ildasm MyFile.exe /text
```

Jeśli plik `MyApp.exe` zawiera osadzone zarządzane i niezarządzane zasoby, następujące polecenie generuje cztery pliki: *MyApp.il*, *MyApp.res*, *Icons.resources*, i *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Następujące polecenie dezasembluje metodę `MyMethod` w klasie `MyClass` w `MyFile.exe` i wyświetla dane wyjściowe do okna konsoli.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

W poprzednim przykładzie, może istnieć wiele metod o nazwie `MyMethod` z różnymi podpisami. Następujące polecenie dezasembluje wystąpienie metody `MyMethod` z typem zwracanym **void** i typy parametrów **int32** i **ciąg**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> W programie .NET Framework nazw w wersjach 1.0 i 1.1, lewy nawias, który następuje po metodzie musi być równoważony przez prawy nawias po podpisie: `MyMethod(instance void(int32))`. Począwszy od programu .NET Framework 2.0, nawias zamykający musi zostać pominięty: `MyMethod(instance void(int32)`.

Aby pobrać `static` — metoda (`Shared` w języku Visual Basic), Pomiń słowo kluczowe `instance`. Typy, które nie są typy pierwotne, takie jak klasy `int32` i `string` musi zawierać przestrzeń nazw i musi być poprzedzona słowem kluczowym `class`. Typy zewnętrzne muszą być poprzedzone nazwą biblioteki umieszczoną w nawiasach kwadratowych. Następujące polecenie dezasembluje statyczną metodę o nazwie `MyMethod` posiadającą jeden parametr typu <xref:System.AppDomain> i ma typ zwracany <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Typ zagnieżdżony musi być poprzedzony klasą zawierającą i oddzielony od niej ukośnikiem. Na przykład jeśli `MyNamespace.MyClass` klasa zawiera klasę zagnieżdżoną o nazwie `NestedClass`, zagnieżdżona klasa jest identyfikowana w następujący sposób: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
