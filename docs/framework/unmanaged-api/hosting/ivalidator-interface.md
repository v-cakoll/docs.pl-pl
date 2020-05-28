---
title: IValidator — Interfejs
ms.date: 03/30/2017
api_name:
- IValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IValidator
helpviewer_keywords:
- IValidator interface [.NET Framework hosting]
ms.assetid: b297e3b0-20f9-478f-b707-5e2eecb2b5b2
topic_type:
- apiref
ms.openlocfilehash: d8e5ab607f9310341ded482b35f02f3845926328
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008563"
---
# <a name="ivalidator-interface"></a>IValidator — Interfejs
Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|Walidacja|Sprawdza poprawność określonego pliku PE lub języka pośredniego firmy Microsoft (MSIL).|  
|FormatEventInfo —|Pobiera komunikat o błędzie odpowiadający określonemu błędowi walidacji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator. idl, IValidator. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Hosting, interfejsy](hosting-interfaces.md)
- [CorRuntimeHost, klasa coclass](corruntimehost-coclass.md)
