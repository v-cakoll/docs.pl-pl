---
title: ICorProfilerInfo2::GetThreadStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de0e46f4703479daeb96cb83276ec14150125e7f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587443"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a>ICorProfilerInfo2::GetThreadStaticAddress — Metoda
Pobiera adres określone pole statyczne wątku, który znajduje się w zakresie określonego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, która zawiera żądane pole statyczne wątku.  
  
 `fieldToken`  
 [in] Token metadanych dla żądanego pola statyczne wątku.  
  
 `threadId`  
 [in] Identyfikator wątku, która jest zakresem dla żądanego pola statyczne.  
  
 `ppAddress`  
 [out] Wskaźnik na adres pole statyczne, który znajduje się w określonym wątku.  
  
## <a name="remarks"></a>Uwagi  
 `GetThreadStaticAddress` Metoda może zwracać jedną z następujących czynności:  
  
- HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.  
  
- Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych. Te adresy mogą stać się nieprawidłowe po wyrzucania elementów bezużytecznych, dlatego po wyrzucania elementów kolekcji profilowania nie należy zakładać, że są prawidłowe.  
  
 Przed ukończeniem konstruktora klasy klasy `GetThreadStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może być zainicjowany i zakorzenienia wyrzucania elementów kolekcji obiektów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
