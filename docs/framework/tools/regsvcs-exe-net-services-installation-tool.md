---
title: Regsvcs.exe (Narzędzie instalacji usług .NET)
ms.date: 03/30/2017
helpviewer_keywords:
- Regsvcs.exe
- .NET Services Installation tool
- loading assemblies
- assemblies [.NET Framework], registering
- type libraries
- registering assemblies
ms.assetid: 5220fe58-5aaf-4e8e-8bc3-b78c63025804
ms.openlocfilehash: 1af93ae89d027bccdd52b9cd9c49f8e620303677
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104939"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (Narzędzie instalacji usług .NET)
Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:  
  
- Ładuje i rejestruje zestawy.  
  
- Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.  
  
- Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.  
  
 Aby uruchomić narzędzie, użyj wiersz polecenia dla deweloperów dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersza polecenia](developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyFile. dll*|Plik zestawu źródłowego. Zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md).|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/Appdir:** *ścieżka*|Określa katalog główny aplikacji.|  
|**/APPNAME:** *ApplicationName*|Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/c**|Tworzy aplikację docelową.|  
|**/componly**|Konfiguruje tylko składniki; ignoruje metody i interfejsy.|  
|**/exapp**|Określa, że narzędzie ma oczekiwać istniejącej aplikacji.|  
|**/extlb**|Używa istniejącej biblioteki typów.|  
|**/FC**|Znajduje lub tworzy aplikację docelową.|  
|**/Help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/noreconfig**|Nie konfiguruje ponownie istniejącej aplikacji docelowej.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/parName:** *Nazwa*|Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/reconfig**|Konfiguruje ponownie istniejącą aplikację docelową. Domyślnie włączone.|  
|**/tlb:** *TypeLibraryFile*|Określa plik biblioteki typów do zainstalowania.|  
|**Określ**|Odinstalowuje aplikację docelową.|  
|**/quiet**|Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Regsvcs. exe wymaga pliku zestawu źródłowego określonego przez *assemblyFile. dll*. Ten zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji na temat podpisywania silnej nazwy, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../standard/assembly/sign-strong-name.md). Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne. Argument *ApplicationName* można wygenerować z pliku zestawu źródłowego i zostanie utworzony przez Regsvcs. exe, jeśli jeszcze nie istnieje. Argument *TypeLibraryFile* może określać nazwę biblioteki typów. Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.  
  
 Gdy Regsvcs. exe rejestruje metody składnika, podlega [zapotrzebowaniu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) i [łącznym potrzebom](../misc/link-demands.md) dotyczącym tych metod. To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie. Jednak Regsvcs. exe nie może zarejestrować składników przy użyciu metod chronionych przez zapotrzebowanie lub żądanie linku dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.  
  
 Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM+) i tworzy `myTest.tlb` biblioteki typów.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM+) i tworzy `newTest.tlb` biblioteki typów.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Instrukcje: podpisywanie zestawu silną nazwą](../../standard/assembly/sign-strong-name.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
