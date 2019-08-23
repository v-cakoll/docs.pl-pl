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
ms.openlocfilehash: 21da325ee58df65ac449464f8292f2ba94d99338
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943296"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a>ICorDebugProcess2::GetReferenceValueFromGCHandle — Metoda
Pobiera wskaźnik odwołania do określonego obiektu zarządzanego, który ma dojście do wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `handle`  
 podczas Wskaźnik do zarządzanego obiektu, który ma dojście do wyrzucania elementów bezużytecznych. Ta wartość jest <xref:System.IntPtr> obiektem i można ją pobrać <xref:System.Runtime.InteropServices.GCHandle> z elementu dla obiektu zarządzanego.  
  
 `pOutValue`  
 określoną Wskaźnik do adresu obiektu ICorDebugReferenceValue, który reprezentuje odwołanie do określonego obiektu zarządzanego.  
  
## <a name="remarks"></a>Uwagi  
 Nie należy mylić zwróconej wartości odniesienia z wartością referencyjną wyrzucania elementów bezużytecznych.  
  
 Zwrócone odwołanie zachowuje się jak normalne odwołanie. Jest ono wyłączone, gdy wykonanie kodu jest kontynuowane po punkcie przerwania. Okres istnienia obiektu docelowego nie ma wpływ na czas istnienia wartości referencyjnej.  
  
> [!NOTE]
> `GetReferenceValueFromGCHandle` Metoda nie sprawdza poprawności dojścia. W `GetReferenceValueFromGCHandle` związku z tym, Metoda może potencjalnie uszkodzić debuger i kod debugowany w przypadku przekazanie nieprawidłowego dojścia.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
