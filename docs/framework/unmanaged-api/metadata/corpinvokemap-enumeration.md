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
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176152"
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
|`pmNoMangle`|Użyj każdej nazwy elementu członkowskiego, jak określono.|  
|`pmCharSetMask`|Zarezerwowany.|  
|`pmCharSetNotSpec`|Zarezerwowany.|  
|`pmCharSetAnsi`|Ciągi marshal jako ciągi znaków wielo bajtów.|  
|`pmCharSetUnicode`|Ciągi marshaljako 2-bajtowe znaki Unicode.|  
|`pmCharSetAuto`|Automatycznie marshal ciągi odpowiednio dla docelowego systemu operacyjnego. Domyślnie jest to Unicode w systemach Windows NT, Windows 2000, Windows XP i Windows Server 2003; domyślnie jest ANSI w systemie Windows 98 i Windows Me.|  
|`pmBestFitUseAssem`|Zarezerwowany.|  
|`pmBestFitEnabled`|Wykonaj najlepsze mapowanie znaków Unicode, które nie mają dokładnego dopasowania w zestawie znaków ANSI.|  
|`pmBestFitDisabled`|Nie należy wykonywać najkosztowanego mapowania znaków Unicode. W takim przypadku wszystkie znaki, które nie można zastosować, zostaną zastąpione przez '?'.|  
|`pmBestFitMask`|Zarezerwowany.|  
|`pmThrowOnUnmappableCharUseAssem`|Zarezerwowany.|  
|`pmThrowOnUnmappableCharEnabled`|Zgłosić wyjątek, gdy organizator międzyoperacyjny napotka znak niezadający do aplikacji.|  
|`pmThrowOnUnmappableCharDisabled`|Nie zgłaszaj wyjątku, gdy organizator międzyoperacyjny napotka znak niemożna zastosować.|  
|`pmThrowOnUnmappableCharMask`|Zarezerwowano|  
|`pmSupportsLastError`|Zezwalaj wywołującemu na wywołanie `SetLastError` funkcji Win32 przed zwróceniem z przypisanej metody.|  
|`pmCallConvMask`|Zarezerwowano|  
|`pmCallConvWinapi`|Użyj domyślnej konwencji wywoływania platformy. Na przykład w systemie `StdCall` Windows domyślny jest i `Cdecl`w systemie Windows CE .NET jest .|  
|`pmCallConvCdecl`|Użyj `Cdecl` konwencji wywoływania. W takim przypadku obiektu wywołującego czyści stosu. Umożliwia to wywoływanie funkcji z `varargs` (czyli funkcje, które akceptują zmienną liczbę parametrów).|  
|`pmCallConvStdcall`|Użyj `StdCall` konwencji wywoływania. W takim przypadku wywoływany czyści stosu. Jest to domyślna konwencja wywoływania niezarządzanych funkcji za pomocą wywołania platformy.|  
|`pmCallConvThiscall`|Użyj `ThisCall` konwencji wywoływania. W takim przypadku pierwszym parametrem `this` jest wskaźnik i jest przechowywany w rejestrze ECX. Inne parametry są wypychane na stosie. Konwencja wywołująca `ThisCall` jest używana do wywoływania metod na klasy eksportowane z biblioteki DLL niezarządzanej.|  
|`pmCallConvFastcall`|Zarezerwowany.|  
|`pmMaxValue`|Zarezerwowany.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
