---
title: Lc.exe (Kompilator licencji)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: 464514a241cc35fc821049ba0c29bec108d88253
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180397"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (Kompilator licencji)
Kompilator licencji czyta pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik binarny, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.  
  
 Plik tekstowy licx jest automatycznie generowany lub aktualizowany przez Projektanta programu Windows Forms zawsze, gdy licencjonowany formant jest dodawany do formularza. W ramach kompilacji system projektu przekształci plik tekstowy licx w zasób binarny licenses, który dostarcza obsługę licencjonowania formantów platformy .NET. Następnie ten zasób binarny zostanie osadzony w danych wyjściowych projektu.  
  
 Krzyżowa kompilacja wersji 32-bitowych i 64-bitowych jest nieobsługiwana, gdy podczas kompilowania projektu jest używany Kompilator licencji. Jest to spowodowane tym, że Kompilator licencji musi ładować zestawy, a ładowanie 64-bitowych zestawów z aplikacji 32-bitowej (i odwrotnie) jest niedozwolone. W takim przypadku należy użyć Kompilatora licencji z wiersza polecenia, aby skompilować licencję ręcznie i określić odpowiednią architekturę.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console
      lc /target:  
targetPE /complist:filename [-outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/complist:** *nazwa pliku*|Określa nazwę pliku zawierającego listę licencjonowanych składników, która ma zostać umieszczona w pliku licenses. W odwołaniu do każdego składnika musi być używana jego pełna nazwa, a w wierszu może znajdować się tylko jeden składnik.<br /><br /> Użytkownicy wiersza polecenia mogą określić osobny plik dla każdego formularza w projekcie. Program LC.exe akceptuje wiele plików wejściowych i tworzy jeden plik licenses.|  
|**/h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/i:** *moduł*|Określa moduły, które zawierają składniki wymienione w pliku **/complist.** Aby określić więcej niż jeden moduł, należy użyć wielu flag **/i.**|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/outdir:** *ścieżka*|Określa katalog, w którym ma zostać umieszczony wyjściowy plik licenses.|  
|**/target:** *targetPE*|Określa plik wykonywalny, dla którego jest generowany plik licenses.|  
|**/v**|Określa tryb pełny; wyświetla informacje o postępie kompilacji.|  
|**@***plik*|Określa plik odpowiedzi (rsp).|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="example"></a>Przykład  
  
1. Jeśli używasz licencjonowanego `MyCompany.Samples.LicControl1` formantu `Samples.DLL` zawartego `HostApp.exe`w aplikacji `HostAppLic.txt` o nazwie *,* można utworzyć, który zawiera następujące.  
  
    ```text
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Utwórz plik .licenses nazywany `HostApp.exe.licenses` następującym poleceniem.  
  
    ```console  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. Kompilacja `HostApp.exe` zawierająca plik .licenses jako zasób. W przypadku kompilowania aplikacji w języku C# należy użyć następującego polecenia, aby skompilować aplikację.  
  
    ```console
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Następujące `myApp.licenses` polecenie kompiluje się z list `hostapplic.txt`licencjonowanych składników określonych przez , `hostapplic2.txt` i `hostapplic3.txt`. Argument `modulesList` określa moduły, które zawierają składniki licencjonowane.  
  
```console  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Przykład pliku odpowiedzi  
 Na poniższej liście przedstawiono przykład `response.rsp`pliku odpowiedzi , . Aby uzyskać więcej informacji na temat plików odpowiedzi, zobacz [Pliki odpowiedzi](/visualstudio/msbuild/msbuild-response-files).  
  
```text  
/target:hostapp.exe  
/complist:hostapplic.txt
/i:WFCPrj.dll
/outdir:"C:\My Folder"  
```  
  
 Następujący wiersz polecenia używa `response.rsp` pliku.  
  
```console  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Al.exe (konsolidator zestawów)](al-exe-assembly-linker.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
