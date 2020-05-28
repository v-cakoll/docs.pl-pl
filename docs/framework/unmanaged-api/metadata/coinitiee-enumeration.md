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
ms.openlocfilehash: f4d1c2f105abb64bf196d0dd8371c2788c97336e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005911"
---
# <a name="coinitiee-enumeration"></a>COINITIEE — Wyliczenie
Określa stałe używane przez [CoInitializeEE —](../hosting/coinitializeee-function.md) podczas inicjowania środowiska uruchomieniowego języka wspólnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum tagCOINITEE {  
   COINITEE_DEFAULT = 0x0,  
   COINITEE_DLL     = 0x1,  
   COINITEE_MAIN    = 0x2  
} COINITIEE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`COINITEE_DEFAULT`|Domyślny tryb inicjalizacji. Spowoduje to zainicjowanie środowiska uruchomieniowego i utworzenie domyślnego <xref:System.AppDomain> .|  
|`COINITEE_DLL`|Inicjuje się uruchamianie zarządzanej biblioteki DLL.|  
|`COINITEE_MAIN`|Jest inicjowany do uruchamiania zarządzanego pliku EXE. Spowoduje to zainicjowanie środowiska uruchomieniowego, ale nie spowoduje utworzenia wartości domyślnej <xref:System.AppDomain> , która jest tworzona po wprowadzeniu głównej procedury pliku exe.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
