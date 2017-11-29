---
title: "PreBindAssemblyEx — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c9bd5cb6be2ccfd25d61a8a2f4347b384e1b2567
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx — Funkcja
Pobiera nazwę wyświetlaną po zastosowaniu zasad dla zestawu.  
  
 Ta funkcja obsługuje infrastrukturę programu .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppCtx`  
 [in] Identyfikuje kontekst aplikacji.  
  
 `pName`  
 [in] Określa nazwę zestawu.  
  
 `pAsmParent`  
 [in] Określa zestaw nadrzędnej. Ten parametr jest ignorowany.  
  
 `pwzRuntimeVersion`  
 [in] Identyfikuje wersję środowiska uruchomieniowego.  
  
 `ppNamePostPolicy`  
 [out] Zawiera nazwę wyświetlaną po zastosowaniu zasad.  
  
 `pvReserved`  
 [in] Zarezerwowane dla przyszłego rozszerzalności. `pvReserved`musi być odwołanie o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 `ppNamePostPolicy` Parametr wyjściowy jest ustawiona tylko wtedy, gdy funkcja zwraca HRESULT FUSION_E_REF_DEF_MISMATCH. W przeciwnym razie ma wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
