---
title: ICorDebugMetaDataLocator::GetMetaData — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator.GetMetaData
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator::GetMetaData
helpviewer_keywords:
- ICorDebugMetaDataLocator::GetMetaData method [.NET Framework debugging]
- GetMetaData method, ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: f9b0ff22-54db-45eb-9cc3-508000a3141d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b761d31e640063e11c1e549966bb372449fe743
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762275"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData — Metoda
Pyta, czy debugera, aby przywrócić pełną ścieżkę do modułu, którego metadanych jest potrzebne do ukończenia operacja, którą żądany debuger.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `wszImagePath`  
 [in] Ciąg zakończony znakiem null, który reprezentuje pełną ścieżkę do pliku. Jeśli pełna ścieżka nie jest dostępna, nazwę i rozszerzenie nazwy pliku (*filename*. *rozszerzenie*).  
  
 `dwImageTimeStamp`  
 [in] Sygnatura czasowa z nagłówków pliku PE obrazu. Ten parametr potencjalnie może służyć do serwera symboli ([SymSrv](/windows/desktop/debug/using-symsrv)) wyszukiwania.  
  
 `dwImageSize`  
 [in] Rozmiar obrazu z nagłówków pliku PE. Ten parametr potencjalnie może służyć do wyszukiwania SymSrv.  
  
 `cchPathBuffer`  
 [in] Znak liczby w `wszPathBuffer`.  
  
 `pcchPathBuffer`  
 [out] Liczba `WCHAR`s zapisywane `wszPathBuffer`.  
  
 Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę `WCHAR`s niezbędne do przechowywania ścieżki.  
  
 `wszPathBuffer`  
 [out] Wskaźnik do buforu, do którego debuger będzie skopiować pełną ścieżkę pliku, który zawiera żądane metadanych.  
  
 `ofReadOnly` Flaga z [coropenflags —](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) wyliczenie jest używane, aby zażądać dostępu tylko do odczytu do metadanych, w tym pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody. Wszystkie inne wartości HRESULT błędu wskazują, że plik nie jest możliwe do pobierania.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie. `wszPathBuffer` zawiera pełną ścieżkę do pliku i jest zakończony znakiem null.|  
|E_NOT_SUFFICIENT_BUFFER|Bieżący rozmiar `wszPathBuffer` nie jest wystarczająca do przechowywania pełnej ścieżki. W tym przypadku `pcchPathBuffer` zawiera wymagana liczba `WCHAR`s, łącznie z końcowym znakiem zerowym, i `GetMetaData` jest wywoływana po raz drugi z rozmiarem buforu żądanej.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `wszImagePath` zawiera pełną ścieżkę dla modułu zrzutu, określa ścieżkę z komputera, w której pobrano zrzut. Plik nie istnieje w tej lokalizacji lub niepoprawny plik o takiej samej nazwie, mogą być przechowywane w ścieżce.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugThread4, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
