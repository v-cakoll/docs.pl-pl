---
title: "ICorProfilerInfo2::GetContextStaticAddress — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress — Metoda
Pobiera adres dla określonego pola statycznej kontekstu, który znajduje się w zakresie określonego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a>Parametry  
 `classId`  
 [in] Identyfikator klasy, która zawiera żądane pole kontekstu statycznego.  
  
 `fieldToken`  
 [in] Token metadanych dla żądanego pola kontekstu statycznego.  
  
 `contextId`  
 [in] Identyfikator kontekstu, która jest zakresem dla żądanego pola statyczne kontekstu.  
  
 `ppAddress`  
 [out] Wskaźnik do adresu pola statycznego, który znajduje się w określonym kontekście.  
  
## <a name="remarks"></a>Uwagi  
 `GetContextStaticAddress` Metoda może zwracać jedną z następujących czynności:  
  
-   HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.  
  
-   Adresy obiektów, które mogą znajdować się w pamięci sterty kolekcji. Te adresy mogą być nieprawidłowe po wyrzucanie elementów bezużytecznych, więc po wyrzucanie elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.  
  
 Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może zainicjować i umieszczanie w katalogu głównym odzyskiwanie kolekcji obiektów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
