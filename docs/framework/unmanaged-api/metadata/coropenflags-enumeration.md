---
title: CorOpenFlags — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108523"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags — Wyliczenie
Zawiera wartości flagi, które kontrolują zachowanie metadanych podczas otwierania plików manifestu.  
  
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
|`ofRead`|Wskazuje, czy można otworzyć pliku do odczytu tylko.|  
|`ofWrite`|Wskazuje, że plik powinien zostać otwarty do zapisu.<br /><br /> Jeśli używasz `ofWrite` Flaga podczas otwierania pliku winmd, należy także przekazać `ofNoTransform` flagi.|  
|`ofReadWriteMask`|Maska do odczytu i zapisu.|  
|`ofCopyMemory`|Wskazuje, że można odczytać pliku do pamięci. Metadane należy zachować własną kopię.|  
|`ofCacheImage`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofManifestMetadata`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofReadOnly`|Wskazuje, że dla odczytu, które można otworzyć pliku wywołanie `QueryInterface` dla [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nie może zostać wykonana.|  
|`ofTakeOwnership`|Wskazuje, że pamięć została przydzielona za pomocą wywołania [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) i zostanie zwolniona w metadanych.|  
|`ofNoTypeLib`|Nieaktualne. Ta flaga jest ignorowana.|  
|`ofNoTransform`|Wskazuje, należy wyłączyć automatyczne transformacje plików winmd. Innymi słowy należy wyłączyć projekcji typu środowiska wykonawczego Windows, aby typ .NET Framework. Aby uzyskać więcej informacji, zobacz [środowiska uruchomieniowego Windows i środowisko CLR - poniżej składniki przy użyciu platformy .NET i środowiska wykonawczego Windows](https://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Zarezerwowane do użytku wewnętrznego.|  
|`ofReserved2`|Zarezerwowane do użytku wewnętrznego.|  
|`ofReserved`|Zarezerwowane do użytku wewnętrznego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
