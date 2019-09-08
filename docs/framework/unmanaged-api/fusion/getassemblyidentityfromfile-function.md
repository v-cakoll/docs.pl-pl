---
title: GetAssemblyIdentityFromFile — Funkcja
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2657ac619bb86bc200de9ce229bf82e4339f78d6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796296"
---
# <a name="getassemblyidentityfromfile-function"></a>GetAssemblyIdentityFromFile — Funkcja
Pobiera wskaźnik do `IUnknown` obiektu z określonym `IID` w zestawie w określonej ścieżce pliku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 podczas Prawidłowa ścieżka do żądanego zestawu.  
  
 `riid`  
 podczas `IID` Interfejs do zwrócenia.  
  
 `ppIdentity`  
 określoną Zwrócony wskaźnik interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IUnknown](/cpp/atl/iunknown)
- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
