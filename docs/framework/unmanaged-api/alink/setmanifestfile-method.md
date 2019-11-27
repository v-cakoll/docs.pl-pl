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
ms.openlocfilehash: df97f4c37d8f335ce183685debd7c0933be910ed
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445563"
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
  
## <a name="return-value"></a>Wartość zwrócona  
 Zwraca S_OK, jeśli metoda zakończy się pomyślnie.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj to przed pytaniem o Win32ResBlob. Wartość parametru `pszFile` jest nazwą pliku manifestu, którego zawartość jest odczytywana i umieszczana w zasobach Win32 z IDENTYFIKATORem RT_MANIFEST. Gdy wywoływana przy użyciu parametru o wartości NULL, każdy poprzednio odczytany manifest jest czyszczony. Umożliwia to jednemu resetowaniu stanu konsolidatora do czasu inicjacji.  
  
## <a name="requirements"></a>Wymagania  
 Wymaga aLink. h  
  
## <a name="see-also"></a>Zobacz także

- [IALink3, interfejs](ialink3-interface.md)
- [ALink, interfejs API](index.md)
- [IALink, interfejs](ialink-interface.md)
- [Al.exe (konsolidator zestawów)](../../tools/al-exe-assembly-linker.md)
