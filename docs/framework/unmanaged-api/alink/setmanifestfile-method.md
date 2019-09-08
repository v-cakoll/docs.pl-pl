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
ms.openlocfilehash: b293c30060107d18c6b609efc82c4128a73cc1c7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787208"
---
# <a name="setmanifestfile-method"></a>SetManifestFile — Metoda
Umożliwia określenie lub zresetowanie pliku manifestu używanego przez konsolidatora podczas tworzenia zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszFile`  
  
 Nazwa pliku manifestu, którego zawartość jest umieszczana w obiekcie blob zasobów Win32.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj to przed pytaniem o Win32ResBlob. Wartość `pszFile` parametru jest nazwą pliku manifestu, którego zawartość jest odczytywana i umieszczana w zasobach Win32 o identyfikatorze RT_MANIFEST. Gdy wywoływana przy użyciu parametru o wartości NULL, każdy poprzednio odczytany manifest jest czyszczony. Umożliwia to jednemu resetowaniu stanu konsolidatora do czasu inicjacji.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga aLink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink3, interfejs](ialink3-interface.md)
- [ALink, interfejs API](index.md)
- [IALink, interfejs](ialink-interface.md)
- [Al.exe (konsolidator zestawów)](../../tools/al-exe-assembly-linker.md)
