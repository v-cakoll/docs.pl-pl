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
ms.openlocfilehash: f3a58a9ec4ed9514e748ed6c8c21a404feed9560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435670"
---
# <a name="iclrassemblyidentitymanager-interface"></a>ICLRAssemblyIdentityManager — Interfejs
Udostępnia metody, które obsługują komunikację między hostem i środowisko uruchomieniowe języka wspólnego (CLR) informacje o zestawach.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBindingIdentityFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|Pobiera tożsamość zestawu powiązania danych dla zestawu przy użyciu określonej ścieżki.|  
|[GetBindingIdentityFromStream, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|Pobiera canonical zestawu danych tożsamości dla zestawu w określonego strumienia.|  
|[GetCLRAssemblyReferenceList, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|Pobiera [ICLRAssemblyReferenceList](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md) wystąpienia z podanej listy tożsamości zestawu częściowej.|  
|[GetProbingAssembliesFromReference, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|Pobiera [ICLRProbingAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md) modułu wyliczającego dla tożsamości zestawu odwołuje się zestaw o określonej tożsamości.|  
|[GetReferencedAssembliesFromFile, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|Pobiera [ICLRReferenceAssemblyEnum](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md) wystąpienia, które zawiera listę zestawów odwołuje się zestaw przy użyciu określonej ścieżki.|  
|[GetReferencedAssembliesFromStream, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|Pobiera wskaźnik do `ICLRReferenceAssemblyEnum` obiekt zawierający dane tożsamości zestawu dla zestawów odwołuje się zestaw w określonego strumienia.|  
|[IsStronglyNamed, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-isstronglynamed-method.md)|Pobiera wartość wskazującą, czy określony zestaw ma silnej nazwy.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj `ICLRAssemblyIdentityManager` można pobrać wystąpień `ICLRAssemblyReferenceList` i wyliczyć tożsamości zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 [ICLRProbingAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
