---
title: ICorProfilerInfo::GetObjectSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: b860cf6eb07c3f063e3e51514f8492cf4af9e8ed
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869675"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize — Metoda
Pobiera rozmiar określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>Parametry  
 `objectId`  
 podczas Identyfikator obiektu.  
  
 `pcSize`  
 określoną Wskaźnik do rozmiaru obiektu, w bajtach.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
> Ta metoda jest przestarzała. Zwraca COR_E_OVERFLOW dla obiektów większych niż 4 GB na platformach 64-bitowych. Zamiast tego użyj metody [ICorProfilerInfo4:: GetObjectSize2 —](icorprofilerinfo4-getobjectsize2-method.md) .  
  
 Różne obiekty tego samego typu często mają ten sam rozmiar. Jednak niektóre typy, takie jak tablice lub ciągi, mogą mieć różne rozmiary dla każdego obiektu.  
  
 Rozmiar zwrócony przez metodę `GetObjectSize` nie obejmuje żadnego dopełnienia wyrównania, które może być wyświetlane po obiekcie na stercie wyrzucania elementów bezużytecznych. Jeśli używasz metody `GetObjectSize`, aby przejść z obiektu do obiektu na stercie wyrzucania elementów bezużytecznych, w razie potrzeby dodaj ręcznie wyrównania.  
  
- W 32-bitowym systemie Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 użyć 4-bajtowego wyrównania, a COR_PRF_GC_LARGE_OBJECT_HEAP używa wyrównania 8-bajtowego.  
  
- W 64-bitowym systemie Windows wyrównanie ma zawsze 8 bajtów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
