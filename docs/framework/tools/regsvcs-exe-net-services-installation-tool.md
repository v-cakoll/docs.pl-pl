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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a13912d006b522e86997fc7850befb996db4b7bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (Narzędzie instalacji usług .NET)
Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:  
  
-   Ładuje i rejestruje zestawy.  
  
-   Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.  
  
-   Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.  
  
 Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7). Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 W wierszu polecenia wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
      regsvcs [/c | /fc | /u] [/tlb:typeLibraryFile] [/extlb]  
[/reconfig] [/componly] [/appname:applicationName]  
[/nologo] [/quiet]assemblyFile.dll   
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Opis|  
|--------------|-----------------|  
|*assemblyFile.dll*|Plik zestawu źródłowego. Zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/appdir:** *ścieżki*|Określa katalog główny aplikacji.|  
|**elementów/appname:** *applicationName*|Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/c**|Tworzy aplikację docelową.|  
|**componly**|Konfiguruje tylko składniki; ignoruje metody i interfejsy.|  
|**/exapp**|Określa, że narzędzie ma oczekiwać istniejącej aplikacji.|  
|**/extlb**|Używa istniejącej biblioteki typów.|  
|**/fc**|Znajduje lub tworzy aplikację docelową.|  
|**/help**|Wyświetla składnię polecenia i opcje narzędzia.|  
|**/noreconfig**|Nie konfiguruje ponownie istniejącej aplikacji docelowej.|  
|**/nologo**|Pomija wyświetlanie transparentu startowego firmy Microsoft.|  
|**/parname:** *nazwy*|Określa nazwę lub identyfikator aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
|**/reconfig**|Konfiguruje ponownie istniejącą aplikację docelową. Domyślnie włączone.|  
|**/ TLB:** *typelibraryfile*|Określa plik biblioteki typów do zainstalowania.|  
|**/u**|Odinstalowuje aplikację docelową.|  
|**/quiet**|Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *assemblyFile.dll*. Ten zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji dotyczących podpisywanie silną nazwą, zobacz [podpisywanie zestawu o silnej nazwie](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md). Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne. *ApplicationName* argument mogą być generowane ze źródłowego pliku zestawu i zostanie utworzony przez Regsvcs.exe, jeśli jeszcze nie istnieje. *Typelibraryfile* argument można określić nazwy biblioteki typów. Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.  
  
 Regsvcs.exe rejestrujący metod składnika, jest warunkiem [wymagań](http://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) i [link zapotrzebowanie](../../../docs/framework/misc/link-demands.md) na jednej z tych metod. To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie. Jednak Regsvcs.exe nie można zarejestrować składników za pomocą metod chroniony przez żądanie lub linkdemand dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.  
  
 Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.  
  
## <a name="examples"></a>Przykłady  
 Polecenie dodaje wszystkie klasy publicznej zawarte w `myTest.dll` do `myTargetApp` (istniejącej aplikacji COM +) i tworzy `myTest.tlb` biblioteki typów.  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Polecenie dodaje wszystkie klasy publicznej zawarte w `myTest.dll` do `myTargetApp` (istniejącej aplikacji COM +) i tworzy `newTest.tlb` biblioteki typów.  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Instrukcje: podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
