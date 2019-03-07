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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 471f4837ff8aee725020f52c09a57d8f3652013c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489869"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="ec066-102">IMetaDataAssemblyImport::GetAssemblyRefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="ec066-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>
<span data-ttu-id="ec066-103">Pobiera zbiór właściwości odwołanie do zestawu za pomocą podpisu określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="ec066-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec066-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec066-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ec066-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ec066-105">Parameters</span></span>  
 `mdar`  
 <span data-ttu-id="ec066-106">[in] `mdAssemblyRef` Token metadanych, który reprezentuje odwołanie do zestawu dla którego należy pobrać właściwości.</span><span class="sxs-lookup"><span data-stu-id="ec066-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="ec066-107">[out] Wskaźnik do tokenu metadanych lub klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="ec066-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="ec066-108">[out] Liczba bajtów zwróconych publicznego klucza lub tokenu.</span><span class="sxs-lookup"><span data-stu-id="ec066-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="ec066-109">[out] Prosta nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec066-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="ec066-110">[in] Rozmiar w szerokie znaki z `szName`.</span><span class="sxs-lookup"><span data-stu-id="ec066-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="ec066-111">[out] Wskaźnik do liczby szerokie znaki rzeczywistego zwrotu w `szName`.</span><span class="sxs-lookup"><span data-stu-id="ec066-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="ec066-112">[out] Wskaźnik do assemblymetadata — struktura, która zawiera metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec066-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="ec066-113">[out] Wskaźnik do wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ec066-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="ec066-114">Jest to skrót, przy użyciu algorytmu SHA-1 z `PublicKey` właściwości zestawu, do którego nastąpiło odwołanie, chyba że flagę arfFullOriginator [assemblyrefflags —](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) ma ustawioną wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="ec066-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="ec066-115">[out] Liczba szerokie znaki w wartości zwracane wyznaczania wartości skrótu.</span><span class="sxs-lookup"><span data-stu-id="ec066-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="ec066-116">[out] Wskaźnik flagi, które opisują metadane zastosowany do zestawu.</span><span class="sxs-lookup"><span data-stu-id="ec066-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="ec066-117">Wartość flagi składa się z co najmniej jeden [corassemblyflags —](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) wartości.</span><span class="sxs-lookup"><span data-stu-id="ec066-117">The flags value is a combination of one or more [CorAssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec066-118">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="ec066-118">Return Value</span></span>  
 <span data-ttu-id="ec066-119">Ta metoda zwraca wartość S_OK, jeśli się powiedzie; w przeciwnym razie zwraca jeden z kodów błędów zdefiniowanych w pliku nagłówka w pliku Winerror.h.</span><span class="sxs-lookup"><span data-stu-id="ec066-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec066-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec066-120">Requirements</span></span>  
 <span data-ttu-id="ec066-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec066-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec066-122">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ec066-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec066-123">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec066-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec066-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec066-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec066-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec066-125">See also</span></span>
- [<span data-ttu-id="ec066-126">IMetaDataAssemblyImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec066-126">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
