---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868307"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4, Metoda

Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Parametry

- `pNativeCodeStartAddress`

  \[w] wskaźnik do początku funkcji natywnej.

- `cCodeInfos`

  \[w] rozmiar tablicy `codeInfos`.

- `pcCodeInfos`

  \[out] wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .

- `codeInfos`

  \[out] bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.

## <a name="remarks"></a>Uwagi

Metoda `GetCodeInfo4` jest podobna do [GetCodeInfo3 —](icorprofilerinfo4-getcodeinfo3-method.md), z tą różnicą, że może wyszukiwać informacje o kodzie dla różnych natywnych wersji metody.

> [!NOTE]
> `GetCodeInfo4` może wyzwolić wyrzucanie elementów bezużytecznych.

Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).

Po powrocie `GetCodeInfo4` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) . W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`. Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo4`.

Alternatywnie można najpierw wywołać `GetCodeInfo4` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu. Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo4`.

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**Nagłówek:** CorProf. idl, CorProf. h

**Biblioteka:** CorGuids. lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo9, interfejs](ICorProfilerInfo9-interface.md)
