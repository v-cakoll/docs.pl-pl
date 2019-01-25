---
title: ICorDebugRemoteTarget — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3eb57295b72dade0bb396b3caa724b21722b26db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743507"
---
# <a name="icordebugremotetarget-interface"></a>ICorDebugRemoteTarget — Interfejs
Udostępnia metody, które umożliwiają deweloperom debugowania aplikacji opartych na technologii Silverlight w środowisku uruchomieniowym języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugRemoteTarget::GetHostName, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|Zwraca nazwę hosta lub adres IP komputera zdalnego.|  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie trybu mieszanego (czyli kodu zarządzanego i natywnego) nie jest obsługiwana na Windows 95, Windows 98 lub Windows ME lub na platformach innych niż x86 (takich jak IA-64 i AMD64).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** : CorGuids.lib  
  
 **Wersje programu .NET framework:** 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
