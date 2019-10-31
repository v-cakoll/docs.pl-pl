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
ms.openlocfilehash: e30b6f2d2254d2d107c4c82a2c5664850ce6ec23
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123066"
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
 podczas Nazwa zestawu do sprawdzenia.  
  
 `pbIsFrameworkAssembly`  
 określoną Wartość logiczna wskazująca, czy zestaw jest zarządzany.  
  
 `pwzFrameworkAssemblyIdentity`  
 podczas Niekanoniczny ciąg, który zawiera unikatową tożsamość zestawu.  
  
 `pccSize`  
 podczas Rozmiar `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Uwagi  
 `pwzAssemblyReference` parametr jest wskaźnikiem do ciągu znaków, który zawiera nazwę zestawu.  
  
 Jeśli ten zestaw jest częścią .NET Framework, parametr `pbIsFrameworkAssembly` będzie zawierać wartość logiczną `true`.  
  
 Jeśli nazwany zestaw nie jest częścią .NET Framework lub jeśli parametr `pwzAssemblyReference` nie ma nazwy zestawu, `pbIsFrameworkAssembly` będzie zawierać wartość logiczną `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
