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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107499"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Narzędzie Global Assembly Cache)

Narzędzie globalnej pamięci podręcznej zestawów umożliwia wyświetlenie zawartości globalnej pamięci podręcznej zestawów i wykonywanie na niej operacji oraz pobieranie pamięci podręcznej.

To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).

W wierszu polecenia wpisz następujące polecenie:

## <a name="syntax"></a>Składnia

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametry

|Argument|Opis|
|--------------|-----------------|
|*Assemblyname*|Nazwa zestawu Można podać częściowo określoną nazwę zestawu, `myAssembly` taką jak lub w `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`pełni określoną nazwę zestawu, taką jak .|
|*ścieżka zestawu*|Nazwa pliku, który zawiera manifest zestawu.|
|*assemblyListFile*|Ścieżka do pliku tekstowego ANSI, który zawiera listę zestawów do zainstalowania lub odinstalowania. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. Narzędzie interpretuje ścieżki względne względem lokalizacji *assemblyListFile*. Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. Zobacz *assemblyListFile* przykłady zawartości w dalszej części tego tematu.|

|Opcja|Opis|
|------------|-----------------|
|**/cdl**|Usuwa zawartość pamięci podręcznej pobierania.|
|**/f**|Określ tę opcję za pomocą opcji **/i** lub **/il,** aby wymusić ponowną instalację złożenia. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.|
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|
|**/i** *assemblyPath*|Instaluje zestaw w globalnej pamięci podręcznej zestawów.|
|**/if**  *AssemblyPath*|Instaluje zestaw w globalnej pamięci podręcznej zestawów. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.<br /><br /> Określenie tej opcji jest równoznaczne z określeniem opcji **/i** i **/f** razem.|
|**/il** *assemblyListFile*|Instaluje jeden lub więcej zestawów określonych w *assemblyListFile* do globalnej pamięci podręcznej zestawów.|
|**/ir**  *assemblyPath*<br /><br /> *Schemat*<br /><br /> *Identyfikator*<br /><br /> *Opis*|Instaluje zestaw w globalnej pamięci podręcznej zestawów i dodaje odwołanie, aby zliczyć zestaw. Za pomocą tej opcji należy określić *parametry assemblyPath*, *scheme,* *id* *i description.* Aby uzyskać opis prawidłowych wartości, które można określić dla tych parametrów, zobacz **/r** opcji.<br /><br /> Określenie tej opcji jest równoznaczne z określeniem opcji **/i** i **/r** razem.|
|**/l** [*nazwa zestawu*]|Wyświetla zawartość globalnej pamięci podręcznej zestawów. Jeśli określisz *parametr assemblyName,* narzędzie wyświetla tylko zestawy pasujące do tej nazwy.|
|**/ldl**|Wyświetla zawartość pamięci podręcznej pobranych plików.|
|**/lr** [*nazwa zestawu*]|Wyświetla listę wszystkich zestawów i liczbę odwołań do nich. Jeśli określisz *parametr assemblyName,* narzędzie wyświetla tylko zestawy pasujące do tej nazwy i ich odpowiednią liczbę odwołań.|
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *Schemat*<br /><br /> *Identyfikator*<br /><br /> *Opis*|Określa śledzone odwołanie do zestawu lub zestawów, które mają zostać zainstalowane lub odinstalowane. Określ tę opcję z opcjami **/i**, **/il**, **/u**lub **/ul.**<br /><br /> Aby zainstalować złożenie, należy określić *parametry assemblyPath,* *scheme,* *id*i *description* z tą opcją. Aby odinstalować zestaw, należy określić *parametry assemblyName*, *scheme*, *id*i *description.*<br /><br /> Aby usunąć odwołanie do złożenia, należy określić ten sam *schemat*, *identyfikator*i parametry *opisu,* które zostały określone za pomocą opcji **/i** i **/r** (lub **/ir)** podczas instalowania zestawu. W trakcie odinstalowywania zestawu narzędzie usuwa zestaw również z globalnej pamięci podręcznej zestawów, jeśli jest to ostatnie odwołanie do usunięcia i jeśli Instalator Windows nie ma innych odwołań do zestawu.<br /><br /> Parametr *scheme* określa typ schematu instalacji. Można określić jedną z następujących wartości:<br /><br /> - UNINSTALL_KEY: Określ tę wartość, jeśli instalator doda aplikację do dodawania/usuwania programów w systemie Microsoft Windows. Aplikacje dodają same siebie do apletu Dodaj/Usuń programy przez dodanie klucza rejestru do gałęzi HKLM\Software\Microsoft\Windows\CurrentVersion.<br />- FILEPATH: Określ tę wartość, jeśli instalator nie doda aplikacji do dodawania/usuwania programów.<br />- OPAQUE: Określ tę wartość, jeśli dostarczanie klucza rejestru lub ścieżki pliku nie ma zastosowania do scenariusza instalacji. Ta wartość umożliwia określenie informacji niestandardowych dla parametru *id.*<br /><br /> Wartość określona dla parametru *id* zależy od wartości określonej dla parametru *schematu:*<br /><br /> - Jeśli określisz UNINSTALL_KEY *parametru schematu,* określ nazwę zestawu aplikacji w kluczu rejestru HKLM\Software\Microsoft\Windows\CurrentVersion. Jeśli na przykład kluczem rejestru jest HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, określ myapp dla parametru *id.*<br />- Jeśli określisz FILEPATH dla parametru *schematu,* określ pełną ścieżkę do pliku wykonywalnego, który instaluje zestaw jako parametr *id.*<br />- Jeśli określisz OPAQUE dla parametru *scheme,* można podać dowolny fragment danych jako parametr *id.* Podane dane muszą być ujęte w znaki cudzysłowu ("").<br /><br /> Parametr *opisu* umożliwia określenie opisowego tekstu o aplikacji do zainstalowania. Te informacje są wyświetlane podczas wyliczania odwołań.|
|**/silent**|Pomija wyświetlanie wszystkich danych wyjściowych.|
|**/u**  *nazwa zestawu*|Odinstalowuje zestaw z globalnej pamięci podręcznej zestawów.|
|**/uf**  *assemblyName*|Wymusza odinstalowanie określonego zestawu przez usunięcie wszystkich odwołań do tego zestawu.<br /><br /> Określenie tej opcji jest równoznaczne z określeniem opcji **/u** i **/f** razem. **Uwaga:**  Tej opcji nie można użyć do usunięcia zestawu zainstalowanego przy użyciu Instalatora Microsoft Windows. Przy próbie wykonania tej operacji narzędzie wyświetli komunikat o błędzie.|
|**/ul** *assemblyListFile*|Odinstalowuje jeden lub więcej zestawów określonych w *assemblyListFile* z globalnej pamięci podręcznej zestawów.|
|**/u**[**ngen**] *nazwa zestawu*|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów. Jeśli istnieją odwołania do określonego zestawu, narzędzie wyświetla liczbę odwołań i nie usuwa zestawu z globalnej pamięci podręcznej zestawów. **Uwaga:**  W .NET Framework w wersji 2.0 nie `/ungen` jest obsługiwany. Zamiast tego należy `uninstall` użyć polecenia [Ngen.exe (Generator obrazu macierzystego)](ngen-exe-native-image-generator.md). <br /><br /> W .NET Framework w wersjach 1.0 i 1.1, określenie **/ungen** powoduje Gacutil.exe, aby usunąć zestaw z pamięci podręcznej obrazu macierzystego. Ta pamięć podręczna przechowuje obrazy macierzyste dla zestawów, które zostały utworzone przy użyciu [pliku Ngen.exe (Generator natywnych obrazów).](ngen-exe-native-image-generator.md)|
|**/ur**  *assemblyName*<br /><br /> *Schemat*<br /><br /> *Identyfikator*<br /><br /> *Opis*|Odinstalowuje odwołanie do określonego zestawu z globalnej pamięci podręcznej zestawów. Aby usunąć odwołanie do złożenia, należy określić ten sam *schemat*, *identyfikator*i parametry *opisu,* które zostały określone za pomocą opcji **/i** **/r** (lub **/ir)** podczas instalowania zestawu. Aby uzyskać opis prawidłowych wartości, które można określić dla tych parametrów, zobacz **/r** opcji.<br /><br /> Określenie tej opcji jest równoznaczne z określeniem opcji **/u** i **/r** razem.|
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Aby użyć programu Gacutil.exe, trzeba mieć uprawnienia administratora.

W szczególności program Gacutil.exe umożliwia instalowanie zestawów w pamięci podręcznej, usuwanie ich z pamięci podręcznej oraz wyświetlanie zawartości pamięci podręcznej.

Program Gacutil.exe oferuje opcje, które obsługują zliczanie odwołań podobne do schematu zliczania odwołań obsługiwanego przez Instalatora Windows. Programu Gacutil.exe można użyć do zainstalowania dwóch aplikacji, które instalują ten sam zestaw; narzędzie przechowuje informacje o liczbie odwołań do zestawu. W rezultacie zestaw pozostanie na komputerze do czasu, aż obie aplikacje zostaną odinstalowane. Jeśli program Gacutil.exe jest używany do instalacji rzeczywistych produktów, należy używać opcji obsługujących zliczanie odwołań. Użyj **/i** **i /r** opcje razem zainstalować zestaw i dodać odwołanie, aby go policzyć. Użyj **/u** i **/r** opcje razem, aby usunąć liczbę odwołań dla zestawu. Należy pamiętać, że przy użyciu **/i** i **/u** opcje sam nie obsługuje zliczania odwołań. Te opcje są odpowiednie do użycia podczas tworzenia produktu, ale nie podczas instalacji rzeczywistego produktu.

Użyj opcji **/il** lub **/ul,** aby zainstalować lub odinstalować listę zestawów przechowywanych w pliku tekstowym ANSI. Zawartość pliku tekstowego musi być poprawnie sformatowana. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do zainstalowania.

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
> Próba zainstalowania złożenia o nazwie pliku dłuższej niż od 79 do 91 znaków (z wyłączeniem rozszerzenia pliku) może spowodować następujący błąd:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Dzieje się tak dlatego, że wewnętrznie Gacutil.exe tworzy ścieżkę do MAX_PATH znaków, która składa się z następujących elementów:
>
> - GAC Root - 34 znaków (tj. `C:\Windows\Microsoft.NET\assembly\`)
> - Architektura - 7 lub 9 znaków (tj. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - Nazwa złożenia — do 91 znaków, w zależności od wielkości pozostałych elementów (np. `System.Xml.Linq\`)
> - AssemblyInfo - 31 do 48 znaków lub więcej składających się z:
>   - Ramy - 5 znaków (np. `v4.0_`)
>   - AssemblyVersion - 8 do 24 znaków (np. `9.0.1000.0_`)
>   - MontażLanguage - 1 do 8 znaków (np. `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 znaków (np. `31bf3856ad364e35\`)
> - DllFileName - Do 91 + 4 znaków (tj. `<AssemblyName>.dll`)

## <a name="examples"></a>Przykłady

Następujące polecenie instaluje `mydll.dll` zestaw w globalnej pamięci podręcznej zestawów.

```console
gacutil /i mydll.dll
```

Następujące polecenie usuwa zestaw `hello` z globalnej pamięci podręcznej zestawów, o ile nie istnieją żadne liczby odwołań dla zestawu.

```console
gacutil /u hello
```

Należy zauważyć, że poprzednie polecenie może usunąć więcej niż jeden zestaw z globalnej pamięci podręcznej zestawów, ponieważ nazwa zestawu nie została w pełni określona. Na przykład jeśli zarówno w wersji 1.0.0.0 i 3.2.2.1 `hello` `gacutil /u hello` są zainstalowane w pamięci podręcznej, polecenie usuwa oba zestawy.

Aby zapobiec usuwaniu więcej niż jednego zestawu, należy użyć składni z poniższego przykładu. To polecenie usuwa `hello` tylko zestaw, który pasuje do w pełni określony numer wersji, kultury i klucza publicznego.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Następujące polecenie instaluje zestawy określone `assemblyList.txt` w pliku w globalnej pamięci podręcznej zestawów.

```console
gacutil /il assemblyList.txt
```

Następujące polecenie usuwa zestawy określone w `assemblyList.txt` pliku z globalnej pamięci podręcznej zestawów.

```console
gacutil /ul assemblyList.txt
```

Następujące polecenie instaluje się w globalnej pamięci podręcznej zestawów `myDll.dll` i dodaje odwołanie, aby je zliczyć. Zespół `myDll.dll` jest używany przez `MyApp`aplikację . Parametr `UNINSTALL_KEY MyApp` określa klucz rejestru, `MyApp` który dodaje do dodaj/usuń programy w systemie Windows. Parametr opisu jest `My Application Description`określony jako .

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Następujące polecenie instaluje się w globalnej pamięci podręcznej zestawów `myDll.dll` i dodaje odwołanie, aby je zliczyć. Parametr `FILEPATH`scheme i parametr id `c:\applications\myApp\myApp.exe`, określ ścieżkę do `myDll.dll.` aplikacji, która instaluje Parametr opisu jest określony jako `MyApp`.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Następujące polecenie instaluje się w globalnej pamięci podręcznej zestawów `myDll.dll` i dodaje odwołanie, aby je zliczyć. Parametr schematu `OPAQUE`umożliwia dostosowanie parametrów identyfikatora i opisu.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Następujące polecenie usuwa odwołanie `myDll.dll` do aplikacji `myApp`. Jeśli jest to ostatnie odwołanie do tego zestawu, spowoduje to również usunięcie zestawu z globalnej pamięci podręcznej zestawów.

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Poniższe polecenie wyświetla zawartość globalnej pamięci podręcznej zestawów.

```console
gacutil /l
```

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Global Assembly Cache](../app-domains/gac.md)
- [Regasm.exe (narzędzie rejestracji zestawów)](regasm-exe-assembly-registration-tool.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
