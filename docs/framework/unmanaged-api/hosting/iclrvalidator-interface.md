---
title: ICLRValidator — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRValidator
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator
helpviewer_keywords:
- ICLRValidator interface [.NET Framework hosting]
ms.assetid: 2edd0a10-77fb-4173-91eb-f2970cc364d0
topic_type:
- apiref
ms.openlocfilehash: e071f9cba7e991c59bf697647e0e4badea57573a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762048"
---
# <a name="iclrvalidator-interface"></a>ICLRValidator — Interfejs
Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[FormatEventInfo, metoda](iclrvalidator-formateventinfo-method.md)|Pobiera szczegółowy komunikat o określonym błędzie walidacji.|  
|[Validate, metoda](iclrvalidator-validate-method.md)|Sprawdza poprawność przenośnego pliku wykonywalnego lub języka pośredniego firmy Microsoft (MSIL) w określonym pliku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** IValidator. idl, IValidator. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRErrorReportingManager, interfejs](iclrerrorreportingmanager-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [CLRRuntimeHost, klasa coclass](clrruntimehost-coclass.md)
