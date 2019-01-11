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
ms.openlocfilehash: df81293a00ad79892618c71a901cea30efe766ec
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221313"
---
# <a name="regsvcsexe-net-services-installation-tool"></a>Regsvcs.exe (Narzędzie instalacji usług .NET)
Narzędzie instalacji usług platformy .NET wykonuje następujące akcje:  
  
-   Ładuje i rejestruje zestawy.  
  
-   Generuje, rejestruje i instaluje biblioteki typów w określonej aplikacji COM+.  
  
-   Konfiguruje usługi, które zostały programowo dodane do klasy użytkownika.  
  
 Aby uruchomić narzędzie, należy użyć wiersz polecenia programisty dla programu Visual Studio (lub wiersza polecenia programu Visual Studio Windows 7). Aby uzyskać więcej informacji, zobacz [wiersz polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
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
|*assemblyFile.dll*|Plik zestawu źródłowego. Zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).|  
  
|Opcja|Opis|  
|------------|-----------------|  
|**/appdir:** *ścieżki*|Określa katalog główny aplikacji.|  
|**operacji:** *applicationName*|Określa nazwę aplikacji COM+, która ma zostać znaleziona lub utworzona.|  
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
|**/ TLB:** *plik_biblioteki_typów*|Określa plik biblioteki typów do zainstalowania.|  
|**/u**|Odinstalowuje aplikację docelową.|  
|**/quiet**|Określa tryb cichy; pomija wyświetlanie logo i komunikatów o sukcesie.|  
|**/?**|Wyświetla składnię polecenia i opcje narzędzia.|  
  
## <a name="remarks"></a>Uwagi  
 Regsvcs.exe wymaga pliku zestawu źródłowego określonego przez *Plikzestawu.dll*. Ten zestaw musi być podpisany za pomocą silnej nazwy. Aby uzyskać więcej informacji na temat podpisywania silnymi nazwami, zobacz [podpisywanie zestawu za pomocą silnej nazwy](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md). Nazwy aplikacji docelowej i pliku biblioteki typów są opcjonalne. *ApplicationName* argument może zostać wygenerowany na podstawie pliku zestawu źródłowego i zostanie utworzona przez Regsvcs.exe, jeśli jeszcze nie istnieje. *Plik_biblioteki_typów* argument może określać nazwę biblioteki typów. Jeśli nie zostanie określona nazwa biblioteki typów, program Regsvcs.exe użyje nazwy zestawu jako wartości domyślnej.  
  
 Gdy Regsvcs.exe rejestruje metody składnika, jest podlegają [zapotrzebowanie](https://msdn.microsoft.com/library/e5283e28-2366-4519-b27d-ef5c1ddc1f48) i [link zapotrzebowanie](../../../docs/framework/misc/link-demands.md) w tych metodach. To narzędzie działa we w pełni zaufanym środowisku, więc większość żądań uprawnienia kończy się pomyślnie. Jednak Regsvcs.exe nie może rejestrować składników z metodami chronionymi przez żądania demand lub linkdemand dla <xref:System.Security.Permissions.StrongNameIdentityPermission> lub <xref:System.Security.Permissions.PublisherIdentityPermission>.  
  
 Aby używać programu Regsvcs.exe, trzeba mieć uprawnienia administracyjne na komputerze lokalnym.  
  
 Jeśli podczas wykonywania dowolnej z tych akcji w programie Regsvcs.exe wystąpi błąd, zostaną wyświetlone odpowiednie komunikaty o błędach.  
  
## <a name="examples"></a>Przykłady  
 Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM +) i tworzy `myTest.tlb` biblioteki typów.  
  
```  
regsvcs /appname:myTargetApp myTest.dll  
```  
  
 Następujące polecenie dodaje wszystkie klasy publiczne zawarte w `myTest.dll` do `myTargetApp` (istniejąca aplikacja COM +) i tworzy `newTest.tlb` biblioteki typów.  
  
```  
regsvcs /appname:myTargetApp /tlb:newTest.tlb myTest.dll  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Instrukcje: Podpisywanie zestawu silną nazwą](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
