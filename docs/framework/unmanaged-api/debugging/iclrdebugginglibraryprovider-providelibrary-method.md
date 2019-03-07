---
title: ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider.ProvideLibrary Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider::ProvideLibrary
helpviewer_keywords:
- ProvideLibrary method [.NET Framework debugging]
- ICLRDebuggingLibraryProvider::ProvideLibrary method [.NET Framework debugging]
ms.assetid: 86f06245-9517-49be-8d8c-ca5deaf34c02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3dd1038fdc8b22b99e1c8c7b753b46b9ce877355
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496446"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda
Pobiera dostawcę biblioteki interfejs wywołania zwrotnego, która umożliwia bibliotekom debudowania określonych wersji środowiska uruchomieniowego (języka wspólnego CLR) lokalizowanie i ładowanie na żądanie języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ProvideLibrary(  
     [in] const WCHAR* pwszFileName,  
     [in] DWORD dwTimestamp,  
     [in] DWORD dwSizeOfImage,  
     [out] HMODULE* hModule);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszFilename`  
 [in] Nazwa modułu żądanej.  
  
 `dwTimestamp`  
 [in] Sygnatura czasowa daty zapisane w nagłówku pliku COFF plików PE.  
  
 `pLibraryProvider`  
 [in] `SizeOfImage` Pola przechowywane w nagłówku pliku opcjonalne COFF plików PE.  
  
 `hModule`  
 [out] Dojście do żądanego modułu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 `ProvideLibrary` Umożliwia debugera, aby zapewnić moduły, które są wymagane do debugowania określone pliki CLR, takich jak plik mscordbi.dll i pliku mscordacwks.dll. Uchwyty modułu trzeba pozostaje ważne do wywołania [ICLRDebugging::CanUnloadNow](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) metoda wskazuje, że mogą one być zwolniona, w tym momencie jest obiekt wywołujący odpowiada za zwolnienie uchwyty.  
  
 Debuger może zlokalizować lub uzyskać moduł debugowania za pomocą dowolnej metody dostępne.  
  
> [!IMPORTANT]
>  Ta funkcja umożliwia wywołującego interfejs API zapewnić modułów zawierających pliku wykonywalnego i potencjalnie złośliwego kodu. Ze względów bezpieczeństwa nie należy używać obiekt wywołujący `ProvideLibrary` do dystrybucji jakiegokolwiek kodu, że nie jest gotowa do wykonania samej.  
>   
>  Jeśli problem z powodu poważnego naruszenia zabezpieczeń został odnaleziony w bibliotece już zwolnione, takich jak plik mscordbi.dll lub pliku, w tym mscordacwks.dll podkładka poprawkę można zastosować do rozpoznawania nieprawidłowe wersje plików. Podkładka można, a następnie wysyłać żądania dotyczące poprawionego wersji plików i Odrzuć nieprawidłowe wersje, jeśli są one udostępniane w odpowiedzi na każde żądanie. To może wystąpić tylko wtedy, gdy użytkownik ma zastosować poprawki do nowej wersji podkładka. Które wersje będą nadal są narażone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
