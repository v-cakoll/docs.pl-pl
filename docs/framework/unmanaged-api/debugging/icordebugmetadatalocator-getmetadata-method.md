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
ms.openlocfilehash: d9269339e8e2ae8d00da701b015aa30cd51cbef3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213377"
---
# <a name="icordebugmetadatalocatorgetmetadata-method"></a>ICorDebugMetaDataLocator::GetMetaData — Metoda
Prosi debugera o zwrócenie pełnej ścieżki do modułu, którego metadane są wymagane do ukończenia operacji wymaganej przez debuger.  
  
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
 podczas Ciąg zakończony znakiem null, który reprezentuje pełną ścieżkę do pliku. Jeśli pełna ścieżka nie jest dostępna, nazwa i rozszerzenie pliku (*filename*.* rozszerzenie*).  
  
 `dwImageTimeStamp`  
 podczas Sygnatura czasowa z nagłówków pliku PE obrazu. Ten parametr może być potencjalnie używany dla wyszukiwania serwera symboli ([SymSrv](/windows/desktop/debug/using-symsrv)).  
  
 `dwImageSize`  
 podczas Rozmiar obrazu z nagłówków pliku PE. Ten parametr może być potencjalnie używany dla wyszukiwania SymSrv.  
  
 `cchPathBuffer`  
 podczas Liczba znaków w `wszPathBuffer` .  
  
 `pcchPathBuffer`  
 określoną Liczba `WCHAR` s zapisywana w `wszPathBuffer` .  
  
 Jeśli metoda zwraca E_NOT_SUFFICIENT_BUFFER, zawiera liczbę elementów `WCHAR` wymaganych do przechowania ścieżki.  
  
 `wszPathBuffer`  
 określoną Wskaźnik do buforu, do którego debuger skopiuje pełną ścieżkę pliku zawierającego żądane metadane.  
  
 `ofReadOnly`Flaga z wyliczenia [CorOpenFlags —](../metadata/coropenflags-enumeration.md) jest używana do żądania dostępu tylko do odczytu do metadanych w tym pliku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody. Wszystkie inne błędy HRESULT wskazują, że plik nie jest możliwy do pobierania.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie. `wszPathBuffer`zawiera pełną ścieżkę do pliku i jest zakończony znakiem null.|  
|E_NOT_SUFFICIENT_BUFFER|Bieżący rozmiar `wszPathBuffer` nie jest wystarczający do przechowywania pełnej ścieżki. W tym przypadku `pcchPathBuffer` zawiera wymaganą liczbę `WCHAR` s, w tym kończący znak null, i `GetMetaData` jest wywoływana po raz drugi z żądanym rozmiarem buforu.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli `wszImagePath` zawiera pełną ścieżkę do modułu ze zrzutu, określa ścieżkę do komputera, na którym został zebrany zrzut. Plik może nie istnieć w tej lokalizacji lub w ścieżce może być przechowywany nieprawidłowy plik o takiej samej nazwie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugThread4 — Interfejs](icordebugthread4-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
