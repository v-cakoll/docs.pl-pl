---
title: "Łączenie statycznych funkcji globalnych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 126edd5f25b56a069a87cd1bd50cce955334a342
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="fusion-global-static-functions"></a>Łączenie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane statyczne funkcje globalne, używane fusion interfejsu API.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ClearDownloadCache, funkcja](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 Powoduje wyczyszczenie pamięci podręcznej GAC pobrany zestawów.  
  
 [CompareAssemblyIdentity, funkcja](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 Porównuje dwa tożsamości zestawu do ustalenia, czy są równoważne.  
  
 [CreateApplicationContext, funkcja](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 Tylko wewnętrznie. (Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [CreateAssemblyCache, funkcja](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 Pobiera wskaźnik do nowego [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) wystąpienie reprezentującego globalnej pamięci podręcznej zestawów.  
  
 [CreateAssemblyEnum, funkcja](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 Pobiera wskaźnik do [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) wystąpienia, który reprezentuje listę obiektów, które istnieją w określonym zestawie.  
  
 [CreateAssemblyNameObject, funkcja](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 Pobiera wskaźnik do [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) wystąpienia, który reprezentuje unikatową tożsamość zestawu o określonej nazwie.  
  
 [CreateHistoryReader, funkcja](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 Tworzy czytnik historii dla określonego pliku.  
  
 [CreateInstallReferenceEnum, funkcja](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 Pobiera wskaźnik do [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) wystąpienia, który reprezentuje listę odwołań aplikacji do określonego zestawu.  
  
 [GetAppIdAuthority, funkcja](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 Pobiera wskaźnik do [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) wystąpienia zarządzanego kluczy dla tożsamości aplikacji i odwołań.  
  
 [GetAssemblyIdentityFromFile, funkcja](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie przy użyciu określonej ścieżki.  
  
 [GetCachePath, funkcja](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 Pobiera ścieżkę do zestawu pamięci podręcznej, przy użyciu określonych flag.  
  
 [GetHistoryFileDirectory, funkcja](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 Pobiera ścieżkę katalogu historii aplikacji.  
  
 [GetIdentityAuthority, funkcja](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 Pobiera wskaźnik do [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) wystąpienia zarządzanego klucze obiekty kod.  
  
 [IsFrameworkAssembly, funkcja](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 Pobiera wartość wskazującą, czy jest zarządzana w określonym zestawie.  
  
 [NukeDownloadedCache, funkcja](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 Usuwa pamięć podręczną wspólnego języka środowiska uruchomieniowego pobierania.  
  
 [PreBindAssemblyEx, funkcja](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [Wyliczenia łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Łączenie — struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
