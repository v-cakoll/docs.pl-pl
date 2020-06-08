---
title: IMetaDataImport::GetPermissionSetProps — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 54c75156c32e5b40aa933ef6530b2cc33edf7de4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490994"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="c1809-102">IMetaDataImport::GetPermissionSetProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1809-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="c1809-103">Pobiera metadane skojarzone z <xref:System.Security.PermissionSet?displayProperty=nameWithType> reprezentowane przez określony token uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="c1809-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1809-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1809-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1809-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1809-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="c1809-106">podczas Token metadanych uprawnienia, który reprezentuje zestaw uprawnień do pobierania właściwości metadanych.</span><span class="sxs-lookup"><span data-stu-id="c1809-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="c1809-107">określoną Wskaźnik do zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c1809-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="c1809-108">określoną Wskaźnik do binarnego podpisu metadanych zestawu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="c1809-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="c1809-109">określoną Rozmiar w bajtach `ppvPermission` .</span><span class="sxs-lookup"><span data-stu-id="c1809-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1809-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1809-110">Requirements</span></span>  
 <span data-ttu-id="c1809-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1809-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1809-112">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c1809-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c1809-113">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c1809-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c1809-114">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1809-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1809-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1809-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="c1809-116">IMetaDataImport — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c1809-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c1809-117">IMetaDataImport2, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1809-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
