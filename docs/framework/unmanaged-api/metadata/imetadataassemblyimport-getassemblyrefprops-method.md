---
title: IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 9aef471c1155070af0e9bcca14975a65bc5dc763
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175970"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="f1eb7-102">IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="f1eb7-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="f1eb7-103">Pobiera zestaw właściwości dla odwołania do zestawu z określonym podpisem metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1eb7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1eb7-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="f1eb7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f1eb7-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="f1eb7-106">[w] Token `mdAssemblyRef` metadanych, który reprezentuje odwołanie do zestawu, dla którego mają zostać właściwości.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="f1eb7-107">[na zewnątrz] Wskaźnik do klucza publicznego lub tokenu metadanych.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="f1eb7-108">[na zewnątrz] Liczba bajtów w zwróconym kluczu publicznym lub tokenie.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="f1eb7-109">[na zewnątrz] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="f1eb7-110">[w] Rozmiar, w szerokich znaków, z `szName`.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="f1eb7-111">[na zewnątrz] Wskaźnik do liczby szerokich znaków rzeczywiście `szName`zwrócony w .</span><span class="sxs-lookup"><span data-stu-id="f1eb7-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="f1eb7-112">[na zewnątrz] Wskaźnik do ASSEMBLYMETADATA struktury, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="f1eb7-113">[na zewnątrz] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="f1eb7-114">Jest to skrót, przy użyciu algorytmu `PublicKey` SHA-1 właściwości zestawu, do którego odwołuje się, chyba że arfFullOriginator flagi [AssemblyRefFlags wyliczenia](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="f1eb7-115">[na zewnątrz] Liczba znaków szerokich w zwróconej wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="f1eb7-116">[na zewnątrz] Wskaźnik do flag, które opisują metadane zastosowane do zestawu.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="f1eb7-117">Wartość flag jest kombinacją jednej lub więcej wartości [CorAssemblyFlags.](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="f1eb7-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1eb7-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f1eb7-118">Return Value</span></span>  
 <span data-ttu-id="f1eb7-119">Ta metoda zwraca S_OK, jeśli zakończy się pomyślnie; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1eb7-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f1eb7-120">Requirements</span></span>  
 <span data-ttu-id="f1eb7-121">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1eb7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1eb7-122">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="f1eb7-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1eb7-123">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f1eb7-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1eb7-124">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1eb7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1eb7-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1eb7-125">See also</span></span>

- [<span data-ttu-id="f1eb7-126">IMetaDataAssemblyImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f1eb7-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
