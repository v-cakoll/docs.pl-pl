---
title: CorFileMapping — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorFileMapping
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFileMapping
helpviewer_keywords:
- CorFileMapping enumeration [.NET Framework metadata]
ms.assetid: 3ca41592-b8da-475a-8032-a15627730003
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 719f0522cc43625a4d6cc8afa838d869e47b40d1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781833"
---
# <a name="corfilemapping-enumeration"></a>CorFileMapping — Wyliczenie
Zawiera wartości, które opisują typ mapowania pliku, który jest zwracany po wywołaniu [IMetaDataInfo::GetFileMapping](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorFileMapping {  
  
    fmFlat                  =   0x0000,  
    fmExecutableImage       =   0x0001  
  
} CorFileMapping;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`fmFlat`|Plik jest mapowany jako pliku danych. Oznacza to, że `SEC_IMAGE` flaga nie został przekazany do Microsoft Win32 `CreateFileMapping` funkcji.|  
|`fmExecutableImage`|Plik jest mapowany na wykonanie, przy użyciu `LoadLibrary` funkcji lub `CreateFileMapping` funkcją `SEC_IMAGE` flagi.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [GetFileMapping, metoda](../../../../docs/framework/unmanaged-api/metadata/imetadatainfo-getfilemapping-method.md)
