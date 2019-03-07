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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4c7ef2beca06713c04c7e0f8e30a47b884bf5c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486293"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="23c5c-102">IMetaDataImport2::GetVersionString — Metoda</span><span class="sxs-lookup"><span data-stu-id="23c5c-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="23c5c-103">Pobiera numer wersji środowiska uruchomieniowego, który został użyty do tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="23c5c-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c5c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23c5c-104">Syntax</span></span>  
  
```  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23c5c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="23c5c-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="23c5c-106">[out] Tablica do przechowywania ciąg, który określa numer wersji.</span><span class="sxs-lookup"><span data-stu-id="23c5c-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="23c5c-107">[in] Rozmiar w szerokich znaków z `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="23c5c-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="23c5c-108">[out] Liczba znaków dwubajtowych, łącznie z terminatorem null, jest zwracany w `pwzBuf` tablicy.</span><span class="sxs-lookup"><span data-stu-id="23c5c-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23c5c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23c5c-109">Remarks</span></span>  
 <span data-ttu-id="23c5c-110">`GetVersionString` Metoda pobiera wersję utworzone dla bieżącego zakresu metadanych.</span><span class="sxs-lookup"><span data-stu-id="23c5c-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="23c5c-111">Jeśli nigdy nie został zapisany zakresu, nie zostaną utworzone dla wersji i zostanie zwrócony pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="23c5c-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23c5c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="23c5c-112">Requirements</span></span>  
 <span data-ttu-id="23c5c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23c5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c5c-114">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="23c5c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="23c5c-115">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="23c5c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="23c5c-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c5c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23c5c-117">See also</span></span>
- [<span data-ttu-id="23c5c-118">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="23c5c-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="23c5c-119">IMetaDataImport, interfejs</span><span class="sxs-lookup"><span data-stu-id="23c5c-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
