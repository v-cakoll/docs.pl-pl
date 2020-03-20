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
ms.openlocfilehash: aecd2f6894558b45898c7f22dd333617d9e2e327
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180359"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (Narzędzie instalacji usług .NET)
Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:  
  
- Ładuje i rejestruje zestawy.  
  
- Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.  
  
- Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.  
  
 Aby uruchomić narzędzie, użyj wiersza polecenia dewelopera dla programu Visual Studio (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [Wiersze poleceń](developer-command-prompt-for-vs.md).  
  
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
|*assemblyFile.dll*|Plik zestawu źródłowego. Zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji, zobacz [Podpisywanie zestawu z silną nazwą](../../standard/assembly/sign-strong-name.md).|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/appdir:** *ścieżka*|Określa katalog główny aplikacji.|  
|**/appname:** *nazwa aplikacji*|Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/c**|Tworzy aplikację docelową.|  
|**/componly**|Konfiguruje tylko składniki; ignoruje metody i interfejsy.|  
|**/exapp**|Określa, że narzędzie ma oczekiwać istniejącej aplikacji.|  
|**/extlb**|Używa istniejącej biblioteki typów.|  
|**/fc**|Znajduje lub tworzy aplikację docelową.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/noreconfig**|Nie konfiguruje ponownie istniejącej aplikacji docelowej.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/parname:** *nazwa*|Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/reconfig**|Konfiguruje ponownie istniejącą aplikację docelową. Domyślnie włączone.|  
|**/tlb:** *plik maszynowy*|Określa plik biblioteki typów do zainstalowania.|  
|**/u**|Odinstalowuje aplikację docelową.|  
|**/cichy**|Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *plik assemblyFile.dll*. Ten zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji na temat podpisywania silnej nazwy, zobacz [Podpisywanie zestawu z silną nazwą](../../standard/assembly/sign-strong-name.md). Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne. Argument *applicationName* może być generowany z pliku zestawu źródłowego i zostanie utworzony przez regsvcs.exe, jeśli jeszcze nie istnieje. Argument *typelibraryfile* może określać nazwę biblioteki typów. Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.  
  
 Gdy Regsvcs.exe rejestruje metody składnika, podlega [wymaganiom](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/9kc0c6st(v=vs.100)) i [wymaganiom łącza](../misc/link-demands.md) w przypadku tych metod. To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie. Jednak regsvcs.exe nie może zarejestrować składników z metod chronionych przez żądanie lub żądanie łącza dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.  
  
 Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie dodaje wszystkie klasy `myTest.dll` publiczne `myTargetApp` zawarte w (istniejącej aplikacji `myTest.tlb` COM+) i tworzy bibliotekę typów.  
  
```console  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Następujące polecenie dodaje wszystkie klasy `myTest.dll` publiczne `myTargetApp` zawarte w (istniejącej aplikacji `newTest.tlb` COM+) i tworzy bibliotekę typów.  
  
```console  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Instrukcje: podpisywanie zestawu silną nazwą](../../standard/assembly/sign-strong-name.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
