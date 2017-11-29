---
title: "IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyRefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9159352c4f7f338c6b9b82ea579ad3cb36c19007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="a38be-102">IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="a38be-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="a38be-103">Pobiera zbiór właściwości dla odwołania do zestawu o sygnaturze określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="a38be-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a38be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a38be-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,   
    [out] const void          **ppbPublicKeyOrToken,   
    [out] ULONG                *pcbPublicKeyOrToken,   
    [out] LPWSTR               szName,   
    [in]  ULONG                cchName,   
    [out] ULONG                *pchName,   
    [out] ASSEMBLYMETADATA     *pMetaData,   
    [out] const void           **ppbHashValue,   
    [out] ULONG                *pcbHashValue,   
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a38be-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a38be-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="a38be-106">[in] `mdAssemblyRef` Token metadanych, który reprezentuje odwołanie do zestawu, do którego można pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="a38be-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="a38be-107">[out] Wskaźnik do klucza publicznego lub token metadanych.</span><span class="sxs-lookup"><span data-stu-id="a38be-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="a38be-108">[out] Liczba bajtów zwróconych publiczny klucza lub tokenu.</span><span class="sxs-lookup"><span data-stu-id="a38be-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="a38be-109">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="a38be-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a38be-110">[in] Rozmiar w znaki dwubajtowe z `szName`.</span><span class="sxs-lookup"><span data-stu-id="a38be-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a38be-111">[out] Wskaźnik do liczby znaki dwubajtowe faktycznie zwracane w `szName`.</span><span class="sxs-lookup"><span data-stu-id="a38be-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="a38be-112">[out] Wskaźnik do struktury assemblymetadata — zawierający metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="a38be-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="a38be-113">[out] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a38be-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="a38be-114">Jest to wartość skrótu, za pomocą algorytmu SHA-1, z `PublicKey` właściwości zestawu, do którego nastąpiło odwołanie, chyba że arfFullOriginator flagę [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) wyliczenie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="a38be-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="a38be-115">[out] Liczba szerokości znaków w wartości zwracane wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="a38be-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="a38be-116">[out] Wskaźnik do flagi opisujące metadanych zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="a38be-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="a38be-117">Wartość flagi składa się z co najmniej jeden [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="a38be-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a38be-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a38be-118">Return Value</span></span>  
 <span data-ttu-id="a38be-119">Ten — metoda zwraca wartość S_OK w razie powodzenia; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka pliku Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="a38be-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a38be-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a38be-120">Requirements</span></span>  
 <span data-ttu-id="a38be-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a38be-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a38be-122">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a38be-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a38be-123">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a38be-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a38be-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a38be-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a38be-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a38be-125">See Also</span></span>  
 [<span data-ttu-id="a38be-126">IMetaDataAssemblyImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="a38be-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
