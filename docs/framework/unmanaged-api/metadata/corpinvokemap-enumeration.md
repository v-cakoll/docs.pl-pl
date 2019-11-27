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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441562"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap — Wyliczenie
Określa opcje wywołania PInvoke.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pmNoMangle`|Użyj każdej nazwy elementu członkowskiego w określony sposób.|  
|`pmCharSetMask`|Rezerwacj.|  
|`pmCharSetNotSpec`|Rezerwacj.|  
|`pmCharSetAnsi`|Kierowanie ciągów jako ciągów znaków wielobajtowych.|  
|`pmCharSetUnicode`|Kierowanie ciągów jako znaków Unicode 2-bajtowych.|  
|`pmCharSetAuto`|Automatyczne kierowanie ciągów odpowiednio dla docelowego systemu operacyjnego. Wartość domyślna to Unicode w systemie Windows NT, Windows 2000, Windows XP i rodziny Windows Server 2003. wartość domyślna to ANSI w systemach Windows 98 i Windows Me.|  
|`pmBestFitUseAssem`|Rezerwacj.|  
|`pmBestFitEnabled`|Wykonaj najlepiej dopasowane mapowanie znaków Unicode, które nie mają dokładnego dopasowania w zestawie znaków ANSI.|  
|`pmBestFitDisabled`|Nie wykonuj najlepszego mapowania znaków Unicode. W takim przypadku wszystkie znaki napotkano zostaną zastąpione "?".|  
|`pmBestFitMask`|Rezerwacj.|  
|`pmThrowOnUnmappableCharUseAssem`|Rezerwacj.|  
|`pmThrowOnUnmappableCharEnabled`|Zgłoś wyjątek, gdy organizator międzyoperacyjny napotka znak napotkano.|  
|`pmThrowOnUnmappableCharDisabled`|Nie zgłaszaj wyjątku, gdy organizator międzyoperacyjny napotka znak napotkano.|  
|`pmThrowOnUnmappableCharMask`|Zarezerwowany|  
|`pmSupportsLastError`|Zezwalaj wywołującemu na wywoływanie funkcji Win32 `SetLastError` przed powrotem z metody z atrybutem.|  
|`pmCallConvMask`|Zarezerwowany|  
|`pmCallConvWinapi`|Użyj domyślnej konwencji wywoływania platformy. Na przykład w systemie Windows wartość domyślna to `StdCall` i Windows CE .NET `Cdecl`.|  
|`pmCallConvCdecl`|Użyj konwencji wywoływania `Cdecl`. W takim przypadku wywołujący czyści stos. Umożliwia to wywoływanie funkcji z `varargs` (to jest funkcja, która akceptuje zmienną liczbę parametrów).|  
|`pmCallConvStdcall`|Użyj konwencji wywoływania `StdCall`. W takim przypadku wywoływany czyści stos. Jest to domyślna konwencja wywoływania funkcji niezarządzanych przy użyciu wywołania platformy.|  
|`pmCallConvThiscall`|Użyj konwencji wywoływania `ThisCall`. W tym przypadku pierwszy parametr jest `this` wskaźnikiem i jest przechowywany w rejestrze ECX. Inne parametry są wypychane na stosie. Konwencja wywoływania `ThisCall` jest używana do wywoływania metod w klasach wyeksportowanych z niezarządzanej biblioteki DLL.|  
|`pmCallConvFastcall`|Rezerwacj.|  
|`pmMaxValue`|Rezerwacj.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
