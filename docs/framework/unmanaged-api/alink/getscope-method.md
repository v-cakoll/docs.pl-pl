---
title: GetScope metoda1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4cb51efc3f431dac4a10cc7582e2b43500ccba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getscope-method1"></a>GetScope metoda1
Pobiera zakres importu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `AssemblyID`  
 Unikatowy identyfikator zestawu, aby zaimportować.  
  
 `FileToken`  
 Unikatowy identyfikator pliku importowanego.  
  
 `dwScope`  
 Liczony od zera zakres do zaimportowania.  
  
 `ppImportScope`  
 Odbiera [IMetaDataImport — interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interfejs dla zakresu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga alink.h  
  
## <a name="see-also"></a>Zobacz też  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [IALink2, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
