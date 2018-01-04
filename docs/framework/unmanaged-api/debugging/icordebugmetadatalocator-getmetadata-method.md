---
title: "ICorDebugMetaDataLocator::GetMetaData — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMetaDataLocator.GetMetaData
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4883ee56c7dd027f053dd072d7c8613f606ff2be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData — Metoda
Pyta debugera do zwrócenia pełną ścieżkę do modułu, którego metadanych wymaganego do ukończenia operacji żądanej przez debuger.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetMetaData(  
      [in] LPCWSTR wszImagePath,  
      [in] DWORD   dwImageTimeStamp,  
      [in] DWORD   dwImageSize,  
      [in] ULONG32 cchPathBuffer,  
      [out] ULONG32 * pcchPathBuffer,  
      [out, size_is(cchPathBuffer), length_is(*pcchPathBuffer)]  
               WCHAR wszPathBuffer[]  
      );  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszImagePath`  
 [in] Ciąg zerem, który reprezentuje pełną ścieżkę do pliku. Jeśli pełna ścieżka nie jest dostępna, nazwę i rozszerzenie pliku (*filename*. *rozszerzenie*).  
  
 `dwImageTimeStamp`  
 [in] Sygnatura czasowa z nagłówków pliku PE obrazu. Ten parametr potencjalnie może służyć do serwera symboli ([SymSrv](http://msdn.microsoft.com/library/cc266470.aspx)) wyszukiwania.  
  
 `dwImageSize`  
 [in] Rozmiar obrazu z nagłówków pliku PE. Ten parametr potencjalnie może służyć do wyszukiwania SymSrv.  
  
 `cchPathBuffer`  
 [in] Liczba znaków `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Liczba `WCHAR`s zapisane `wszPathBuffer`.  
  
 Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę `WCHAR`s niezbędne do przechowywania ścieżki.  
  
 `wszPathBuffer`  
 [out] Wskaźnik do buforu, w której debuger skopiuje pełną ścieżkę pliku, który zawiera żądanych metadanych.  
  
 `ofReadOnly` Flaga z [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie jest używane do żądania dostępu tylko do odczytu do metadanych w tym pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody. Wszystkich innych wyników HRESULT awarii wskazują, że plik nie jest pobieranie.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie. `wszPathBuffer`zawiera pełną ścieżkę do pliku i jest zerem.|  
|E_NOT_SUFFICIENT_BUFFER|Bieżący rozmiar `wszPathBuffer` nie jest wystarczająca do przechowywania pełną ścieżkę. W takim przypadku `pcchPathBuffer` zawiera wymagana liczba `WCHAR`s, w tym znak końcowy null i `GetMetaData` jest wywoływana po raz drugi z rozmiarem buforu żądanej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `wszImagePath` zawiera pełną ścieżkę dla modułu zrzutu Określa ścieżkę z komputera, na którym zrzut został zebrany. Plik nie istnieje w tej lokalizacji lub niepoprawny plik o tej samej nazwie może być przechowywany w ścieżce.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
