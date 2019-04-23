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
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072431"
---
# <a name="setmanifestfile-method"></a>SetManifestFile — Metoda
Pozwala na określenie lub zresetowania pliku manifestu, który konsolidator używa podczas tworzenia zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Nazwa pliku manifestu, którego zawartość są umieszczane w obiekcie blob zasobów Win32.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.  
  
## <a name="remarks"></a>Uwagi  
 Połączenie się z tym przed żądaniem Win32ResBlob. Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest odczytać i umieścić w zasoby Win32, za pomocą Identyfikatora RT_MANIFEST. Gdy zostanie wywołana przy użyciu parametru o wartości NULL, jest wyczyszczone wszelkie wcześniej odczytu manifestu. Dzięki temu jeden do zresetowania stanu konsolidator do tego czasu inicjowania.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga aLink.h  
  
## <a name="see-also"></a>Zobacz także

- [IALink3, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [ALink, interfejs API](../../../../docs/framework/unmanaged-api/alink/index.md)
- [IALink, interfejs](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [Al.exe (konsolidator zestawów)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
