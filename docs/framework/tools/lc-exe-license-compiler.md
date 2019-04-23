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
ms.openlocfilehash: 6c4432d94372ce10ee9ecdf6e441eda3318a20d7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298971"
---
# <a name="lcexe-license-compiler"></a>Lc.exe (Kompilator licencji)
Kompilator licencji czyta pliki tekstowe zawierające informacje o licencjonowaniu i tworzy plik binarny, który może zostać osadzony jako zasób w pliku wykonywalnym środowiska uruchomieniowego języka wspólnego.  
  
 Plik tekstowy licx jest automatycznie generowany lub aktualizowany przez Projektanta programu Windows Forms zawsze, gdy licencjonowany formant jest dodawany do formularza. W ramach kompilacji system projektu przekształci plik tekstowy licx w zasób binarny licenses, który dostarcza obsługę licencjonowania formantów platformy .NET. Następnie ten zasób binarny zostanie osadzony w danych wyjściowych projektu.  
  
 Krzyżowa kompilacja wersji 32-bitowych i 64-bitowych jest nieobsługiwana, gdy podczas kompilowania projektu jest używany Kompilator licencji. Jest to spowodowane tym, że Kompilator licencji musi ładować zestawy, a ładowanie 64-bitowych zestawów z aplikacji 32-bitowej (i odwrotnie) jest niedozwolone. W takim przypadku należy użyć Kompilatora licencji z wiersza polecenia, aby skompilować licencję ręcznie i określić odpowiednią architekturę.  
  
 To narzędzie jest instalowane automatycznie z programem Visual Studio. Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/complist:** *nazwy pliku*|Określa nazwę pliku zawierającego listę licencjonowanych składników, która ma zostać umieszczona w pliku licenses. W odwołaniu do każdego składnika musi być używana jego pełna nazwa, a w wierszu może znajdować się tylko jeden składnik.<br /><br /> Użytkownicy wiersza polecenia mogą określić osobny plik dla każdego formularza w projekcie. Program LC.exe akceptuje wiele plików wejściowych i tworzy jeden plik licenses.|  
|**/ h**[**elp**]|Wyświetla składnię polecenia i opcje narzędzia.|  
|**i:** *modułu*|Określa moduły, które zawierają składniki wymienione w **/complist** pliku. Aby określić więcej niż jeden moduł, używanych jest wiele **/i** flag.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**do pliku klucza:** *ścieżki*|Określa katalog, w którym ma zostać umieszczony wyjściowy plik licenses.|  
|**/ target:** *targetPE*|Określa plik wykonywalny, dla którego jest generowany plik licenses.|  
|**/v**|Określa tryb pełny; wyświetla informacje o postępie kompilacji.|  
|**@** *Plik*|Określa plik odpowiedzi (rsp).|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="example"></a>Przykład  
  
1. Jeśli używasz licencjonowany formant `MyCompany.Samples.LicControl1` zawarte w `Samples.DLL` w aplikacji o nazwie `HostApp.exe` *,* można utworzyć `HostAppLic.txt` zawiera następujące czynności.  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2. Utwórz plik licenses o nazwie `HostApp.exe.licenses` przy użyciu następującego polecenia.  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3. Tworzenie `HostApp.exe` dołączając plik licenses jako zasób. W przypadku kompilowania aplikacji w języku C# należy użyć następującego polecenia, aby skompilować aplikację.  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 Następujące polecenie kompiluje `myApp.licenses` z list licencjonowanych składników `hostapplic.txt`, `hostapplic2.txt` i `hostapplic3.txt`. `modulesList` Argument określa moduły zawierające licencjonowane składniki.  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>Przykład pliku odpowiedzi  
 Poniżej przedstawiono przykładowy plik odpowiedzi, `response.rsp`. Aby uzyskać więcej informacji na temat plików odpowiedzi, zobacz [pliki odpowiedzi](/visualstudio/msbuild/msbuild-response-files).  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 Następujące zastosowania wiersza polecenia `response.rsp` pliku.  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](../../../docs/framework/tools/index.md)
- [Al.exe (konsolidator zestawów)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
