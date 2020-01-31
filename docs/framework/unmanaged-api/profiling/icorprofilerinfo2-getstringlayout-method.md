---
title: ICorProfilerInfo2::GetStringLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
ms.openlocfilehash: 537840ac03b4136682b78cb964950ab5670a7d7e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868619"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout — Metoda
Pobiera informacje o układzie obiektu ciągu. Ta metoda jest przestarzała w .NET Framework 4 i jest zastępowana przez metodę [ICorProfilerInfo3:: GetStringLayout2 —](icorprofilerinfo3-getstringlayout2-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `pBufferLengthOffset`  
 określoną Wskaźnik do przesunięcia lokalizacji względem wskaźnika `ObjectID`, w którym jest przechowywana długość ciągu. Długość jest przechowywana jako `DWORD`.  
  
> [!NOTE]
> Ten parametr zwraca długość samego ciągu, a nie długość buforu. Długość buforu nie jest już dostępna.  
  
 `PStringLengthOffset`  
 określoną Wskaźnik do przesunięcia lokalizacji względem wskaźnika `ObjectID`, w którym jest przechowywana długość ciągu. Długość jest przechowywana jako `DWORD`.  
  
 `pBufferOffset`  
 określoną Wskaźnik do przesunięcia buforu względem wskaźnika `ObjectID`, który przechowuje ciąg znaków dwubajtowych.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `GetStringLayout` pobiera przesunięcia, względem wskaźnika `ObjectID`, lokalizacji, w których są przechowywane następujące elementy:  
  
- Długość buforu ciągu.  
  
- Długość samego ciągu.  
  
- Bufor, który zawiera rzeczywisty ciąg znaków dwubajtowych.  
  
 Ciągi mogą być zakończone wartością null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
