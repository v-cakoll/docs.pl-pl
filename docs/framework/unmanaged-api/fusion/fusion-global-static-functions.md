---
title: Łączenie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: ff94ed23f3e39888b4f7e255feece99898f8aa74
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108271"
---
# <a name="fusion-global-static-functions"></a>Łączenie statycznych funkcji globalnych
W tej sekcji opisano niezarządzane globalne funkcje statyczne używane przez interfejs API Fusion.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ClearDownloadCache, funkcja](cleardownloadcache-function.md)  
 Czyści globalną pamięć podręczną zestawów pobranych zestawów.  
  
 [CompareAssemblyIdentity, funkcja](compareassemblyidentity-function.md)  
 Porównuje dwie tożsamości zestawów, aby określić, czy są one równoważne.  
  
 [CreateApplicationContext, funkcja](createapplicationcontext-function.md)  
 Tylko wewnętrzne. (Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [CreateAssemblyCache, funkcja](createassemblycache-function.md)  
 Pobiera wskaźnik do nowego wystąpienia [IAssemblyCache](iassemblycache-interface.md) , które reprezentuje globalną pamięć podręczną zestawów.  
  
 [CreateAssemblyEnum, funkcja](createassemblyenum-function.md)  
 Pobiera wskaźnik do wystąpienia [IAssemblyEnum](iassemblyenum-interface.md) , które reprezentuje listę obiektów istniejących w określonym zestawie.  
  
 [CreateAssemblyNameObject, funkcja](createassemblynameobject-function.md)  
 Pobiera wskaźnik do wystąpienia [IAssemblyName](iassemblyname-interface.md) , które reprezentuje unikatową tożsamość zestawu o określonej nazwie.  
  
 [CreateHistoryReader, funkcja](createhistoryreader-function.md)  
 Tworzy czytelnika historii dla określonego pliku.  
  
 [CreateInstallReferenceEnum, funkcja](createinstallreferenceenum-function.md)  
 Pobiera wskaźnik do wystąpienia [IInstallReferenceEnum](iinstallreferenceenum-interface.md) , które reprezentuje listę odwołań aplikacji do określonego zestawu.  
  
 [GetAppIdAuthority, funkcja](getappidauthority-function.md)  
 Pobiera wskaźnik do wystąpienia [IAppIdAuthority —](iappidauthority-interface.md) , które zarządza kluczami dla tożsamości i odwołań aplikacji.  
  
 [GetAssemblyIdentityFromFile, funkcja](getassemblyidentityfromfile-function.md)  
 Pobiera wskaźnik do obiektu `IUnknown` o określonym `IID` w zestawie w określonej ścieżce pliku.  
  
 [GetCachePath, funkcja](getcachepath-function.md)  
 Pobiera ścieżkę do buforowanego zestawu przy użyciu określonych flag.  
  
 [GetHistoryFileDirectory, funkcja](gethistoryfiledirectory-function.md)  
 Pobiera ścieżkę katalogu historii aplikacji.  
  
 [GetIdentityAuthority, funkcja](getidentityauthority-function.md)  
 Pobiera wskaźnik do wystąpienia [IIdentityAuthority —](iidentityauthority-interface.md) , które zarządza kluczami obiektów kodu.  
  
 [IsFrameworkAssembly, funkcja](isframeworkassembly-function.md)  
 Pobiera wartość wskazującą, czy określony zestaw jest zarządzany.  
  
 [NukeDownloadedCache, funkcja](nukedownloadedcache-function.md)  
 Usuwa pamięć podręczną pobierania środowiska uruchomieniowego języka wspólnego.  
  
 [PreBindAssemblyEx, funkcja](prebindassemblyex-function.md)  
 Pobiera nazwę wyświetlaną dla zestawu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Interfejsy łączenia](fusion-interfaces.md)  
  
 [Wyliczenia łączenia](fusion-enumerations.md)  
  
 [Łączenie — struktury](fusion-structures.md)  
  
 [Global Assembly Cache](../../app-domains/gac.md)
