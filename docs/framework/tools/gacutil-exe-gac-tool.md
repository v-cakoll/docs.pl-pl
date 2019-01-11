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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1dac8aec7f565b82797ba179fc01968e00bf36b
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54223081"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Narzędzie Global Assembly Cache)
Narzędzie globalnej pamięci podręcznej zestawów umożliwia wyświetlenie zawartości globalnej pamięci podręcznej zestawów i wykonywanie na niej operacji oraz pobieranie pamięci podręcznej.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyName*|Nazwa zestawu Można podać nazwę częściowo określonego zestawu, taką jak `myAssembly` lub nazwę w pełni określonego zestawu, taką jak `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*Ścieżkazestawu*|Nazwa pliku, który zawiera manifest zestawu.|  
|*Pliklistyzestawów*|Ścieżka do pliku tekstowego ANSI, który zawiera listę zestawów do zainstalowania lub odinstalowania. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. Narzędzie interpretuje ścieżki względne względem lokalizacji pliku *Pliklistyzestawów*. Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. Zobacz *Pliklistyzestawów* zawartości przykłady w dalszej części tego tematu.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/CDL**|Usuwa zawartość pamięci podręcznej pobierania.|  
|**/f**|Wybierz tę opcję z **/i** lub **/il** opcji, aby wymusić ponowną instalację zestawu. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.|  
|**/ h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/i** *Ścieżkazestawu*|Instaluje zestaw w globalnej pamięci podręcznej zestawów.|  
|**/IF***Ścieżkazestawu*|Instaluje zestaw w globalnej pamięci podręcznej zestawów. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.<br /><br /> Użycie tej opcji jest równoznaczne z użyciem **/i** i **/f** opcje razem.|  
|**/il** *Pliklistyzestawów*|Instaluje jeden lub więcej zestawów, do których określony w *Pliklistyzestawów* w globalnej pamięci podręcznej.|  
|**/IR***Ścieżkazestawu*<br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Instaluje zestaw w globalnej pamięci podręcznej zestawów i dodaje odwołanie, aby zliczyć zestaw. Należy określić *Ścieżkazestawu*, *schemat*, *identyfikator*, i *opis* parametrów przy użyciu tej opcji. Aby uzyskać opis prawidłowe wartości dla tych parametrów można określić, zobacz **/r** opcji.<br /><br /> Użycie tej opcji jest równoznaczne z użyciem **/i** i **/r** opcje razem.|  
|**/l** [*assemblyName*]|Wyświetla zawartość globalnej pamięci podręcznej zestawów. Jeśli określisz *assemblyName* parametru, narzędzie wyświetli tylko zestawy pasujące do danej nazwy.|  
|**/Ldl**|Wyświetla zawartość pamięci podręcznej pobranych plików.|  
|**/LR** [*assemblyName*]|Wyświetla listę wszystkich zestawów i liczbę odwołań do nich. Jeśli określisz *assemblyName* parametr, narzędzie wyświetli tylko zestawy pasujące do nazwy i ich odpowiadające im liczby odwołań.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/r** [*assemblyName &#124; Ścieżkazestawu*]<br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Określa śledzone odwołanie do zestawu lub zestawów, które mają zostać zainstalowane lub odinstalowane. Wybierz tę opcję z **/i**, **/il**, **/u**, lub **/ul** opcje.<br /><br /> Aby zainstalować zestaw, należy określić *Ścieżkazestawu*, *schemat*, *identyfikator*, i *opis* parametrów przy użyciu tej opcji. Aby odinstalować zestaw, należy określić *assemblyName*, *schemat*, *identyfikator*, i *opis* parametrów.<br /><br /> Aby usunąć odwołanie do zestawu, należy określić ten sam *schemat*, *identyfikator*, i *opis* parametry, które zostały określone z **/i** i **/r** (lub **/ir**) po zainstalowaniu zestawu opcji. W trakcie odinstalowywania zestawu narzędzie usuwa zestaw również z globalnej pamięci podręcznej zestawów, jeśli jest to ostatnie odwołanie do usunięcia i jeśli Instalator Windows nie ma innych odwołań do zestawu.<br /><br /> *Schemat* parametr określa typ schematu instalacji. Można określić jedną z następujących wartości:<br /><br /> -UNINSTALL_KEY: Należy określić tę wartość, jeśli Instalator dodaje aplikację do apletu Dodaj/Usuń programy w programie Microsoft Windows. Aplikacje dodają same siebie do apletu Dodaj/Usuń programy przez dodanie klucza rejestru do gałęzi HKLM\Software\Microsoft\Windows\CurrentVersion.<br />— ŚCIEŻKA PLIKU: Należy określić tę wartość, jeśli Instalator nie dodaje aplikację do apletu Dodaj/Usuń programy.<br />-NIEPRZEZROCZYSTE: Jeśli dostarczenie klucza rejestru należy określić tę wartość lub ścieżka pliku nie ma zastosowania do tego scenariusza instalacji. Ta wartość służy do określania niestandardowych informacji dla *identyfikator* parametru.<br /><br /> Wartość do określenia dla *identyfikator* zależy od wartości określonej dla parametru *schemat* parametru:<br /><br /> — W przypadku określenia UNINSTALL_KEY dla *schemat* parametru, określ nazwę aplikacji ustawioną w kluczu rejestru HKLM\Software\Microsoft\Windows\CurrentVersion. Na przykład, jeśli klucz rejestru to hklm\software\microsoft\windows\currentversion\mojaaplikacja, należy określić wartość MojaAplikacja dla *identyfikator* parametru.<br />— Jeśli określono wartość FILEPATH dla *schemat* parametrów, wprowadź pełną ścieżkę do pliku wykonywalnego, który instaluje zestaw jako *identyfikator* parametru.<br />— Jeśli określono wartość OPAQUE dla *schemat* parametru, można podać dowolny element danych jako *identyfikator* parametru. Podane dane muszą być ujęte w znaki cudzysłowu ("").<br /><br /> *Opis* parametr umożliwia podanie tekstu opisującego aplikację do zainstalowania. Te informacje są wyświetlane podczas wyliczania odwołań.|  
|**/silent**|Pomija wyświetlanie wszystkich danych wyjściowych.|  
|**/u***assemblyName*|Odinstalowuje zestaw z globalnej pamięci podręcznej zestawów.|  
|**/Uf***assemblyName*|Wymusza odinstalowanie określonego zestawu przez usunięcie wszystkich odwołań do tego zestawu.<br /><br /> Użycie tej opcji jest równoznaczne z użyciem **/u** i **/f** opcje razem. **Uwaga:**  Nie można używać tej opcji, aby usunąć zestaw, który został zainstalowany przy użyciu Instalatora Microsoft Windows. Przy próbie wykonania tej operacji narzędzie wyświetli komunikat o błędzie.|  
|**/ul** *Pliklistyzestawów*|Odinstalowuje co najmniej jeden zestaw określony w *Pliklistyzestawów* z globalnej pamięci podręcznej.|  
|**/u**[**ngen**] *assemblyName*|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów. Jeśli istnieją odwołania do określonego zestawu, narzędzie wyświetla liczbę odwołań i nie usuwa zestawu z globalnej pamięci podręcznej zestawów. **Uwaga:**  W .NET Framework w wersji 2.0 `/ungen` nie jest obsługiwane. Zamiast tego należy użyć `uninstall` polecenia [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> W .NET Framework w wersji 1.0 i 1.1 określając **/ ungen** powoduje, że Gacutil.exe usuwa zestaw z pamięci podręcznej obrazów natywnych. Ta pamięć podręczna są przechowywane obrazy natywne dla zestawów, które zostały utworzone przy użyciu [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/UR***assemblyName*<br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Odinstalowuje odwołanie do określonego zestawu z globalnej pamięci podręcznej zestawów. Aby usunąć odwołanie do zestawu, należy określić ten sam *schemat*, *identyfikator*, i *opis* parametry, które zostały określone z **/i** i **/r** (lub **/ir)** opcji podczas instalowania zestawu. Aby uzyskać opis prawidłowe wartości dla tych parametrów można określić, zobacz **/r** opcji.<br /><br /> Użycie tej opcji jest równoznaczne z użyciem **/u** i **/r** opcje razem.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć programu Gacutil.exe, trzeba mieć uprawnienia administratora.  
  
 W szczególności program Gacutil.exe umożliwia instalowanie zestawów w pamięci podręcznej, usuwanie ich z pamięci podręcznej oraz wyświetlanie zawartości pamięci podręcznej.  
  
 Program Gacutil.exe oferuje opcje, które obsługują zliczanie odwołań podobne do schematu zliczania odwołań obsługiwanego przez Instalatora Windows. Programu Gacutil.exe można użyć do zainstalowania dwóch aplikacji, które instalują ten sam zestaw; narzędzie przechowuje informacje o liczbie odwołań do zestawu. W rezultacie zestaw pozostanie na komputerze do czasu, aż obie aplikacje zostaną odinstalowane. Jeśli program Gacutil.exe jest używany do instalacji rzeczywistych produktów, należy używać opcji obsługujących zliczanie odwołań. Użyj **/i** i **/r** opcje celu zainstalowanie zestawu i dodanie odwołania do zliczenia. Użyj **/u** i **/r** opcje umożliwia usunięcie liczby odwołań do zestawu. Należy pamiętać, że używanie **/i** i **/u** samych opcji nie obsługują zliczanie odwołań. Te opcje są odpowiednie do użycia podczas tworzenia produktu, ale nie podczas instalacji rzeczywistego produktu.  
  
 Użyj **/il** lub **/ul** opcji, aby zainstalować lub odinstalowanie listy zestawów przechowywanej w pliku tekstowym ANSI. Zawartość pliku tekstowego musi być poprawnie sformatowana. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do zainstalowania.  
  
```  
myAssembly1.dll  
myAssembly2.dll  
myAssembly3.dll  
```  
  
 Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do odinstalowania.  
  
```  
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
```  

> [!NOTE]
>  Próba zainstalowania zestawu przy użyciu nazwy pliku przekracza od 79 i 91 znaków (bez rozszerzenia pliku) może spowodować następujący błąd:
> ```
> Failure adding assembly to the cache:   The file name is too long.
> ```
> Jest to, ponieważ wewnętrznie Gacutil.exe tworzy ścieżki z maksymalnie MAX_PATH znaków, który składa się z następujących elementów:
> - GAC Root - 34 znaków (tj. `C:\Windows\Microsoft.NET\assembly\`)
> - Architektura — 7 i 9 znaków (tj. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName — maksymalnie 91 znaki, w zależności od rozmiaru inne elementy (np.) `System.Xml.Linq\`)
> - AssemblyInfo - 31 do 48 znaków lub więcej składający się z:
>   - Framework - 5 znaków (np.) `v4.0_`)
>   - AssemblyVersion - 8-24 znaki (np.) `9.0.1000.0_`)
>   - AssemblyLanguage - 1 do 8 znaków (np.) `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 znaki (np.) `31bf3856ad364e35\`)
> - DllFileName — maksymalnie 91 + 4 znaki (tj. `<AssemblyName>.dll`)

## <a name="examples"></a>Przykłady  
 Poniższe polecenie instaluje zestaw `mydll.dll` w globalnej pamięci podręcznej.  
  
```  
gacutil /i mydll.dll  
```  
  
 Następujące polecenie usuwa zestaw `hello` z globalnej pamięci podręcznej tak długo, jak liczby odwołań istnieje dla zestawu.  
  
```  
gacutil /u hello  
```  
  
 Należy zauważyć, że poprzednie polecenie może usunąć więcej niż jeden zestaw z globalnej pamięci podręcznej zestawów, ponieważ nazwa zestawu nie została w pełni określona. Na przykład, jeśli obie wersje 1.0.0.0 i 3.2.2.1 zestawu `hello` są zainstalowane w pamięci podręcznej, polecenie `gacutil /u hello` usunie oba zestawy.  
  
 Aby zapobiec usuwaniu więcej niż jednego zestawu, należy użyć składni z poniższego przykładu. To polecenie usuwa tylko `hello` zestawu, który pasuje do w pełni określonego numeru wersji, kultury i klucza publicznego.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Poniższe polecenie instaluje zestawy określone w pliku `assemblyList.txt` w globalnej pamięci podręcznej.  
  
 `gacutil /il assemblyList.txt`  
  
 Poniższe polecenie usuwa zestawy określone w pliku `assemblyList.txt` z globalnej pamięci podręcznej.  
  
 `gacutil /ul assemblyList.txt`  
  
 Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołania do zliczenia. Zestaw `myDll.dll` jest używany przez aplikację `MyApp`. `UNINSTALL_KEY MyApp` Parametr określa klucz rejestru, który dodaje `MyApp` do apletu Dodaj/Usuń programy w Windows. Parametr opisu jest określony jako `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołania do zliczenia. Parametr "schemat" `FILEPATH`oraz parametru id `c:\applications\myApp\myApp.exe`, określ ścieżkę do aplikacji, który jest instalowany `myDll.dll.` parametr opisu jest określony jako `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Poniższe polecenie instaluje `myDll.dll` w globalnej pamięci podręcznej zestawów i dodaje odwołania do zliczenia. Parametr schematu `OPAQUE`, umożliwia dostosowanie parametrów identyfikator i opis.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Poniższe polecenie usuwa odwołanie do `myDll.dll` przez aplikację `myApp`. Jeśli jest to ostatnie odwołanie do tego zestawu, spowoduje to również usunięcie zestawu z globalnej pamięci podręcznej zestawów.  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Poniższe polecenie wyświetla zawartość globalnej pamięci podręcznej zestawów.  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Global Assembly Cache](../../../docs/framework/app-domains/gac.md)  
 [Regasm.exe (narzędzie rejestracji zestawów)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
