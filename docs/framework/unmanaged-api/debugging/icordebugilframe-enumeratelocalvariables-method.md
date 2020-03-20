---
title: ICorDebugILFrame::EnumerateLocalVariables — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: c071a7ddb7d8d3f0e6487ab85284c45f9a7f0372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178845"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a>ICorDebugILFrame::EnumerateLocalVariables — Metoda
Pobiera wyliczenia dla zmiennych lokalnych w tej ramce.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppValueEnum`  
 [na zewnątrz] Wskaźnik do adresu obiektu ICorDebugValueEnum, który jest wyliczaczem zmiennych lokalnych w tej ramce.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateLocalVariables`pobiera wyliczenia, który można wyświetlić listę zmiennych lokalnych dostępnych w ramce wywołania, który jest reprezentowany przez ten obiekt ICorDebugILFrame. Lista może nie zawierać wszystkich zmiennych lokalnych w uruchomionej funkcji, ponieważ niektóre z nich mogą nie być aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
