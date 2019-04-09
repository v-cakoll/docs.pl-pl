---
title: ICLRProbingAssemblyEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum
helpviewer_keywords:
- ICLRProbingAssemblyEnum interface [.NET Framework hosting]
ms.assetid: e7d3ccab-b0f0-4872-8935-0ed72920171b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 118345f246de3d7ee68d51cf37e8cdea9de1fdba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094297"
---
# <a name="iclrprobingassemblyenum-interface"></a>ICLRProbingAssemblyEnum — Interfejs
Udostępnia metody umożliwiające hosta można pobrać badania tożsamości zestawu przy użyciu informacji o tożsamości zestawu, jest wewnętrzny środowisko uruchomieniowe języka wspólnego (CLR), bez konieczności tworzenia lub zrozumieć tej tożsamości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Get, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-get-method.md)|Pobiera tożsamość zestawu pod określonym indeksem.|  
  
## <a name="remarks"></a>Uwagi  
 Metody takie jak [iclrassemblyidentitymanager::getprobingassembliesfromreference —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md) zwracają `ICLRProbingAssemblyEnum` wystąpienia.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyIdentityManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [ICLRAssemblyReferenceList — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
