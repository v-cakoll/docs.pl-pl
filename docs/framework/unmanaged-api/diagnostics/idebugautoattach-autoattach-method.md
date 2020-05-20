---
title: IDebugAutoAttach::AutoAttach — Metoda
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442127"
---
# <a name="idebugautoattachautoattach-method"></a>IDebugAutoAttach::AutoAttach — Metoda
Wykonuje automatyczne dołączanie debugera wywoływanego przez serwer.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `guidPort`  
 podczas Zawsze ustawiaj na `GUID_NULL` .  
  
 `dwPid`  
 podczas Identyfikator procesu, zwykle pobierany z `GetCurrentProcessId` funkcją.  
  
 `dwProgramType`  
 podczas Typ programu: `AUTOATTACH_PROGRAM_WIN32` , `AUTOATTACH_PROGRAM_COMPLUS` , lub `AUTOATTACH_PROGRAM_UNKNOWN` .  
  
 `dwProgramId`  
 podczas Identyfikator programu.  
  
 `pszSessionId`  
 podczas Ciąg przesłany przez czasownik debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** DbgAutoAttach. h  
  
## <a name="see-also"></a>Zobacz także

- [IDebugAutoAttach — Interfejs](idebugautoattach-interface.md)
