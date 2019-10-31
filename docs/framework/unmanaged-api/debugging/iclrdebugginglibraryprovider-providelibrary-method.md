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
ms.openlocfilehash: 8fc2abd0728115edbbfae42958d8013029523ed1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111362"
---
# <a name="iclrdebugginglibraryproviderprovidelibrary-method"></a>ICLRDebuggingLibraryProvider::ProvideLibrary — Metoda

Pobiera interfejs wywołania zwrotnego dostawcy biblioteki, który umożliwia zlokalizowanie i załadowanie bibliotek debugowania specyficznych dla wersji środowiska uruchomieniowego języka wspólnego (CLR) na żądanie.

## <a name="syntax"></a>Składnia

```cpp
HRESULT ProvideLibrary(
     [in] const WCHAR* pwszFileName,
     [in] DWORD dwTimestamp,
     [in] DWORD dwSizeOfImage,
     [out] HMODULE* hModule);
```

## <a name="parameters"></a>Parametry

`pwszFilename` \
podczas Nazwa żądanego modułu.

`dwTimestamp` \
podczas Sygnatura czasowa, która jest przechowywana w nagłówku pliku COFF plików PE.

`pLibraryProvider` \
podczas Pole `SizeOfImage` przechowywane w nagłówku opcjonalnego pliku COFF dla plików PE.

`hModule` \
określoną Uchwyt do żądanego modułu.

## <a name="return-value"></a>Wartość zwracana

Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.

|HRESULT|Opis|
|-------------|-----------------|
|S_OK|Metoda została ukończona pomyślnie.|

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi

`ProvideLibrary` umożliwia debugerowi dostarczenie modułów, które są konieczne do debugowania określonych plików CLR, takich jak mscordbi. dll i mscordacwks. dll. Obsługa modułów musi pozostać ważna, dopóki wywołanie metody [ICLRDebugging:: CanUnloadNow —](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md) nie wskazuje, że mogą być zwolnione, a tym samym jest odpowiedzialnością wywołującą, aby zwolnić dojścia.

Debuger może używać dowolnego dostępnego środka do lokalizowania lub pozyskiwania modułu debugowania.

> [!IMPORTANT]
> Ta funkcja umożliwia obiektowi wywołującemu interfejsu API dostarczanie modułów, które zawierają plik wykonywalny, i prawdopodobnie złośliwego kodu. Ze względów bezpieczeństwa obiekt wywołujący nie powinien używać `ProvideLibrary` do dystrybuowania dowolnego kodu, który nie jest gotowy do wykonania.
>
> W przypadku odnalezienia poważnego problemu z zabezpieczeniami w już wydanej bibliotece, takiej jak mscordbi. dll lub mscordacwks. dll, Poprawka podkładki może zostać poprawiona w celu rozpoznania nieprawidłowych wersji plików. Podkładka może następnie wydać żądania dotyczące wersji plików z poprawkami i odrzucić niewłaściwe wersje, jeśli są one dostarczane w odpowiedzi na jakiekolwiek żądanie. Taka sytuacja może wystąpić tylko wtedy, gdy użytkownik połączył się z nową wersją podkładki. Niepoprawione wersje pozostaną zagrożone.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).

**Nagłówek:** CorDebug. idl, CorDebug. h

**Biblioteka:** CorGuids. lib

**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
