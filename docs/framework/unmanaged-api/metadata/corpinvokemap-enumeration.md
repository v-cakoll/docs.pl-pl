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
ms.openlocfilehash: 199a649b0481c2a740926636345eefbda6831ef2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007549"
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`pmNoMangle`|Użyj każdej nazwy elementu członkowskiego w określony sposób.|  
|`pmCharSetMask`|Zarezerwowany.|  
|`pmCharSetNotSpec`|Zarezerwowany.|  
|`pmCharSetAnsi`|Kierowanie ciągów jako ciągów znaków wielobajtowych.|  
|`pmCharSetUnicode`|Kierowanie ciągów jako znaków Unicode 2-bajtowych.|  
|`pmCharSetAuto`|Automatyczne kierowanie ciągów odpowiednio dla docelowego systemu operacyjnego. Wartość domyślna to Unicode w systemie Windows NT, Windows 2000, Windows XP i rodziny Windows Server 2003. wartość domyślna to ANSI w systemach Windows 98 i Windows Me.|  
|`pmBestFitUseAssem`|Zarezerwowany.|  
|`pmBestFitEnabled`|Wykonaj najlepiej dopasowane mapowanie znaków Unicode, które nie mają dokładnego dopasowania w zestawie znaków ANSI.|  
|`pmBestFitDisabled`|Nie wykonuj najlepszego mapowania znaków Unicode. W takim przypadku wszystkie znaki napotkano zostaną zastąpione "?".|  
|`pmBestFitMask`|Zarezerwowany.|  
|`pmThrowOnUnmappableCharUseAssem`|Zarezerwowany.|  
|`pmThrowOnUnmappableCharEnabled`|Zgłoś wyjątek, gdy organizator międzyoperacyjny napotka znak napotkano.|  
|`pmThrowOnUnmappableCharDisabled`|Nie zgłaszaj wyjątku, gdy organizator międzyoperacyjny napotka znak napotkano.|  
|`pmThrowOnUnmappableCharMask`|Zarezerwowano|  
|`pmSupportsLastError`|Zezwalaj wywołującemu na wywoływanie `SetLastError` funkcji Win32 przed powrotem z metody z atrybutem.|  
|`pmCallConvMask`|Zarezerwowano|  
|`pmCallConvWinapi`|Użyj domyślnej konwencji wywoływania platformy. Na przykład w systemie Windows jest to ustawienie domyślne `StdCall` i na Windows CE .NET `Cdecl` .|  
|`pmCallConvCdecl`|Użyj `Cdecl` konwencji wywoływania. W takim przypadku wywołujący czyści stos. Umożliwia to wywoływanie funkcji za pomocą `varargs` (czyli funkcji, które akceptują zmienną liczbę parametrów).|  
|`pmCallConvStdcall`|Użyj `StdCall` konwencji wywoływania. W takim przypadku wywoływany czyści stos. Jest to domyślna konwencja wywoływania funkcji niezarządzanych przy użyciu wywołania platformy.|  
|`pmCallConvThiscall`|Użyj `ThisCall` konwencji wywoływania. W tym przypadku pierwszy parametr jest `this` wskaźnikiem i jest przechowywany w rejestrze ECX. Inne parametry są wypychane na stosie. `ThisCall`Konwencja wywoływania jest używana do wywoływania metod w klasach wyeksportowanych z niezarządzanej biblioteki DLL.|  
|`pmCallConvFastcall`|Zarezerwowany.|  
|`pmMaxValue`|Zarezerwowany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
