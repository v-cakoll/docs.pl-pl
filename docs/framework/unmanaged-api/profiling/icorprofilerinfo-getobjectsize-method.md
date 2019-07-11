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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd337ca6d7b03ad22f178c9c7084cfa2585da73c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782747"
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
 [in] Identyfikator obiektu.  
  
 `pcSize`  
 [out] Wskaźnik do obiektu, rozmiar w bajtach.  
  
## <a name="remarks"></a>Uwagi  
  
> [!IMPORTANT]
>  Ta metoda jest przestarzała. Zwraca COR_E_OVERFLOW obiektów większą niż 4GB na platformach 64-bitowych. Użyj [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metody zamiast tego.  
  
 Te same typy dwóch różnych obiektów często mają taki sam rozmiar. Jednak niektóre typy, takie jak tablice i ciągów, może mieć inny rozmiar dla każdego obiektu.  
  
 Rozmiar zwrócony przez `GetObjectSize` metoda nie zawiera żadnych dopełnienie wyrównanie, które mogą być wyświetlane po obiektu na stercie wyrzucania elementów bezużytecznych. Jeśli używasz `GetObjectSize` metody, aby przejść do innego obiektu na stercie wyrzucania elementów bezużytecznych, Dodaj wyrównanie dopełnienie ręcznego zgodnie z potrzebami.  
  
- Na Windows 32-bitowych COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 użyj 4-bajtowe wyrównanie i COR_PRF_GC_LARGE_OBJECT_HEAP korzysta z 8-bajtowe wyrównanie.  
  
- Na Windows 64-bitowych wyrównania jest zawsze 8 bajtów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
