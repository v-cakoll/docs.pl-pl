---
title: CorPinvokeMap — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 951941092f67f66c5b17c8ae592569c2a8e6a675
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079633"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap — Wyliczenie
Określa opcje dla wywołań PInvoke.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,   
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pmNoMangle`|Użyj nazwy elementów członkowskich określonych.|  
|`pmCharSetMask`|Zastrzeżone.|  
|`pmCharSetNotSpec`|Zastrzeżone.|  
|`pmCharSetAnsi`|Przeprowadzanie marshalingu ciągów jako ciągi wielu-bajtowych wartości znakowych.|  
|`pmCharSetUnicode`|Przeprowadzanie marshalingu ciągów Unicode znaki 2-bajtowe.|  
|`pmCharSetAuto`|Automatycznie kierować ciągi, odpowiednio dla docelowego systemu operacyjnego. Wartość domyślna to Unicode na Windows NT, Windows 2000, Windows XP i rodziny Windows Server 2003; Wartość domyślna to ANSI w systemach Windows 98 i Windows Me.|  
|`pmBestFitUseAssem`|Zastrzeżone.|  
|`pmBestFitEnabled`|Wykonaj mapowanie znaków Unicode, których brakuje dokładnego dopasowania do zestawu znaków ANSI.|  
|`pmBestFitDisabled`|Nie wykonuj mapowanie znaków Unicode. W takim przypadku wszystkie, którego nie można zmapować znaki zostaną zastąpione przez "?".|  
|`pmBestFitMask`|Zastrzeżone.|  
|`pmThrowOnUnmappableCharUseAssem`|Zastrzeżone.|  
|`pmThrowOnUnmappableCharEnabled`|Zgłoś wyjątek, jeśli Organizator międzyoperacyjny napotka znaku, którego nie można zmapować.|  
|`pmThrowOnUnmappableCharDisabled`|Nie zgłasza wyjątku, gdy organizator międzyoperacyjny napotka znaku, którego nie można zmapować.|  
|`pmThrowOnUnmappableCharMask`|Zarezerwowany|  
|`pmSupportsLastError`|Zezwalaj na / / wywoływany w celu wywołania Win32 `SetLastError` funkcji przed zwróceniem z atrybutami metody.|  
|`pmCallConvMask`|Zarezerwowany|  
|`pmCallConvWinapi`|Użyj platformy domyślną konwencję wywoływania. Na przykład na Windows wartość domyślna to `StdCall` i na Windows CE .NET jest `Cdecl`.|  
|`pmCallConvCdecl`|Użyj `Cdecl` konwencji wywoływania. W tym przypadku obiekt wywołujący czyści stos. Dzięki temu wywoływania funkcji z `varargs` (oznacza to, funkcje, które przyjmują zmienną liczbę parametrów).|  
|`pmCallConvStdcall`|Użyj `StdCall` konwencji wywoływania. W tym przypadku wywoływany obiekt czyści stos. To jest domyślna konwencja wywoływania niezarządzanych przy użyciu platformy wywołają procedurę obsługi.|  
|`pmCallConvThiscall`|Użyj `ThisCall` konwencji wywoływania. W tym przypadku jest pierwszym parametrem `this` wskaźnika i jest przechowywany w rejestrze ECX. Inne parametry są przekazywane na stosie. `ThisCall` Konwencji wywoływania służy do wywoływania metod w klasach wyeksportowane z niezarządzaną biblioteką DLL.|  
|`pmCallConvFastcall`|Zastrzeżone.|  
|`pmMaxValue`|Zastrzeżone.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
