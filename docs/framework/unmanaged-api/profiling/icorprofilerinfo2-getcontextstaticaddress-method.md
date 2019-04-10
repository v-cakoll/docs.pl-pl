---
title: ICorProfilerInfo2::GetContextStaticAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 46fd79931e7f2f05b1b17ebca3f8cff28c152ff4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221430"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress — Metoda
Pobiera adres dla określonego pola statyczne kontekstu, który znajduje się w zakresie określonego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, która zawiera żądane pole statyczne kontekstu.  
  
 `fieldToken`  
 [in] Token metadanych dla żądanego pola statyczne kontekstu.  
  
 `contextId`  
 [in] Identyfikator kontekstu, która jest zakresem dla żądanego pola statyczne kontekstu.  
  
 `ppAddress`  
 [out] Wskaźnik na adres pole statyczne, który znajduje się w określonym kontekście.  
  
## <a name="remarks"></a>Uwagi  
 `GetContextStaticAddress` Metoda może zwracać jedną z następujących czynności:  
  
-   HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.  
  
-   Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych. Te adresy mogą stają się nieprawidłowe po wyrzucania elementów bezużytecznych, więc po wyrzucania elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.  
  
 Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może być zainicjowany i zakorzenienia wyrzucania elementów kolekcji obiektów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
