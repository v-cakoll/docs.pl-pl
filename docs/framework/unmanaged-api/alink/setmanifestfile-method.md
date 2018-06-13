---
title: SetManifestFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f8398c16b27836b772e8ac56ee1f7e8494f4be0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403572"
---
# <a name="setmanifestfile-method"></a>SetManifestFile — Metoda
Pozwala określić lub zresetować plik manifestu podczas tworzenia zestawu używa konsolidator.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Nazwa pliku manifestu, których zawartość są umieszczane w obiekcie blob zasobów Win32.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj ten element przed żądaniem Win32ResBlob. Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest do odczytu i umieść w zasobów Win32 o identyfikatorze RT_MANIFEST. Po wywołaniu za pomocą parametru o wartości NULL, wszystkie wcześniej odczytu manifestu jest wyczyszczone. Dzięki temu jeden do zresetowania stanu konsolidator niż czas inicjowania.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga aLink.h  
  
## <a name="see-also"></a>Zobacz też  
 [IALink3, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)  
 [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)  
 [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
