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
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796320"
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
 `pwzAssemblyReference` Parametr jest wskaźnikiem do ciągu znaków, który zawiera nazwę zestawu.  
  
 Jeśli ten zestaw jest częścią .NET Framework, `pbIsFrameworkAssembly` parametr będzie zawierać `true`wartość logiczną.  
  
 Jeśli nazwany zestaw nie jest częścią .NET Framework lub jeśli `pwzAssemblyReference` parametr nie ma nazwy zestawu, `pbIsFrameworkAssembly` będzie `false`zawierać wartość logiczną.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
