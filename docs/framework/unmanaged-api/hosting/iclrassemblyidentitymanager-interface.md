---
title: ICLRAssemblyIdentityManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b209e568b1e65ed785155d045cd48d1248672da
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209804"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager — Interfejs
Udostępnia metody, które obsługują komunikację między hostem i środowisko uruchomieniowe języka wspólnego (CLR) informacje o zestawach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBindingIdentityFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Pobiera tożsamość zestawu, wiązanie danych do zestawu w określonej ścieżce pliku.|  
|[GetBindingIdentityFromStream, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Pobiera dane tożsamości canonical zestawu dla zestawu w określonej usłudze stream.|  
|[GetCLRAssemblyReferenceList, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Pobiera [iclrassemblyreferencelist —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) wystąpienia z podanej listy tożsamości zestawu częściowego.|  
|[GetProbingAssembliesFromReference, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Pobiera [iclrprobingassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw o określonej tożsamości.|  
|[GetReferencedAssembliesFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Pobiera [iclrreferenceassemblyenum —](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) wystąpienia, które zawiera listę zestawów, które odwołuje się zestaw w określonej ścieżce pliku.|  
|[GetReferencedAssembliesFromStream, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Pobiera wskaźnik do `ICLRReferenceAssemblyEnum` obiekt, który zawiera dane o tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.|  
|[IsStronglyNamed, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `ICLRAssemblyIdentityManager` można pobrać wystąpień `ICLRAssemblyReferenceList` i wyliczania tożsamości zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)
- [ICLRProbingAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
