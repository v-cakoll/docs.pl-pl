---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08bf4022f7cd7f85ffe7939c16fd47950e131a77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948905"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda
Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma obsługiwać wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `handle`  
 [in] Wskaźnik do obiektu zarządzanego, który ma dojścia kolekcji wyrzucania elementów. Ta wartość jest <xref:System.IntPtr> obiektu i może zostać pobrana z <xref:System.Runtime.InteropServices.GCHandle> obiektu zarządzanego.  
  
 `pOutValue`  
 [out] Wskaźnik na adres obiektu ICorDebugReferenceValue, który reprezentuje odwołanie do określonego obiektu zarządzanego.  
  
## <a name="remarks"></a>Uwagi  
 Nie należy mylić wartości zwracane odwołanie o wartości odniesienia kolekcji wyrzucania elementów.  
  
 Zwracane odwołanie zachowuje się jak normalne odwołania. Jest ona wyłączona, gdy punkt przerwania jest kontynuowane wykonywanie kodu. Okres istnienia wartość odwołania nie dotyczy okresu istnienia obiektu docelowego.  
  
> [!NOTE]
>  `GetReferenceValueFromGCHandle` Metoda nie sprawdza poprawności dojścia. W związku z tym `GetReferenceValueFromGCHandle` metoda może potencjalnie uszkodzić debugera i kod debugowany, jeśli zostanie przekazana nieprawidłowego dojścia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
