---
title: "CorOpenFlags — Wyliczenie"
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
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4447f648277576169c9004d1880283728639c8f3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags — Wyliczenie
Zawiera wartości flag, które kontrolują zachowanie metadanych podczas otwierania plików manifestu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ofRead`|Wskazuje, że plik powinien zostać otwarty tylko odczyt.|  
|`ofWrite`|Wskazuje, że plik powinien zostać otwarty do zapisu.<br /><br /> Jeśli używasz `ofWrite` Flaga podczas otwierania pliku winmd, należy również przekazać `ofNoTransform` flagi.|  
|`ofReadWriteMask`|Maska do odczytu i zapisu.|  
|`ofCopyMemory`|Wskazuje, że można odczytać pliku do pamięci. Metadane należy korzystać z własnej kopii.|  
|`ofCacheImage`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofManifestMetadata`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofReadOnly`|Wskazuje, że plik powinien zostać otwarty do odczytu i że wywołanie `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nie można dokonać korekty.|  
|`ofTakeOwnership`|Wskazuje, że pamięć został przydzielony przy użyciu wywołania [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) i zostanie zwolniona w metadanych.|  
|`ofNoTypeLib`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofNoTransform`|Wskazuje, należy wyłączyć automatyczne transformacje plików winmd. Innymi słowy można wyłączyć projekcji typu środowiska wykonawczego systemu Windows, aby typ .NET Framework. Aby uzyskać więcej informacji, zobacz [Underneath maską .NET i środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Zarezerwowany do użytku wewnętrznego.|  
|`ofReserved2`|Zarezerwowany do użytku wewnętrznego.|  
|`ofReserved`|Zarezerwowany do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
