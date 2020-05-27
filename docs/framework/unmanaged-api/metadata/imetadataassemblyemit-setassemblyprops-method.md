---
title: IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetAssemblyProps
helpviewer_keywords:
- SetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetAssemblyProps method [.NET Framework metadata]
ms.assetid: 91b633d7-9e75-43c3-a8d2-2144984e5f9e
topic_type:
- apiref
ms.openlocfilehash: 7c6adcbcfe64f63048078b4ccba6727a58531033
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008108"
---
# <a name="imetadataassemblyemitsetassemblyprops-method"></a>IMetaDataAssemblyEmit::SetAssemblyProps — Metoda
Modyfikuje określoną `Assembly` strukturę metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAssemblyProps (  
    [in] mdAssembly               pma,  
    [in] const void               *pbPublicKey,  
    [in] ULONG                    cbPublicKey,  
    [in] ULONG                    ulHashAlgId,  
    [in] LPCWSTR                  szName,  
    [in] const ASSEMBLYMETADATA   *pMetaData,  
    [in] DWORD                    dwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pma`  
 podczas Token metadanych określający `Assembly` strukturę metadanych, która ma zostać zmodyfikowana.  
  
 `pbPublicKey`  
 podczas Wskaźnik do klucza publicznego wydawcy zestawu.  
  
 `cbPublicKey`  
 podczas Rozmiar w bajtach `pbPublicKey` .  
  
 `ulHashAlgId`  
 podczas Identyfikator algorytmu wyznaczania wartości skrótu używany do mieszania plików zestawu.  
  
 `szName`  
 podczas Nazwa tekstu do odczytania przez człowieka.  
  
 `pMetaData`  
 podczas Wskaźnik do ASSEMBLYMETADATA, który zawiera wersję, platformę i informacje o ustawieniach regionalnych dla zestawu.  
  
 `dwAssemblyFlags`  
 podczas Bitowa kombinacja wartości [AssemblyFlags —](assemblyflags-enumeration.md) , które określają różne atrybuty zestawu.  
  
## <a name="remarks"></a>Uwagi  
 Aby utworzyć `Assembly` strukturę metadanych, użyj metody [IMetaDataAssemblyEmit::D efineassembly](imetadataassemblyemit-defineassembly-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataAssemblyEmit — Interfejs](imetadataassemblyemit-interface.md)
