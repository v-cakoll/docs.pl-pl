---
title: "Gacutil.exe (Narzędzie Global Assembly Cache)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f802abf6ed90a60b057b01589dcf32c2aa495676
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (Narzędzie Global Assembly Cache)
Narzędzie globalnej pamięci podręcznej zestawów umożliwia wyświetlenie zawartości globalnej pamięci podręcznej zestawów i wykonywanie na niej operacji oraz pobieranie pamięci podręcznej.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyName*|Nazwa zestawu Możesz podać nazwę częściowo określonego zestawu takich jak `myAssembly` lub Pełna nazwa zestawu takich jak `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*zestawu assemblyPath*|Nazwa pliku, który zawiera manifest zestawu.|  
|*assemblyListFile*|Ścieżka do pliku tekstowego ANSI, który zawiera listę zestawów do zainstalowania lub odinstalowania. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. Narzędzie interpretuje ścieżek względnych względną wobec lokalizacji *assemblyListFile*. Aby użyć pliku tekstowego do odinstalowania zestawów, należy określić w pełni kwalifikowaną nazwę każdego zestawu w oddzielnym wierszu w pliku. Zobacz *assemblyListFile* zawartości przykłady w dalszej części tego tematu.|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/CDL**|Usuwa zawartość pamięci podręcznej pobierania.|  
|**/f**|Wybierz tę opcję z **/i** lub **/il** opcji, aby wymusić ponowne zainstalowanie zestawu. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/i** *zestawu assemblyPath*|Instaluje zestaw w globalnej pamięci podręcznej zestawów.|  
|**/IF***zestawu assemblyPath* |Instaluje zestaw w globalnej pamięci podręcznej zestawów. Jeśli zestaw o tej samej nazwie już istnieje w globalnej pamięci podręcznej zestawów, narzędzie zastępuje go.<br /><br /> Zaznaczenie tej opcji jest odpowiednikiem określenie **/i** i **/f** opcje razem.|  
|**/il** *assemblyListFile*|Instaluje jeden lub więcej zestawów, do których określony w *assemblyListFile* w globalnej pamięci podręcznej zestawów.|  
|**/IR***zestawu assemblyPath* <br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Instaluje zestaw w globalnej pamięci podręcznej zestawów i dodaje odwołanie, aby zliczyć zestaw. Należy określić *zestawu assemblyPath*, *schemat*, *identyfikator*, i *opis* parametrów przy użyciu tej opcji. Opis prawidłowych wartości dla tych parametrów można określić, zobacz **/r** opcji.<br /><br /> Zaznaczenie tej opcji jest odpowiednikiem określenie **/i** i **/r** opcje razem.|  
|**/l** [*assemblyName*]|Wyświetla zawartość globalnej pamięci podręcznej zestawów. Jeśli określisz *assemblyName* parametru, narzędzie wyświetla tylko zestawy pasujących do tej nazwy.|  
|**/Ldl**|Wyświetla zawartość pamięci podręcznej pobranych plików.|  
|**/LR** [*assemblyName*]|Wyświetla listę wszystkich zestawów i liczbę odwołań do nich. Jeśli określisz *assemblyName* parametru liczby ich odpowiednich odwołania i narzędzie wyświetla tylko zestawy pasujących do tej nazwy.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/r** [*assemblyName &#124; zestawu assemblyPath*]<br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Określa śledzone odwołanie do zestawu lub zestawów, które mają zostać zainstalowane lub odinstalowane. Wybierz tę opcję z **/i**, **/il**, **/u**, lub **/ul** opcje.<br /><br /> Aby zainstalować zestaw, określ *zestawu assemblyPath*, *schemat*, *identyfikator*, i *opis* parametrów przy użyciu tej opcji. Aby odinstalować zestawu, określ *assemblyName*, *schemat*, *identyfikator*, i *opis* parametrów.<br /><br /> Aby usunąć odwołania do zestawu, należy określić ten sam *schemat*, *identyfikator*, i *opis* parametrów, które zostały określone z **/i** i **/r** (lub **/ir**) opcji podczas instalowania zestawu. W trakcie odinstalowywania zestawu narzędzie usuwa zestaw również z globalnej pamięci podręcznej zestawów, jeśli jest to ostatnie odwołanie do usunięcia i jeśli Instalator Windows nie ma innych odwołań do zestawu.<br /><br /> *Schemat* parametr określa typ schematu instalacji. Można określić jedną z następujących wartości:<br /><br /> -UNINSTALL_KEY: Podać tę wartość, jeśli Instalator dodaje aplikację do apletu Dodaj/Usuń programy w systemie Microsoft Windows. Aplikacje dodają same siebie do apletu Dodaj/Usuń programy przez dodanie klucza rejestru do gałęzi HKLM\Software\Microsoft\Windows\CurrentVersion.<br />-FILEPATH: Podać tę wartość, jeśli Instalator nie dodaje aplikację do apletu Dodaj/Usuń programy.<br />-NIEPRZEZROCZYSTE: Podać tę wartość, jeśli dostarczenie klucza rejestru lub ścieżka pliku nie ma zastosowania do danego scenariusza instalacji. Ta wartość służy do określenia niestandardowych informacji do *identyfikator* parametru.<br /><br /> Wartość, aby określić dla *identyfikator* zależy od wartości określonej dla parametru *schemat* parametru:<br /><br /> — Jeśli określisz UNINSTALL_KEY dla *schemat* parametru, określ nazwę aplikacji, ustaw w kluczu rejestru HKLM\Software\Microsoft\Windows\CurrentVersion. Na przykład, jeśli klucz rejestru jest HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, określ moja_aplikacja dla *identyfikator* parametru.<br />— Jeśli określisz ŚCIEŻKA *schemat* parametru, określ pełną ścieżkę do pliku wykonywalnego, który instaluje zestaw jako *identyfikator* parametru.<br />— Jeśli określisz NIEPRZEZROCZYSTE dla *schemat* parametru, możesz podać dowolne dane jako *identyfikator* parametru. Podane dane muszą być ujęte w znaki cudzysłowu ("").<br /><br /> *Opis* parametr umożliwia określenie tekst opisujący aplikację do zainstalowania. Te informacje są wyświetlane podczas wyliczania odwołań.|  
|**/silent**|Pomija wyświetlanie wszystkich danych wyjściowych.|  
|**/u***assemblyName* |Odinstalowuje zestaw z globalnej pamięci podręcznej zestawów.|  
|**/Uf***assemblyName* |Wymusza odinstalowanie określonego zestawu przez usunięcie wszystkich odwołań do tego zestawu.<br /><br /> Zaznaczenie tej opcji jest odpowiednikiem określenie **/u** i **/f** opcje razem. **Uwaga:** nie można użyć tej opcji do usunięcia zestawu, który został zainstalowany przy użyciu Instalatora systemu Microsoft Windows. Przy próbie wykonania tej operacji narzędzie wyświetli komunikat o błędzie.|  
|**/ul** *assemblyListFile*|Odinstalowuje jeden lub więcej zestawów, do których określony w *assemblyListFile* z globalnej pamięci podręcznej zestawów.|  
|**/u**[**ngen**] *assemblyName*|Odinstalowuje określony zestaw z globalnej pamięci podręcznej zestawów. Jeśli istnieją odwołania do określonego zestawu, narzędzie wyświetla liczbę odwołań i nie usuwa zestawu z globalnej pamięci podręcznej zestawów. **Uwaga:** w programie .NET Framework w wersji 2.0, `/ungen` nie jest obsługiwane. Zamiast tego należy użyć `uninstall` polecenie z [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> W wersji systemu .NET Framework 1.0 i 1.1 określając **/ ungen** powoduje, że Gacutil.exe usunięcie zestawu z pamięci podręcznej obrazów natywnych. Ta pamięć podręczna przechowuje zestawy, które zostały utworzone przy użyciu obrazów macierzystych [Ngen.exe (Generator obrazu natywnego)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/UR***assemblyName* <br /><br /> *Schemat*<br /><br /> *id*<br /><br /> *Opis elementu*|Odinstalowuje odwołanie do określonego zestawu z globalnej pamięci podręcznej zestawów. Aby usunąć odwołania do zestawu, należy określić ten sam *schemat*, *identyfikator*, i *opis* parametrów, które zostały określone z **/i** i **/r** (lub **/ir)** opcji podczas instalowania zestawu. Opis prawidłowych wartości dla tych parametrów można określić, zobacz **/r** opcji.<br /><br /> Zaznaczenie tej opcji jest odpowiednikiem określenie **/u** i **/r** opcje razem.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Aby użyć programu Gacutil.exe, trzeba mieć uprawnienia administratora.  
  
 W szczególności program Gacutil.exe umożliwia instalowanie zestawów w pamięci podręcznej, usuwanie ich z pamięci podręcznej oraz wyświetlanie zawartości pamięci podręcznej.  
  
 Program Gacutil.exe oferuje opcje, które obsługują zliczanie odwołań podobne do schematu zliczania odwołań obsługiwanego przez Instalatora Windows. Programu Gacutil.exe można użyć do zainstalowania dwóch aplikacji, które instalują ten sam zestaw; narzędzie przechowuje informacje o liczbie odwołań do zestawu. W rezultacie zestaw pozostanie na komputerze do czasu, aż obie aplikacje zostaną odinstalowane. Jeśli program Gacutil.exe jest używany do instalacji rzeczywistych produktów, należy używać opcji obsługujących zliczanie odwołań. Użyj **/i** i **/r** opcje ze sobą w celu zainstalowania zestawu i Dodaj odwołanie do liczby go. Użyj **/u** i **/r** opcje ze sobą w celu usuwania liczba odwołań do zestawu. Należy pamiętać, że korzystanie **/i** i **/u** tylko opcje nie obsługuje liczenie odwołań. Te opcje są odpowiednie do użycia podczas tworzenia produktu, ale nie podczas instalacji rzeczywistego produktu.  
  
 Użyj **/il** lub **/ul** opcji, aby zainstalować lub odinstalować listę zestawów przechowywane w pliku tekstowym ANSI. Zawartość pliku tekstowego musi być poprawnie sformatowana. Aby użyć pliku tekstowego do instalowania zestawów, należy określić ścieżkę do każdego zestawu w oddzielnym wierszu w pliku. W poniższym przykładzie pokazano zawartość pliku zawierającego zestawy do zainstalowania.  
  
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
  
## <a name="examples"></a>Przykłady  
 Poniższe polecenie powoduje zainstalowanie zestawu `mydll.dll` w globalnej pamięci podręcznej zestawów.  
  
```  
gacutil /i mydll.dll  
```  
  
 Następujące polecenie spowoduje usunięcie zestawu `hello` z zestawu globalnej pamięci podręcznej tak długo, jak liczby żadne odwołanie istnieje dla zestawu.  
  
```  
gacutil /u hello  
```  
  
 Należy zauważyć, że poprzednie polecenie może usunąć więcej niż jeden zestaw z globalnej pamięci podręcznej zestawów, ponieważ nazwa zestawu nie została w pełni określona. Na przykład, jeśli obie wersję 1.0.0.0 i 3.2.2.1 z `hello` są zainstalowane w pamięci podręcznej, polecenie `gacutil /u hello` usuwa oba zestawy.  
  
 Aby zapobiec usuwaniu więcej niż jednego zestawu, należy użyć składni z poniższego przykładu. To polecenie usuwa tylko `hello` zestawu, który jest zgodny z pełni podany numer wersji, kultury i klucz publiczny.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Polecenie instaluje zestawy określony w pliku `assemblyList.txt` w globalnej pamięci podręcznej zestawów.  
  
 `gacutil /il assemblyList.txt`  
  
 Następujące polecenie usuwa zestawy określony w pliku `assemblyList.txt` z globalnej pamięci podręcznej zestawów.  
  
 `gacutil /ul assemblyList.txt`  
  
 Następujące polecenie spowoduje zainstalowanie `myDll.dll` do pamięci podręcznej GAC i dodaje odwołanie do liczby go. Zestaw `myDll.dll` jest używany przez aplikację `MyApp`. `UNINSTALL_KEY MyApp` Parametr określa klucz rejestru, który dodaje `MyApp` Dodaj lub usuń programy w systemie Windows. Parametr description jest określony jako `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Następujące polecenie spowoduje zainstalowanie `myDll.dll` do pamięci podręcznej GAC i dodaje odwołanie do liczby go. Parametru schematem `FILEPATH`, a parametr id `c:\applications\myApp\myApp.exe`, określ ścieżkę do aplikacji, który jest instalowany `myDll.dll.` parametr description jest określony jako `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Następujące polecenie spowoduje zainstalowanie `myDll.dll` do pamięci podręcznej GAC i dodaje odwołanie do liczby go. Parametr schematu `OPAQUE`, można go dostosować parametry identyfikator i opis.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Następujące polecenie usuwa odwołanie do `myDll.dll` przez aplikację `myApp`. Jeśli jest to ostatnie odwołanie do tego zestawu, spowoduje to również usunięcie zestawu z globalnej pamięci podręcznej zestawów.  
  
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
