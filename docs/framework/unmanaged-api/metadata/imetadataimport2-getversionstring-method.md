---
title: "IMetaDataImport2::GetVersionString — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetVersionString
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d08f43a790305c960d557064539de680a2d04af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="1f09e-102">IMetaDataImport2::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f09e-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="1f09e-103">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do budowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="1f09e-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f09e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f09e-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f09e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f09e-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="1f09e-106">[out] Tablica do przechowywania ciąg, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="1f09e-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="1f09e-107">[in] Rozmiar w znaki dwubajtowe z `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f09e-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="1f09e-108">[out] Liczba znaki dwubajtowe, włącznie z terminatorem null, jest zwracany w `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f09e-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f09e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f09e-109">Remarks</span></span>  
 <span data-ttu-id="1f09e-110">`GetVersionString` Metoda pobiera wersję skompilowany dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="1f09e-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="1f09e-111">Jeśli nigdy nie został zapisany zakresu, nie będzie miała skompilowany dla wersji i zostanie zwrócony pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="1f09e-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f09e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f09e-112">Requirements</span></span>  
 <span data-ttu-id="1f09e-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f09e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f09e-114">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="1f09e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1f09e-115">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f09e-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1f09e-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f09e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f09e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f09e-117">See Also</span></span>  
 [<span data-ttu-id="1f09e-118">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f09e-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="1f09e-119">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f09e-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
