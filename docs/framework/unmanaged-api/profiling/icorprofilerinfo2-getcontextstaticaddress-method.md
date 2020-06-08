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
ms.openlocfilehash: 7550caaa7cb4d7ed77dc36ecf0ce0e0cbc541db7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497065"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress — Metoda
Pobiera adres dla określonego kontekstu-static pola, które znajduje się w zakresie określonego kontekstu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 podczas Identyfikator klasy, która zawiera wymagane pole kontekstu-static.  
  
 `fieldToken`  
 podczas Token metadanych dla żądanego pola kontekstu-static.  
  
 `contextId`  
 podczas Identyfikator kontekstu, który jest zakresem dla żądanego pola kontekstowego.  
  
 `ppAddress`  
 określoną Wskaźnik do adresu pola statycznego znajdującego się w określonym kontekście.  
  
## <a name="remarks"></a>Uwagi  
 `GetContextStaticAddress`Metoda może zwracać jedną z następujących wartości:  
  
- CORPROF_E_DATAINCOMPLETE HRESULT, jeśli podane pole statyczne nie ma przypisanego adresu w określonym kontekście.  
  
- Adresy obiektów, które mogą znajdować się w stercie wyrzucania elementów bezużytecznych. Te adresy mogą stać się nieprawidłowe po wyrzucaniu elementów bezużytecznych, więc po wybraniu elementów bezużytecznych nie należy zakładać, że są one poprawne.  
  
 Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwraca CORPROF_E_DATAINCOMPLETE dla wszystkich pól statycznych, chociaż niektóre pola statyczne mogą już być zainicjowane i główne obiekty wyrzucania elementów bezużytecznych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](icorprofilerinfo2-interface.md)
