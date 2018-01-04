---
title: "ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cf6860a616312504e3d23177734cb532405bd714
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda
Pobiera dostawcę biblioteki interfejsu wywołania zwrotnego, który umożliwia wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) określonej wersji biblioteki debugowania należy odnaleźć i załadować na żądanie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFilename`  
 [in] Nazwa modułu żądanej.  
  
 `dwTimestamp`  
 [in] Sygnatury czasowej przechowywane w nagłówku pliku PE — pliki COFF.  
  
 `pLibraryProvider`  
 [in] `SizeOfImage` Pola przechowywane w nagłówku COFF opcjonalny plik PE — pliki.  
  
 `hModule`  
 [out] Dojście do żądanego modułu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `ProvideLibrary`Umożliwia debugera zapewnić modułów, które są wymagane do debugowania określonych plików CLR, takie jak mscordbi.dll i pliku mscordacwks.dll. Uchwyty modułu muszą być prawidłowe do wywołania [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metody wskazuje, że mogą one zostać zwolniony w takim przypadku odpowiada wywołującego wolne uchwytów.  
  
 Debuger może używać oznacza, że wszystkie dostępne do zlokalizowania lub uzyskaj moduł debugowania.  
  
> [!IMPORTANT]
>  Ta funkcja umożliwia wywołującego interfejs API zapewnić modułów zawierających pliku wykonywalnego i potencjalnie złośliwego kodu. Ze względów bezpieczeństwa nie należy używać wywołującego `ProvideLibrary` do dystrybucji dowolny kod, że nie jest gotowa do wykonania sam.  
>   
>  Jeśli poważny problem został odnaleziony w bibliotece już zwolnione, takie jak mscordbi.dll lub pliku mscordacwks.dll, podkładki można serwisować rozpoznawanie zły wersje plików. Podkładka może, a następnie wysyłania żądań do poprawioną wersje plików i odrzucić zły wersji, jeśli są one udostępniane w odpowiedzi na każde żądanie. To może występować tylko wtedy, gdy użytkownik ma poprawiono do nowej wersji poprawki. Które wersje pozostanie zagrożone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
