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
ms.openlocfilehash: e6708971909c1035e41786f4d8dad1cf9afdffaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665615"
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

#### <a name="parameters"></a>Parametry

`pNativeCodeStartAddress` \
podczas Wskaźnik do początku funkcji natywnej.

`cCodeInfos` \
podczas Rozmiar `codeInfos` tablicy.

`pcCodeInfos` \
określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .

`codeInfos` \
określoną Bufor dostarczony przez wywołującego. Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.

## <a name="remarks"></a>Uwagi

Metoda jest podobna do GetCodeInfo3 —, z tą różnicą, że może wyszukiwać informacje o kodzie dla różnych natywnych wersji metody. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`

> [!NOTE]
> `GetCodeInfo4`może wyzwolić wyrzucanie elementów bezużytecznych.

Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).

Po `GetCodeInfo4` powrocie należy sprawdzić `codeInfos` , czy bufor jest wystarczająco duży, aby można było zawierać wszystkie struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru. Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) jest `pcCodeInfos`mniejsza niż, Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo4` .

Alternatywnie, można najpierw wywołać `GetCodeInfo4` z buforem o zerowej długości `codeInfos` , aby uzyskać prawidłowy rozmiar buforu. Następnie `codeInfos` można ustawić rozmiar buforu na wartość zwróconą `pcCodeInfos`w, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo4` .

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).

**Nagłówki** CorProf. idl, CorProf. h

**Biblioteki** CorGuids.lib

**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo9, interfejs](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
