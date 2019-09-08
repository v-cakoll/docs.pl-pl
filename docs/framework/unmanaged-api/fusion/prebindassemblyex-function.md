---
title: PreBindAssemblyEx — Funkcja
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8aa2d174200db76f5c7a6db43e14bb6904604226
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796326"
---
# <a name="prebindassemblyex-function"></a>PreBindAssemblyEx — Funkcja
Pobiera nazwę wyświetlaną dla zestawu.  
  
 Ta funkcja obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppCtx`  
 podczas Identyfikuje kontekst aplikacji.  
  
 `pName`  
 podczas Identyfikuje nazwę zestawu.  
  
 `pAsmParent`  
 podczas Identyfikuje zestaw nadrzędny. Ten parametr jest ignorowany.  
  
 `pwzRuntimeVersion`  
 podczas Identyfikuje wersję środowiska uruchomieniowego.  
  
 `ppNamePostPolicy`  
 określoną Zawiera nazwę wyświetlaną po wprowadzeniu zasad.  
  
 `pvReserved`  
 podczas Zarezerwowane do użytku w przyszłości. `pvReserved`musi być odwołaniem o wartości null.  
  
## <a name="remarks"></a>Uwagi  
 Parametr `ppNamePostPolicy` Output jest ustawiany tylko wtedy, gdy funkcja zwraca wartość HRESULT FUSION_E_REF_DEF_MISMATCH. W przeciwnym razie ma wartość null.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Fusion. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)
