---
title: COINITIEE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COINITIEE
helpviewer_keywords:
- COINITIEE enumeration [.NET Framework metadata]
ms.assetid: 64264238-3b68-4bac-a887-36b552426a6c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48f15cc08167baaadc61787b8b1f7167304f0cae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569482"
---
# <a name="coinitiee-enumeration"></a>COINITIEE — Wyliczenie
Określa stałe używane przez [coinitializeee —](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Domyślny tryb inicjowania. To inicjuje środowisko uruchomieniowe i tworzy domyślną <xref:System.AppDomain>.|  
|`COINITEE_DLL`|Inicjuje, aby uruchomić zarządzanej biblioteki DLL.|  
|`COINITEE_MAIN`|Inicjuje do uruchamiania zarządzanego EXE. To inicjuje środowiska uruchomieniowego, ale nie tworzy domyślnie <xref:System.AppDomain>, który jest tworzony po wprowadzeniu główne procedury pliku exe.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
