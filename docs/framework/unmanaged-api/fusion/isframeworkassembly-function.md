---
title: "IsFrameworkAssembly — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IsFrameworkAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IsFrameworkAssembly
helpviewer_keywords: IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 216a7221550cb6345b29b5ed9e45b13ce40eadf4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly — Funkcja
Pobiera wartość wskazującą, czy jest zarządzana w określonym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzAssemblyReference`  
 [in] Nazwa zestawu do sprawdzenia.  
  
 `pbIsFrameworkAssembly`  
 [out] Wartość logiczna wskazująca, czy zestaw jest zarządzana.  
  
 `pwzFrameworkAssemblyIdentity`  
 [in] Uncanonicalized ciąg, który zawiera unikatową tożsamość zestawu.  
  
 `pccSize`  
 [in] Rozmiar `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Uwagi  
 `pwzAssemblyReference` Parametr jest wskaźnikiem do ciągu znaków, który zawiera nazwę zestawu.  
  
 Jeśli ten zestaw jest częścią programu .NET Framework, `pbIsFrameworkAssembly` parametr będzie zawierać wartość logiczną `true`.  
  
 Jeśli nazwany zestaw nie jest częścią programu .NET Framework lub `pwzAssemblyReference` parametru nie nadaje nazwy zestawu `pbIsFrameworkAssembly` będzie zawierać wartość logiczną `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
