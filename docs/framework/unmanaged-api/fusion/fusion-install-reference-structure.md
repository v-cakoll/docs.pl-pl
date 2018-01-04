---
title: "FUSION_INSTALL_REFERENCE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FUSION_INSTALL_REFERENCE
api_location: fusion.dll
api_type: COM
f1_keywords: FUSION_INSTALL_REFERENCE
helpviewer_keywords: FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36321606fe208233fb6114fe9568b655f0e1b400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE — Struktura
Reprezentuje odwołanie, które umożliwia aplikacji z zestawem aplikacji został zainstalowany w globalnej pamięci podręcznej zestawów.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`cbSize`|Rozmiar struktury w bajtach.|  
|`dwFlags`|Zarezerwowane dla przyszłego rozszerzalności. Ta wartość musi być 0 (zero).|  
|`guidScheme`|Jednostka, która dodaje odwołanie. To pole może mieć jedną z następujących wartości:<br /><br /> -FUSION_REFCOUNT_MSI_GUID: Zestaw jest wywoływany przez aplikację, która została zainstalowana przy użyciu Instalatora systemu Microsoft Windows. `szIdentifier` Pole jest ustawione na `MSI`i `szNonCanonicalData` pole jest ustawione na `Windows Installer`. Ten schemat jest używany dla zestawów side-by-side systemu Windows.<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID: Zestaw jest przywoływany przez aplikację, która jest wyświetlana w **Dodaj lub usuń programy** interfejsu. `szIdentifier` Pole zawiera token, który rejestruje aplikację z **Dodaj lub usuń programy** interfejsu.<br />-FUSION_REFCOUNT_FILEPATH_GUID: Zestaw jest wywoływany przez aplikację, która jest reprezentowana przez pliki w systemie plików. `szIdentifier` Pole zawiera ścieżkę do tego pliku.<br />-FUSION_REFCOUNT_OPAQUE_STRING_GUID: Zestaw jest wywoływany przez aplikację, która odpowiada tylko ciąg z ogólnym opisem. `szIdentifier` Pole zawiera ten ciąg z ogólnym opisem. Globalna pamięć podręczna zestawów nie sprawdza istnienie odwołania nieprzezroczyste, po usunięciu tej wartości.<br />-FUSION_REFCOUNT_OSINSTALL_GUID: Ta wartość jest zastrzeżona.|  
|`szIdentifier`|Unikatowy ciąg, który identyfikuje aplikację, zainstalowanym zestawu w globalnej pamięci podręcznej zestawów. Wartość zależy od wartości `guidScheme` pola.|  
|`szNonCanonicalData`|Ciąg, który jest rozpoznawany tylko przez jednostki, która dodaje odwołanie. Globalna pamięć podręczna zestawów przechowuje ten ciąg, ale nie używa ich.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Fusion.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Łączenie — struktury](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
 [Global Assembly Cache](../../../../docs/framework/app-domains/gac.md)
