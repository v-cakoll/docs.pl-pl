---
title: IMetaDataImport2::GetVersionString — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 84cf5ac9eab5749d3bdc63670fe5c31bfb62abcd
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490410"
---
# <a name="imetadataimport2getversionstring-method"></a>IMetaDataImport2::GetVersionString — Metoda
Pobiera numer wersji środowiska uruchomieniowego, który został użyty do skompilowania zestawu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuf`  
 określoną Tablica do przechowywania ciągu, który określa wersję.  
  
 `ccBufSize`  
 podczas Rozmiar, w postaci dwubajtowej `pwzBuf` tablicy.  
  
 `pccBufSize`  
 określoną Liczba znaków dwubajtowych, łącznie z terminatorem wartości null, zwracana w `pwzBuf` tablicy.  
  
## <a name="remarks"></a>Uwagi  
 `GetVersionString`Metoda pobiera wbudowaną wersję bieżącego zakresu metadanych. Jeśli zakres nigdy nie został zapisany, nie będzie miał wbudowanej wersji i zostanie zwrócony pusty ciąg.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IMetaDataImport2, interfejs](imetadataimport2-interface.md)
- [IMetaDataImport — Interfejs](imetadataimport-interface.md)
