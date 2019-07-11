---
title: IsFrameworkAssembly — Funkcja
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 989d046bba1ba3170649e9d908a850bd1177fdd2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67773831"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly — Funkcja
Pobiera wartość wskazującą, czy określony zestaw jest zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyReference`  
 [in] Nazwa zestawu do sprawdzenia.  
  
 `pbIsFrameworkAssembly`  
 [out] Wartość logiczna wskazująca, czy zestaw jest zarządzany.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Uncanonicalized ciąg, który zawiera unikatową tożsamość zestawu.  
  
 `pccSize`  
 [in] Rozmiar `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Uwagi  
 `pwzAssemblyReference` Parametr jest wskaźnikiem do ciągu znaków, który zawiera nazwę zestawu.  
  
 Jeśli ten zestaw jest częścią programu .NET Framework, `pbIsFrameworkAssembly` parametr będzie zawierać wartość logiczną `true`.  
  
 Jeśli nazwany zestaw nie jest częścią programu .NET Framework lub `pwzAssemblyReference` parametru nazwy zestawu, `pbIsFrameworkAssembly` będzie zawierać wartość logiczną `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
