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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105057"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Dezasembler IL)

IL Disassembler jest narzędziem towarzyszącym asembleru IL *(Ilasm.exe).* *Ildasm.exe* pobiera przenośny plik wykonywalny (PE), który zawiera kod języka pośredniego (IL) i tworzy plik tekstowy odpowiedni jako wejście do *Ilasm.exe*.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Następujące opcje są dostępne dla plików *.exe*, *.dll*, *.obj*, *.lib*i *.winmd.*

| Opcja | Opis |
| ------ | ----------- |
|**/out=**`filename`|Tworzy plik wyjściowy `filename`z określonym , zamiast wyświetlania wyników w graficznym interfejsie użytkownika.|
|**/rtf**|Generuje wyjście w formacie RTF. Nieprawidłowy z opcją **/text.**|
|**/tekst**|Wyświetla wyniki w oknie konsoli, a nie w graficznym interfejsie użytkownika czy plik wyjściowy.|
|**/html**|Generuje wyjście w formacie HTML. Jest prawidłowy tylko z opcją **/output.**|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

Następujące dodatkowe opcje są dostępne dla plików *.exe*, *.dll*i *.winmd.*

| Opcja | Opis |
| ------ | ----------- |
|**/bajty**|Pokazuje rzeczywiste bajty w formacie szesnastkowym, jak mówi instrukcja.|
|**/caverbal**|Generuje obiekty typu blob niestandardowych atrybutów w formie słownej. Domyślnie jest to forma binarna.|
|**/len**|Dołącza odwołania do oryginalnych wierszy źródłowych.|
|**/nobar**|Pomija wyskakujące okienko ze wskaźnikiem postępu dezasemblera.|
|**/noca**|Pomija wyjście niestandardowych atrybutów.|
|**/projekt**|Wyświetla metadane w sposób, w jaki wydaje się zarządzać kodem, a nie sposób, w jaki pojawia się w macierzystym środowisku wykonawczego systemu Windows. Jeśli `PEfilename` nie jest to plik metadanych systemu Windows (*.winmd),* ta opcja nie ma wpływu. Zobacz [.NET Framework Support for Windows Store Apps and Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Dezasembluje tylko typy publiczne i elementy członkowskie. Odpowiednik **/visibility:PUB**.|
|**/quoteallnames**|Umieszcza wszystkie nazwy w pojedynczym cudzysłowie.|
|**/raweh**|Wyświetla klauzule obsługi błędów w pierwotnej formie.|
|**/źródło**|Wyświetla wiersze z oryginalnego źródła jako komentarze.|
|**/tokeny**|Wyświetla tokeny metadanych klas i składowych.|
|**/widoczność:** `vis``vis`[+ ...]|Dezasembluje tylko typy lub elementy członkowskie o określonej widoczności. Poniżej znajdują się `vis`prawidłowe wartości dla:<br /><br /> **PUB** — Publiczny<br /><br /> **PRI** — Prywatny<br /><br /> **FAM** — Rodzina<br /><br /> **ASM** — Montaż<br /><br /> **FAA** — Rodzina i montaż<br /><br /> **FOA** — Rodzina lub Montaż<br /><br /> **PSC** — zakres prywatny<br /><br /> Definicje tych modyfikatorów <xref:System.Reflection.MethodAttributes> widoczności można znaleźć w części . <xref:System.Reflection.TypeAttributes>|

Następujące opcje są prawidłowe dla plików *.exe*, *.dll*i *.winmd* tylko dla plików lub danych wyjściowych konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/wszystkie**|Określa kombinację opcji **/header**, **/bytes**, **/stats**, **/classlist**i **/tokens.**|
|**/lista klas**|Dołącza listę klas zdefiniowanych w module.|
|**/do przodu**|Używa deklaracji przekazującej klasy.|
|**/nagłówki**|Dołącza informacje nagłówka pliku do wyjścia.|
|**/item:** `class`[**::** `member`[`(sig`]]|W zależności od określonego argumentu dezasembluje następujące obiekty:<br /><br /> - Dezasembles określony `class`.<br />- Dezasembles określony `member` z `class`.<br />- Dezasembles `member` z `class` określonym podpisem `sig`. Format `sig` jest:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Uwaga** W .NET Framework w wersjach 1.0 `sig` i 1.1 musi `(sig)`następować nawias zamykający: . Począwszy od net framework 2.0 nawias zamykający `(sig`należy pominąć: .|
|**/noil (nie)**|Wyłącza wyjście kodu zestawu IL.|
|**/statystyki**|Zawiera dane statystyczne dotyczące obrazu.|
|**/lista typów**|Generuje pełną listę typów, aby zachować kolejność typów w rundzie.|
|**/unicode**|Używa kodowania Unicode danych wyjściowych.|
|**/utf8**|Używa kodowania UTF-8 danych wyjściowych. Domyślne jest ANSI.|

Następujące opcje są prawidłowe dla plików *.exe*, *.dll*, *.obj*, *.lib*i *.winmd* tylko dla plików lub plików wyjściowych konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/metadane**`specifier`[= ]|Pokazuje metadane, gdzie `specifier` jest:<br /><br /> **MDHEADER** — pokaż informacje nagłówka metadanych i rozmiary.<br /><br /> **HEX** — Pokaż informacje w hex, jak również w słowach.<br /><br /> **CSV** — pokaż liczby rekordów i rozmiary sterty.<br /><br /> **UNREX** — Pokaż nierozwiązane elementy zewnętrzne.<br /><br /> **SCHEMAT** — pokaż nagłówek metadanych i informacje o schemacie.<br /><br /> **RAW** — pokaż nieprzetworzone tabele metadanych.<br /><br /> **HEAPS** — pokaż surowe stery.<br /><br /> **SPRAWDŹ POPRAWNOŚĆ** — sprawdź spójność metadanych.<br /><br /> Można określić **/metadane** wiele razy, z różnymi wartościami dla `specifier`.|

Poniższe opcje są *prawidłowe* dla plików lib tylko dla danych wyjściowych plików lub konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/objectfile**=`filename`|Wyświetla metadane pojedynczego pliku obiektu w określonej bibliotece.|

> [!NOTE]
> Wszystkie opcje programu *Ildasm.exe* są niewrażliwe na wielkość liter i rozpoznawane przez pierwsze trzy litery. Na przykład **/quo** jest odpowiednikiem **/quoteallnames**. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output:** *nazwa pliku* jest odpowiednikiem **/output=** *nazwa pliku*.

## <a name="remarks"></a>Uwagi

*Ildasm.exe* działa tylko na plikach PE na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Plik tekstowy wyprodukowany przez *Ildasm.exe* może być używany jako wejście do IL Assembler (*Ilasm.exe*). Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Po skompilowaniu kodu i uruchomieniu jego danych wyjściowych za pośrednictwem *pliku Ildasm.exe*wynikowy plik tekstowy IL może być ręcznie edytowany w celu dodania brakujących atrybutów. Następnie można przetworzyć ten plik tekstowym Asemblerem IL, aby wygenerować ostateczny plik wykonywalny.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).  

Można użyć domyślnego graficznego interfejsu użytkownika dezasemblera IL, aby wyświetlić metadane i zdezasemblowany kod jakiegokolwiek istniejącego pliku PE w hierarchicznym widoku drzewa. Aby użyć graficznego interfejsu użytkownika, wpisz **ildasm** w wierszu polecenia bez pokazania argumentu *PEfilename* ani żadnych opcji. Z menu **Plik** można przejść do pliku PE, który chcesz załadować do *pliku Ildasm.exe*. Aby zapisać metadane i zdemontowany kod wyświetlany dla wybranego PE, wybierz polecenie **Zrzut** z menu **Plik.** Aby zapisać tylko widok drzewa hierarchicznego, wybierz polecenie **Dump Treeview** z menu **Plik.** Aby uzyskać szczegółowy przewodnik po załadowaniu pliku do *pliku Ildasm.exe* i interpretacji danych wyjściowych, zobacz *samouczek Ildasm.exe,* znajdujący się w folderze Samples dostarczanym z zestawem Windows SDK.

Jeśli podasz *programowi Ildasm.exe* argument *PEfilename* zawierający zasoby osadzone, narzędzie tworzy wiele plików wyjściowych: plik tekstowy zawierający kod IL oraz, dla każdego osadzonego zasobu zarządzanego, plik .resources wyprodukowany przy użyciu nazwy zasobu z metadanych. Jeśli niezarządzany zasób jest osadzony w *pliku PEfilename,* plik .res jest produkowany przy użyciu nazwy pliku określonego dla danych wyjściowych IL przez opcję **/output.**

> [!NOTE]
> *Program Ildasm.exe* pokazuje tylko opisy metadanych dla plików wejściowych *.obj* i *.lib.* Kod IL dla tych typów plików nie jest dezasemblowany.

Program *Ildasm.exe* można uruchomić za pomocą pliku an.exe lub *dll,* aby ustalić, czy plik jest zarządzany. Jeśli plik nie jest zarządzany, narzędzie wyświetli komunikat informujący, że plik nie ma prawidłowego nagłówka środowiska uruchomieniowego języka wspólnego i nie może zostać zdezasemblowany. Jeśli plik jest zarządzany, narzędzie zostanie uruchomione pomyślnie.

## <a name="version-information"></a>Informacje o wersji

Począwszy od .NET Framework 4.5, *Ildasm.exe* obsługuje nierozpoznany obiekt BLOB marshal (binarny duży obiekt) przez wyświetlanie nieprzetworzonej zawartości binarnej. Na przykład, poniższy kod przedstawia sposób wyświetlania skierowanego obiektu typu BLOB, wygenerowanego przez program C#.

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Począwszy od programu .NET Framework 4.5, *program Ildasm.exe* wyświetla atrybuty stosowane do implementacji interfejsu, jak pokazano w poniższym fragmencie danych *wyjściowych Ildasm.exe:*

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

Następujące polecenie powoduje, że metadane i zdemontowany kod `MyHello.exe` pliku PE mają być wyświetlane w domyślnym interfejsie GUI *ildasm.exe.*

```console
ildasm myHello.exe
```

Poniższe polecenie dezmontuje plik `MyFile.exe` i przechowuje wynikowy tekst asemblera IL w pliku *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Następujące polecenie powoduje demontaż pliku `MyFile.exe` i wyświetla wynikowy tekst asemblera IL w oknie konsoli.

```console
ildasm MyFile.exe /text
```

Jeśli plik `MyApp.exe` zawiera osadzone zasoby zarządzane i niezarządzane, następujące polecenie generuje cztery pliki: *MyApp.il*, *MyApp.res*, *Icons.resources*i *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Następujące polecenie dezażemble w `MyMethod` klasie `MyClass` `MyFile.exe` i wyświetla dane wyjściowe do okna konsoli.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

W poprzednim przykładzie może istnieć `MyMethod` kilka metod nazwanych z różnymi podpisami. Następujące polecenie dezasembles metody `MyMethod` wystąpienia z typu zwracanego **void** i typy parametrów **int32** i **string**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> W .NET Framework w wersjach 1.0 i 1.1 lewy nawias, który następuje po nazwie metody, musi być równoważony prawym nawiasem po podpisie: `MyMethod(instance void(int32))`. Począwszy od programu .NET Framework 2.0, należy `MyMethod(instance void(int32)`pominąć nawias zamykający: .

Aby pobrać `static` metodę`Shared` (metodę w języku Visual `instance`Basic), pomiń słowo kluczowe . Typy klas, które nie `int32` są `string` typami pierwotnymi, takimi jak i `class`muszą zawierać obszar nazw i muszą być poprzedzone słowem kluczowym . Typy zewnętrzne muszą być poprzedzone nazwą biblioteki umieszczoną w nawiasach kwadratowych. Następujące polecenie dezasembles metody statycznej o `MyMethod` nazwie, <xref:System.AppDomain> która ma jeden <xref:System.AppDomain>parametr typu i ma typ zwracany .

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Typ zagnieżdżony musi być poprzedzony klasą zawierającą i oddzielony od niej ukośnikiem. Na przykład jeśli `MyNamespace.MyClass` klasa zawiera klasę `NestedClass`zagnieżdżoną o nazwie `class MyNamespace.MyClass/NestedClass`, klasa zagnieżdżona jest identyfikowana w następujący sposób: .

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Ilasm.exe (asembler IL)](ilasm-exe-il-assembler.md)
- [Proces zarządzanego wykonania](../../standard/managed-execution-process.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
