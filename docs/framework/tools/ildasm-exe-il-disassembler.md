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
ms.openlocfilehash: f23f8c48a31dffa7d350c872aed7505da7a36861
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105057"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Dezasembler IL)

Dezasembler IL jest narzędziem towarzyszącym Asemblerowi IL (*Ilasm. exe*). *Ildasm. exe* pobiera przenośny plik wykonywalny (PE), który zawiera kod języka pośredniego (IL) i tworzy plik tekstowy odpowiedni jako dane wejściowe do *Ilasm. exe*.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Dostępne są następujące opcje dla plików *exe*, *dll*, *obj*, *lib*i *winmd* .

| Opcja | Opis |
| ------ | ----------- |
|**/out =** `filename`|Tworzy plik wyjściowy o określonym `filename`, zamiast wyświetlać wyniki w graficznym interfejsie użytkownika.|
|**/rtf**|Generuje wyjście w formacie RTF. Nieprawidłowa z opcją **/Text** .|
|**/Text**|Wyświetla wyniki w oknie konsoli, a nie w graficznym interfejsie użytkownika czy plik wyjściowy.|
|**/html**|Generuje wyjście w formacie HTML. Prawidłowy tylko z opcją **/Output** .|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

Następujące dodatkowe opcje są dostępne dla plików *exe*, *dll*i *winmd* .

| Opcja | Opis |
| ------ | ----------- |
|**/bytes**|Pokazuje rzeczywiste bajty w formacie szesnastkowym, jak mówi instrukcja.|
|**/caverbal**|Generuje obiekty typu blob niestandardowych atrybutów w formie słownej. Domyślnie jest to forma binarna.|
|**/linenum**|Dołącza odwołania do oryginalnych wierszy źródłowych.|
|**/nobar**|Pomija wyskakujące okienko ze wskaźnikiem postępu dezasemblera.|
|**/noca**|Pomija wyjście niestandardowych atrybutów.|
|**/Project**|Wyświetla metadane, tak jak pojawiają się one w kodzie zarządzanym, a nie w sposób pojawiający się w środowisko wykonawcze systemu Windows macierzystym. Jeśli `PEfilename` nie jest plikiem metadanych systemu Windows (*winmd*), ta opcja nie ma żadnego wpływu. Zobacz [.NET Framework obsługa aplikacji do sklepu Windows i środowisko wykonawcze systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Dezasembluje tylko typy publiczne i elementy członkowskie. Odpowiednik **/Visibility: pub**.|
|**/quoteallnames**|Umieszcza wszystkie nazwy w pojedynczym cudzysłowie.|
|**/raweh**|Wyświetla klauzule obsługi błędów w pierwotnej formie.|
|**/source**|Wyświetla wiersze z oryginalnego źródła jako komentarze.|
|**/tokens**|Wyświetla tokeny metadanych klas i składowych.|
|**/Visibility:** `vis`[+`vis`...]|Dezasembluje tylko typy lub elementy członkowskie o określonej widoczności. Następujące wartości są prawidłowe dla `vis`:<br /><br /> **Pub** — publiczny<br /><br /> **Pri** — prywatny<br /><br /> **Farma** — rodzina<br /><br /> **ASM** — zestaw<br /><br /> **FAA** — rodzina i zestaw<br /><br /> **FOA** — rodzina lub zestaw<br /><br /> **PSC** — zakres prywatny<br /><br /> Aby zapoznać się z definicjami tych modyfikatorów widoczności, zobacz <xref:System.Reflection.MethodAttributes> i <xref:System.Reflection.TypeAttributes>.|

Następujące opcje są prawidłowe dla plików *exe*, *dll*i *winmd* tylko dla plików wyjściowych w pliku lub konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/All**|Określa kombinację opcji **/header**, **/Bytes**, **/stats**, **/classlist**i **/Tokens** .|
|**/classlist**|Dołącza listę klas zdefiniowanych w module.|
|**/forward**|Używa deklaracji przekazującej klasy.|
|**/Headers**|Dołącza informacje nagłówka pliku do wyjścia.|
|**/Item:** `class`[ **::** `member`[`(sig`]]|W zależności od określonego argumentu dezasembluje następujące obiekty:<br /><br /> — Rozkłada określony `class`.<br />— Rozkłada określony `member` `class`.<br />-Łączy `member` `class` z określoną sygnaturą `sig`. Format `sig` to:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`,..., `parameterTypeN`)<br />     **Uwaga** W .NET Framework wersje 1,0 i 1,1 `sig` musi następować nawias zamykający: `(sig)`. Począwszy od platformy NET Framework 2,0 nawias zamykający musi zostać pominięty: `(sig`.|
|**/noil**|Wyłącza wyjście kodu zestawu IL.|
|**/stats**|Zawiera dane statystyczne dotyczące obrazu.|
|**/typelist**|Generuje pełną listę typów, aby zachować kolejność typów w rundzie.|
|**/unicode**|Używa kodowania Unicode danych wyjściowych.|
|**/utf8**|Używa kodowania UTF-8 danych wyjściowych. Domyślne jest ANSI.|

Następujące opcje są prawidłowe dla plików *exe*, *dll*, *obj*, *lib*i *winmd* tylko w przypadku plików wyjściowych w pliku lub konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/Metadata**[=`specifier`]|Pokazuje metadane, gdzie `specifier`:<br /><br /> **MDHEADER** — wyświetla informacje i rozmiary nagłówka metadanych.<br /><br /> **HEX** — Pokaż informacje w postaci szesnastkowej, a także słowa.<br /><br /> **CSV** — pokazuje liczbę rekordów i rozmiary sterty.<br /><br /> **UNREX** — Pokaż nierozpoznane zewnętrzne.<br /><br /> **Schemat** — pokazuje nagłówek metadanych i informacje o schemacie.<br /><br /> **RAW** — wyświetlanie nieprzetworzonych tabel metadanych.<br /><br /> **Sterty** — Pokaż nieprzetworzone sterty.<br /><br /> **Sprawdź** poprawność — Sprawdź spójność metadanych.<br /><br /> Można określić **/Metadata** wiele razy, z różnymi wartościami dla `specifier`.|

Poniższe opcje są prawidłowe dla plików *lib* tylko dla plików wyjściowych w pliku lub konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/objectfile**=`filename`|Wyświetla metadane pojedynczego pliku obiektu w określonej bibliotece.|

> [!NOTE]
> Wszystkie opcje programu *Ildasm. exe* nie uwzględniają wielkości liter i są rozpoznawane przez pierwsze trzy litery. Na przykład **/quo** jest odpowiednikiem **/quoteallnames**. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/Output:** *filename* jest równoważne **/Output =** *filename*.

## <a name="remarks"></a>Uwagi

*Ildasm. exe* działa tylko na plikach PE na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Plik tekstowy utworzony przez *Ildasm. exe* może być używany jako dane wejściowe do asemblera Il (*Ilasm. exe*). Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i uruchomieniu jego danych wyjściowych za pomocą *Ildasm. exe*wynikowy plik tekstowy Il może być edytowany ręcznie w celu dodania brakujących atrybutów. Następnie można przetworzyć ten plik tekstowym Asemblerem IL, aby wygenerować ostateczny plik wykonywalny.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).  

Można użyć domyślnego graficznego interfejsu użytkownika dezasemblera IL, aby wyświetlić metadane i zdezasemblowany kod jakiegokolwiek istniejącego pliku PE w hierarchicznym widoku drzewa. Aby użyć graficznego interfejsu użytkownika, wpisz **Ildasm** w wierszu polecenia bez podawania argumentu *PEfilename* ani żadnych opcji. Z menu **plik** można przejść do pliku PE, który ma zostać załadowany do *Ildasm. exe*. Aby zapisać metadane i rozłożony kod wyświetlany dla wybranego środowiska PE, wybierz polecenie **Zrzuć** z menu **plik** . Aby zapisać hierarchiczny widok drzewa, wybierz polecenie **Zrzuć TreeView** z menu **plik** . Szczegółowy przewodnik dotyczący ładowania pliku do programu *Ildasm. exe* i interpretowania danych wyjściowych znajduje się w samouczku *Ildasm. exe* , który znajduje się w folderze Samples, który jest dostarczany z Windows SDK.

Jeśli podano *Ildasm. exe* z argumentem *PEfilename* zawierającym osadzone zasoby, narzędzie tworzy wiele plików wyjściowych: plik tekstowy zawierający kod IL oraz, dla każdego osadzonego zasobu zarządzanego, plik resources utworzony przy użyciu Nazwa zasobu na podstawie metadanych. Jeśli zasób niezarządzany jest osadzony w *PEfilename*, plik. res jest tworzony przy użyciu nazwy pliku określonej dla danych wyjściowych Il przez opcję **/Output** .

> [!NOTE]
> *Ildasm. exe* wyświetla tylko opisy metadanych dla plików wejściowych *. obj* i *. lib* . Kod IL dla tych typów plików nie jest dezasemblowany.

Można uruchomić *Ildasm. exe* w pliku exe lub *dll* , aby określić, czy plik jest zarządzany. Jeśli plik nie jest zarządzany, narzędzie wyświetli komunikat informujący, że plik nie ma prawidłowego nagłówka środowiska uruchomieniowego języka wspólnego i nie może zostać zdezasemblowany. Jeśli plik jest zarządzany, narzędzie zostanie uruchomione pomyślnie.

## <a name="version-information"></a>Informacje o wersji

Począwszy od .NET Framework 4,5, *Ildasm. exe* obsługuje nierozpoznany zorganizowany obiekt BLOB (duży obiekt binarny), wyświetlając nieprzetworzoną zawartość binarną. Na przykład, poniższy kod przedstawia sposób wyświetlania skierowanego obiektu typu BLOB, wygenerowanego przez program C#.

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Począwszy od .NET Framework 4,5, *Ildasm. exe* Wyświetla atrybuty, które są stosowane do implementacji interfejsu, jak pokazano w poniższym fragmencie danych wyjściowych programu *Ildasm. exe* :

```il
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

Poniższe polecenie powoduje, że metadane i rozłożony kod dla pliku PE `MyHello.exe` być wyświetlana w domyślnym interfejsie GUI *Ildasm. exe* .

```console
ildasm myHello.exe
```

Następujące polecenie odłączy plik `MyFile.exe` i zapisuje otrzymany tekst asemblera IL w pliku *myfile.Il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Następujące polecenie odłączy plik `MyFile.exe` i wyświetla otrzymany tekst asemblera IL do okna konsoli.

```console
ildasm MyFile.exe /text
```

Jeśli plik `MyApp.exe` zawiera osadzone zarządzane i niezarządzane zasoby, następujące polecenie generuje cztery pliki: *MyApp.Il*, *MojaApl. res*, *ikon. resources*i *Message. resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Następujące polecenie odłączy metodę `MyMethod` w klasie `MyClass` w `MyFile.exe` i wyświetla dane wyjściowe w oknie konsoli.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

W poprzednim przykładzie może istnieć kilka metod o nazwie `MyMethod` z różnymi podpisami. Następujące polecenie deasembleruje metodę wystąpienia `MyMethod` z typem zwracanym **void** i typami parametrów **Int32** i **String**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> W .NET Framework wersje 1,0 i 1,1, po lewej stronie nazwy metody muszą być zrównoważone po prawej stronie po podpisie: `MyMethod(instance void(int32))`. Począwszy od .NET Framework 2,0 nawias zamykający musi zostać pominięty: `MyMethod(instance void(int32)`.

Aby pobrać metodę `static` (`Shared` Metoda w Visual Basic), Pomiń `instance`słowa kluczowego. Typy klas, które nie są typami pierwotnymi, takimi jak `int32` i `string`, muszą zawierać przestrzeń nazw i muszą być poprzedzone `class`em słowa kluczowego. Typy zewnętrzne muszą być poprzedzone nazwą biblioteki umieszczoną w nawiasach kwadratowych. Następujące polecenie deasembleruje metodę statyczną o nazwie `MyMethod`, która ma jeden parametr typu <xref:System.AppDomain> i ma zwracany typ <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Typ zagnieżdżony musi być poprzedzony klasą zawierającą i oddzielony od niej ukośnikiem. Na przykład, jeśli Klasa `MyNamespace.MyClass` zawiera zagnieżdżoną klasę o nazwie `NestedClass`, Klasa zagnieżdżona jest identyfikowana w następujący sposób: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Ilasm.exe (asembler IL)](ilasm-exe-il-assembler.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
