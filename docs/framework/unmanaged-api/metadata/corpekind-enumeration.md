---
title: "CorPEKind — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: CorPEKind
helpviewer_keywords: CorPEKind enumeration [.NET Framework metadata]
ms.assetid: 22dc6dea-b1b9-4982-a730-a022d586b117
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 612c71db092e7a3474d262c1d601335a5f416791
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corpekind-enumeration"></a>CorPEKind — Wyliczenie
Zawiera wartości, które opisują pliku przenośny plik wykonywalny (PE), ponieważ zwracany po wywołaniu [IMetaDataImport2::GetPEKind](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorPEKind {  
  
    peNot           = 0x00000000,  
    peILonly        = 0x00000001,  
    pe32BitRequired = 0x00000002,  
    pe32Plus        = 0x00000004,  
    pe32Unmanaged   = 0x00000008,  
    pe32BitPreferred= 0x00000010  
  
} CorPEKind;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`peNot`|Wskazuje, że nie jest plikiem PE.|  
|`peILOnly`|Wskazuje, czy ten plik PE zawiera tylko kod zarządzany.|  
|`pe32BitRequired`|Wskazuje, czy ten plik PE wywołań Win32.|  
|`pe32Plus`|Wskazuje, czy ten plik PE jest uruchamiana na 64-bitowej platformy.|  
|`pe32Unmanaged`|Wskazuje, że ten plik PE jest kodu natywnego.|  
|pe32BitPreferred|Wskazuje, czy ten plik PE jest niezależny od platformy i preferuje do załadowania w środowisku 32-bitowym.|  
  
## <a name="remarks"></a>Uwagi  
 Można używać tych wartości bitowe kombinacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
