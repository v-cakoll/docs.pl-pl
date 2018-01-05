---
title: Ildasm.exe (Dezasembler IL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f42726b24abe78b151e4174da37b7c7bfff4c8d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (Dezasembler IL)

Dezasembler IL jest narzędziem Asystent asembler IL (*Ilasm.exe*). *Ildasm.exe* przyjmuje pliku przenośny plik wykonywalny (PE), który zawiera kod w języku pośrednim (IL) i tworzy plik tekstowy właściwe jako dane wejściowe *Ilasm.exe*.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```
ildasm [options] [PEfilename] [options]
```

#### <a name="parameters"></a>Parametry

Poniższe opcje są dostępne dla *.exe*, *.dll*, *.obj*, *.lib*, i *winmd* plików.

| Opcja | Opis |
| ------ | ----------- |
|**/ out =**`filename`|Tworzy plik wyjściowy z określonym `filename`, zamiast wyświetlanie wyników w graficznym interfejsie użytkownika.|
|**/RTF**|Generuje wyjście w formacie RTF. Nieprawidłowy z **można** opcji.|
|**można**|Wyświetla wyniki w oknie konsoli, a nie w graficznym interfejsie użytkownika czy plik wyjściowy.|
|**polecenia**|Generuje wyjście w formacie HTML. Prawidłowe **/output** tylko opcji.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

Następujące dodatkowe opcje są dostępne dla *.exe*, *.dll*, i *winmd* plików.

| Opcja | Opis |
| ------ | ----------- |
|**/bytes**|Pokazuje rzeczywiste bajty w formacie szesnastkowym, jak mówi instrukcja.|
|**/caverbal**|Generuje obiekty typu blob niestandardowych atrybutów w formie słownej. Domyślnie jest to forma binarna.|
|**/LineNum**|Dołącza odwołania do oryginalnych wierszy źródłowych.|
|**/nobar**|Pomija wyskakujące okienko ze wskaźnikiem postępu dezasemblera.|
|**/noca**|Pomija wyjście niestandardowych atrybutów.|
|**/ Project**|Wyświetla metadane, pojawi się tak, jak do kodu zarządzanego, zamiast sposób go w natywnym [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Jeśli `PEfilename` nie jest metadanych systemu Windows (*winmd*) pliku, ta opcja nie ma wpływu. Zobacz [.NET Framework — obsługa dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Dezasembluje tylko typy publiczne i elementy członkowskie. Odpowiednikiem **/visibility:PUB**.|
|**/quoteallnames**|Umieszcza wszystkie nazwy w pojedynczym cudzysłowie.|
|**/raweh**|Wyświetla klauzule obsługi błędów w pierwotnej formie.|
|**/ Source**|Wyświetla wiersze z oryginalnego źródła jako komentarze.|
|**/ tokens**|Wyświetla tokeny metadanych klas i składowych.|
|**/visibility:** `vis`[+`vis`...]|Dezasembluje tylko typy lub elementy członkowskie o określonej widoczności. Poniżej przedstawiono prawidłowe wartości `vis`:<br /><br /> **PUB** — publiczny<br /><br /> **PRI** — prywatne<br /><br /> **FARMA** — rodziny<br /><br /> **Funkcja ASM** — zestawu<br /><br /> **FAA** — rodziny i zestawu<br /><br /> **FOA** — rodziny lub zestawu<br /><br /> **PSC** — zakresu prywatnych<br /><br /> Definicje modyfikatorów te widoczność, zobacz <xref:System.Reflection.MethodAttributes> i <xref:System.Reflection.TypeAttributes>.|

Poniższe opcje są prawidłowe dla *.exe*, *.dll*, i *winmd* plików dla pliku lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/ all**|Określa kombinację **/header**, **/bytes**, **/stats**, **/classlist**, i **/tokeny** Opcje.|
|**/classlist**|Dołącza listę klas zdefiniowanych w module.|
|**/ do przodu**|Używa deklaracji przekazującej klasy.|
|**/headers**|Dołącza informacje nagłówka pliku do wyjścia.|
|**/ elementu:** `class`[**::** `member`[`(sig`]]|W zależności od określonego argumentu dezasembluje następujące obiekty:<br /><br /> -Rozkłada określonego `class`.<br />-Rozkłada określonego `member` z `class`.<br />-Rozkłada `member` z `class` z określoną sygnaturą `sig`. Format `sig` jest:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Uwaga** w programie .NET Framework w wersji 1.0 i 1.1, `sig` musi następować nawiasu zamykającego: `(sig)`. Począwszy od Net Framework 2.0 zamykający nawias okrągły należy pominąć: (`sig`.|
|**/noil**|Wyłącza wyjście kodu zestawu IL.|
|**/ stats**|Zawiera dane statystyczne dotyczące obrazu.|
|**/typelist**|Generuje pełną listę typów, aby zachować kolejność typów w rundzie.|
|**/Unicode**|Używa kodowania Unicode danych wyjściowych.|
|**/UTF8**|Używa kodowania UTF-8 danych wyjściowych. Domyślne jest ANSI.|

Poniższe opcje są prawidłowe dla *.exe*, *.dll*, *.obj*, *.lib*, i *winmd* pliki plik lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/METADATA**[=`specifier`]|Pokazuje metadanych, gdy `specifier` jest:<br /><br /> **MDHEADER** — Pokaż informacje o nagłówku metadanych i rozmiary.<br /><br /> **SZESNASTKOWYCH** — Pokaż informacje szesnastkowo także jak słów.<br /><br /> **CSV** — Pokaż liczby rekordów i stercie rozmiary.<br /><br /> **UNREX** — Pokaż nierozwiązane obiektów zewnętrznych.<br /><br /> **Schemat** — Pokaż informacje o nagłówku i schematu metadanych.<br /><br /> **NIEPRZETWORZONA** — Pokaż tabele metadanych raw.<br /><br /> **STOSÓW** — Pokaż nieprzetworzone stosów.<br /><br /> **Sprawdź poprawność** — Sprawdź spójność metadanych.<br /><br /> Można określić **/metadata** wiele razy przy użyciu różnych wartości `specifier`.|

Poniższe opcje są prawidłowe dla *.lib* plików dla pliku lub tylko dane wyjściowe z konsoli.

| Opcja | Opis |
| ------ | ----------- |
|**/objectfile**=`filename`|Wyświetla metadane pojedynczego pliku obiektu w określonej bibliotece.|

> [!NOTE]
> Wszystkie opcje *Ildasm.exe* bez uwzględniania wielkości liter i jest rozpoznawana przez pierwsze trzy litery. Na przykład **/quo** jest odpowiednikiem **/quoteallnames**. Opcje, które określają argumenty, akceptują dwukropek (:) lub znak równości (=) jako separator między opcją a argumentem. Na przykład **/output:** *filename* jest odpowiednikiem **/output =** *filename*.

## <a name="remarks"></a>Uwagi

*Ildasm.exe* działa tylko na PE — pliki na dysku. Nie wykonuje operacji na plikach zainstalowanych w globalnej pamięci podręcznej zestawów.

Plik tekstowy utworzonego przez *Ildasm.exe* mogą być używane jako dane wejściowe asembler IL (*Ilasm.exe*). Jest to przydatne na przykład podczas kompilowania kodu w języku programowania, który nie obsługuje wszystkich atrybutów metadanych środowiska uruchomieniowego. Kompilowanie kodu i systemem dane wyjściowe za pośrednictwem *Ildasm.exe*, wynikowy plik tekstowy IL można edytowane ręcznie dodać brakujące atrybuty. Następnie można przetworzyć ten plik tekstowym Asemblerem IL, aby wygenerować ostateczny plik wykonywalny.

> [!NOTE]
> Obecnie nie można używać tej techniki w połączeniu z plikami PE zawierającymi osadzony kod natywny (na przykład pliki PE generowane przez program Visual C++).  

Można użyć domyślnego graficznego interfejsu użytkownika dezasemblera IL, aby wyświetlić metadane i zdezasemblowany kod jakiegokolwiek istniejącego pliku PE w hierarchicznym widoku drzewa. Aby korzystać z graficznego interfejsu użytkownika, wpisz **narzędzia ildasm** w wierszu polecenia bez podawania *PEfilename* argument lub żadnych opcji. Z **pliku** menu, można przejść do pliku PE, który chcesz załadować do *Ildasm.exe*. Aby zapisać metadane i kod asemblerze wyświetlane dla wybranego środowiska Preinstalacyjnego, zaznacz **zrzutu** polecenie **pliku** menu. Aby zapisać hierarchicznego widoku drzewa wybierz pozycję tylko **zrzutu Treeview** polecenie **pliku** menu. Szczegółowy przewodnik dotyczący podczas ładowania pliku do *Ildasm.exe* i interpretowanie danych wyjściowych, zobacz *Ildasm.exe* samouczek znajdujące się w folderze przykłady, który jest dostarczany z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

Jeśli podasz *Ildasm.exe* z *PEfilename* zasobów osadzonych argument, który zawiera, narzędzie tworzy wiele plików wyjściowych: plik tekstowy, który zawiera kodu IL, dla każdego osadzonych zarządzanych zasób, plik .resources utworzone przy użyciu nazwy zasobu z metadanych. Jeśli zasób niezarządzany jest osadzony w *PEfilename*, .res jest generowany przy użyciu nazwy pliku określonej dla danych wyjściowych IL przez **/output** opcji.

> [!NOTE]
> *Ildasm.exe* zawiera tylko metadane opisy *.obj* i *.lib* pliki wejściowe. Kod IL dla tych typów plików nie jest dezasemblowany.

Można uruchomić *Ildasm.exe* za pośrednictwem an.exe lub *.dll* plik, aby określić, czy plik jest zarządzana. Jeśli plik nie jest zarządzany, narzędzie wyświetli komunikat informujący, że plik nie ma prawidłowego nagłówka środowiska uruchomieniowego języka wspólnego i nie może zostać zdezasemblowany. Jeśli plik jest zarządzany, narzędzie zostanie uruchomione pomyślnie.

## <a name="version-information"></a>Informacje o wersji

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* obsługuje nierozpoznany kierowanie obiektów BLOB (duży obiekt binarny) za pomocą wyświetlania nieprzetworzona zawartość binarną. Na przykład, poniższy kod przedstawia sposób wyświetlania skierowanego obiektu typu BLOB, wygenerowanego przez program C#.

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Począwszy od [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* Wyświetla atrybuty, które są stosowane do implementacji interfejsu, jak pokazano w poniższym fragmencie *Ildasm.exe* danych wyjściowych:

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

Poniższe polecenie powoduje, że metadane i dezasemblowania kodu dla pliku PE `MyHello.exe` do wyświetlenia w *Ildasm.exe* domyślne graficznego interfejsu użytkownika.

```console
ildasm myHello.exe
```

Poniższe polecenie powoduje wykonanie dezasemblacji pliku `MyFile.exe` i przechowuje asembler IL tekstu w pliku *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Poniższe polecenie powoduje wykonanie dezasemblacji pliku `MyFile.exe` i wyświetla tekst wynikowy asembler IL w oknie konsoli.

```console
ildasm MyFile.exe /text
```

Jeśli plik `MyApp.exe` zawiera osadzony zasoby zarządzane i niezarządzane, następujące polecenie tworzy cztery pliki: *MyApp.il*, *MyApp.res*, *Icons.resources*, i *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Poniższe polecenie powoduje wykonanie dezasemblacji metody `MyMethod` w klasie `MyClass` w `MyFile.exe` i wyświetla dane wyjściowe w oknie konsoli.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

W poprzednim przykładzie, może istnieć wiele metod o nazwie `MyMethod` z różnych podpisów. Poniższe polecenie powoduje wykonanie dezasemblacji metody wystąpienia `MyMethod` z typem zwracanym **void** i typy parametrów **int32** i **ciąg**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> W programie .NET Framework w wersjach 1.0 i 1.1, lewy nawias, stosowanej metody nazwa musi uwzględniać prawy nawias po podpisaniu: `MyMethod(instance void(int32))`. Począwszy od programu .NET Framework 2.0 zamykający nawias okrągły należy pominąć: `MyMethod(instance void(int32)`.

Aby pobrać `static` — metoda (`Shared` metody w języku Visual Basic), Pomiń słowo kluczowe `instance`. Klasa typy, które nie są typy pierwotne, takie jak `int32` i `string` musi zawierać przestrzeń nazw i musi być poprzedzona słowem kluczowym `class`. Typy zewnętrzne muszą być poprzedzone nazwą biblioteki umieszczoną w nawiasach kwadratowych. Poniższe polecenie powoduje wykonanie dezasemblacji metody statycznej o nazwie `MyMethod` który ma jeden parametr typu <xref:System.AppDomain> i ma typ zwracany <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Typ zagnieżdżony musi być poprzedzony klasą zawierającą i oddzielony od niej ukośnikiem. Na przykład jeśli `MyNamespace.MyClass` klasa zawiera zagnieżdżone klasy o nazwie `NestedClass`, zagnieżdżona klasa zostanie zidentyfikowana w następujący sposób: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Zobacz także

[Narzędzia](../../../docs/framework/tools/index.md)  
[Ilasm.exe (asembler IL)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
[Proces zarządzanego wykonania](../../../docs/standard/managed-execution-process.md)  
[Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
