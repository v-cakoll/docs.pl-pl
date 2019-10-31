---
title: Gacutil.exe (Narzędzie Global Assembly Cache)
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
ms.openlocfilehash: 87f3cb799ba4e406906759e1facd19d00c8bdace
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107499"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Narzędzie Global Assembly Cache)

Narzędzie globalnej pamięci podręcznej zestawów umożliwia wyświetlenie zawartości globalnej pamięci podręcznej zestawów i wykonywanie na niej operacji oraz pobieranie pamięci podręcznej.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|*assemblyName*|Nazwa zestawu Można podać częściowo określoną nazwę zestawu, taką jak `myAssembly`, lub w pełni określoną nazwę zestawu, taką jak `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|
|*assemblyPath*|Nazwa pliku, który zawiera manifest zestawu.|
|*Pliku plikListyZestawów*|Ścieżka do pliku tekstowego ANSI, który zawiera listę zestawów do zainstalowania lub odinstalowania. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. Narzędzie interpretuje ścieżki względne względem lokalizacji *pliku plikListyZestawów*. Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. Zobacz przykłady zawartości *pliku plikListyZestawów* w dalszej części tego tematu.|

|Opcja|Opis|
|------------|-----------------|
|**/cdl**|Usuwa zawartość pamięci podręcznej pobierania.|
|**opcją**|Aby wymusić ponowne zainstalowanie zestawu, należy określić tę opcję z opcjami **/i** lub **/Il** . Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.|
|**/h**[**ELP**]|Wyświetla składnię polecenia i opcje narzędzia.|
|**/I** *AssemblyPath*|Instaluje zestaw w globalnej pamięci podręcznej zestawów.|
|**/if**  *AssemblyPath*|Instaluje zestaw w globalnej pamięci podręcznej zestawów. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.<br /><br /> Określenie tej opcji jest równoznaczne z podaniem opcji **/i** i **/f** razem.|
|**/Il** *pliku plikListyZestawów*|Instaluje co najmniej jeden zestaw określony w *pliku plikListyZestawów* w globalnej pamięci podręcznej zestawów.|
|**/IR**  *AssemblyPath*<br /><br /> *równaniu*<br /><br /> *id*<br /><br /> *zharmonizowan*|Instaluje zestaw w globalnej pamięci podręcznej zestawów i dodaje odwołanie, aby zliczyć zestaw. Należy określić parametry *AssemblyPath*, *Schema*, *ID*i *Description* z tą opcją. Aby uzyskać opis prawidłowych wartości, które można określić dla tych parametrów, zobacz **/r** opcji.<br /><br /> Określenie tej opcji jest równoznaczne z użyciem opcji **/i** i **/r** razem.|
|**/l** [*AssemblyName*]|Wyświetla zawartość globalnej pamięci podręcznej zestawów. Jeśli określisz parametr *AssemblyName* , narzędzie wyświetli tylko zestawy pasujące do tej nazwy.|
|**/ldl**|Wyświetla zawartość pamięci podręcznej pobranych plików.|
|**/LR** [*AssemblyName*]|Wyświetla listę wszystkich zestawów i liczbę odwołań do nich. Jeśli określisz parametr *AssemblyName* , narzędzie wyświetli tylko zestawy pasujące do tej nazwy i odpowiadające im liczby odwołań.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/r** [*AssemblyName &#124; AssemblyPath*]<br /><br /> *równaniu*<br /><br /> *id*<br /><br /> *zharmonizowan*|Określa śledzone odwołanie do zestawu lub zestawów, które mają zostać zainstalowane lub odinstalowane. Określ tę opcję z opcjami **/i**, **/Il**, **/u**lub **/ul** .<br /><br /> Aby zainstalować zestaw, określ parametry *AssemblyPath*, *Schema*, *ID*i *Description* z tą opcją. Aby odinstalować zestaw, określ parametry *AssemblyName*, *schemat*, *Identyfikator*i *Opis* .<br /><br /> Aby usunąć odwołanie do zestawu, należy określić te same parametry *schemat*, *Identyfikator*i *Opis* , które zostały określone z opcjami **/i** i **/r** (lub **/IR**) podczas instalowania zestawu. W trakcie odinstalowywania zestawu narzędzie usuwa zestaw również z globalnej pamięci podręcznej zestawów, jeśli jest to ostatnie odwołanie do usunięcia i jeśli Instalator Windows nie ma innych odwołań do zestawu.<br /><br /> Parametr *schemat* określa typ schematu instalacji. Można określić jedną z następujących wartości:<br /><br /> -UNINSTALL_KEY: Określ tę wartość, jeśli Instalator doda aplikację do dodawania/usuwania programów w systemie Microsoft Windows. Aplikacje dodają same siebie do apletu Dodaj/Usuń programy przez dodanie klucza rejestru do gałęzi HKLM\Software\Microsoft\Windows\CurrentVersion.<br />-FILEPATH: Określ tę wartość, jeśli Instalator nie doda aplikacji do apletu Dodaj/Usuń programy.<br />-Nieprzezroczyste: Określ tę wartość, jeśli podanie klucza rejestru lub ścieżki pliku nie ma zastosowania do scenariusza instalacji. Ta wartość umożliwia określenie niestandardowych informacji dla parametru *ID* .<br /><br /> Wartość, która ma zostać określona dla parametru *identyfikatora* , zależy od wartości określonej dla parametru *schematu* :<br /><br /> — Jeśli dla parametru *schemat* określono wartość UNINSTALL_KEY, należy określić nazwę zestawu aplikacji w kluczu rejestru HKLM\Software\Microsoft\Windows\CurrentVersion. Na przykład, jeśli klucz rejestru to HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, określ wartość MojaApl dla parametru *ID* .<br />— Jeśli dla parametru *schemat* określono wartość FilePath, należy określić pełną ścieżkę do pliku wykonywalnego, który instaluje zestaw jako parametr *ID* .<br />— Jeśli dla parametru *schemat* określono nieprzezroczystość, można podać dowolne dane jako parametr *ID* . Podane dane muszą być ujęte w znaki cudzysłowu ("").<br /><br /> Parametr *Description* umożliwia określenie tekstu opisującego aplikację do zainstalowania. Te informacje są wyświetlane podczas wyliczania odwołań.|
|**/silent**|Pomija wyświetlanie wszystkich danych wyjściowych.|
|**/U**  *AssemblyName*|Odinstalowuje zestaw z globalnej pamięci podręcznej zestawów.|
|**/UF**  *AssemblyName*|Wymusza odinstalowanie określonego zestawu przez usunięcie wszystkich odwołań do tego zestawu.<br /><br /> Określenie tej opcji jest równoznaczne z użyciem opcji **/u** i **/f** razem. **Uwaga:**  Nie można użyć tej opcji, aby usunąć zestaw, który został zainstalowany przy użyciu Instalator Windows Microsoft. Przy próbie wykonania tej operacji narzędzie wyświetli komunikat o błędzie.|
|**/ul** *pliku plikListyZestawów*|Odinstalowuje co najmniej jeden zestaw określony w *pliku plikListyZestawów* z globalnej pamięci podręcznej zestawów.|
|**/u**[**NGen**] *AssemblyName*|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów. Jeśli istnieją odwołania do określonego zestawu, narzędzie wyświetla liczbę odwołań i nie usuwa zestawu z globalnej pamięci podręcznej zestawów. **Uwaga:**  W .NET Framework w wersji 2,0 `/ungen` nie jest obsługiwana. Zamiast tego należy użyć `uninstall` polecenia programu [Ngen. exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md). <br /><br /> W .NET Framework wersje 1,0 i 1,1, określenie **/ungen** powoduje, że Gacutil. exe usuwa zestaw z pamięci podręcznej obrazów natywnych. Ta pamięć podręczna przechowuje obrazy natywne dla zestawów, które zostały utworzone przy użyciu programu [Ngen. exe (Generator obrazu natywnego)](ngen-exe-native-image-generator.md).|
|**/ur**  *AssemblyName*<br /><br /> *równaniu*<br /><br /> *id*<br /><br /> *zharmonizowan*|Odinstalowuje odwołanie do określonego zestawu z globalnej pamięci podręcznej zestawów. Aby usunąć odwołanie do zestawu, należy określić te same parametry *schemat*, *Identyfikator*i *Opis* , które zostały określone z opcjami **/i** i **/r** (lub **/IR)** podczas instalowania zestawu. Aby uzyskać opis prawidłowych wartości, które można określić dla tych parametrów, zobacz **/r** opcji.<br /><br /> Określenie tej opcji jest równoznaczne z użyciem opcji **/u** i **/r** razem.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć programu Gacutil.exe, trzeba mieć uprawnienia administratora.

W szczególności program Gacutil.exe umożliwia instalowanie zestawów w pamięci podręcznej, usuwanie ich z pamięci podręcznej oraz wyświetlanie zawartości pamięci podręcznej.

Program Gacutil.exe oferuje opcje, które obsługują zliczanie odwołań podobne do schematu zliczania odwołań obsługiwanego przez Instalatora Windows. Programu Gacutil.exe można użyć do zainstalowania dwóch aplikacji, które instalują ten sam zestaw; narzędzie przechowuje informacje o liczbie odwołań do zestawu. W rezultacie zestaw pozostanie na komputerze do czasu, aż obie aplikacje zostaną odinstalowane. Jeśli program Gacutil.exe jest używany do instalacji rzeczywistych produktów, należy używać opcji obsługujących zliczanie odwołań. Użyj opcji **/i** i **/r** w celu zainstalowania zestawu i dodania odwołania do jego zliczenia. Użyj opcji **/u** i **/r** , aby usunąć liczbę odwołań dla zestawu. Należy pamiętać, że użycie opcji **/i** i **/u** same nie obsługuje zliczania odwołań. Te opcje są odpowiednie do użycia podczas tworzenia produktu, ale nie podczas instalacji rzeczywistego produktu.

Użyj opcji **/Il** lub **/ul** , aby zainstalować lub odinstalować listę zestawów przechowywanych w pliku tekstowym ANSI. Zawartość pliku tekstowego musi być poprawnie sformatowana. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do zainstalowania.

```text
myAssembly1.dll
myAssembly2.dll
myAssembly3.dll
```

Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do odinstalowania.

```text
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
```

> [!NOTE]
> Próba zainstalowania zestawu przy użyciu nazwy pliku o długości przekraczającej od 79 do 91 znaków (oprócz rozszerzenia pliku) może skutkować następującym błędem:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Wynika to z faktu, że wewnętrznie Gacutil. exe konstruuje ścieżkę do znaków, które składają się z następujących elementów:
>
> - Katalog główny GAC — 34 znaków (IE. `C:\Windows\Microsoft.NET\assembly\`)
> - Architektura-7 lub 9 znaków (IE. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName — do 91 znaków, w zależności od rozmiaru innych elementów (np. `System.Xml.Linq\`)
> - AssemblyInfo-31 do 48 znaków lub więcej składających się z:
>   - Framework-5 znaków (np. `v4.0_`)
>   - AssemblyVersion-8 do 24 znaków (np. `9.0.1000.0_`)
>   - AssemblyLanguage — od 1 do 8 znaków (np. `de_`, `sr-Cyrl_`)
>   - PublicKey – 17 znaków (np. `31bf3856ad364e35\`)
> - DllFileName — do 91 + 4 znaków (IE. `<AssemblyName>.dll`)

## <a name="examples"></a>Przykłady

Poniższe polecenie instaluje zestaw `mydll.dll` w globalnej pamięci podręcznej zestawów.

```console
gacutil /i mydll.dll
```

Następujące polecenie usuwa zestaw `hello` z globalnej pamięci podręcznej zestawów, o ile nie istnieją żadne liczniki odwołań dla zestawu.

```console
gacutil /u hello
```

Należy zauważyć, że poprzednie polecenie może usunąć więcej niż jeden zestaw z globalnej pamięci podręcznej zestawów, ponieważ nazwa zestawu nie została w pełni określona. Na przykład jeśli w pamięci podręcznej są zainstalowane wersje 1.0.0.0 i 3.2.2.1 `hello`, polecenie `gacutil /u hello` usuwa oba zestawy.

Aby zapobiec usuwaniu więcej niż jednego zestawu, należy użyć składni z poniższego przykładu. To polecenie usuwa tylko zestaw `hello`, który jest zgodny z w pełni określonym numerem wersji, kulturą i kluczem publicznym.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Poniższe polecenie instaluje zestawy określone w pliku `assemblyList.txt` w globalnej pamięci podręcznej zestawów.

```console
gacutil /il assemblyList.txt
```

Następujące polecenie usuwa zestawy określone w pliku `assemblyList.txt` z globalnej pamięci podręcznej zestawów.

```console
gacutil /ul assemblyList.txt
```

Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołanie do jego zliczenia. `myDll.dll` zestawu jest używany przez `MyApp`aplikacji. `UNINSTALL_KEY MyApp` parametr określa klucz rejestru, który dodaje `MyApp` do dodawania/usuwania programów w systemie Windows. Parametr Description jest określony jako `My Application Description`.

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołanie do jego zliczenia. Parametr schematu, `FILEPATH`i parametr ID, `c:\applications\myApp\myApp.exe`, określa ścieżkę do aplikacji, która jest instalowana `myDll.dll.` parametr Description jest określony jako `MyApp`.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołanie do jego zliczenia. Parametr schemat `OPAQUE`, umożliwia dostosowanie parametrów identyfikatora i opisu.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Następujące polecenie usuwa odwołanie do `myDll.dll` przez `myApp`aplikacji. Jeśli jest to ostatnie odwołanie do tego zestawu, spowoduje to również usunięcie zestawu z globalnej pamięci podręcznej zestawów.

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Poniższe polecenie wyświetla zawartość globalnej pamięci podręcznej zestawów.

```console
gacutil /l
```

## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Global Assembly Cache](../app-domains/gac.md)
- [Regasm.exe (narzędzie rejestracji zestawów)](regasm-exe-assembly-registration-tool.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
