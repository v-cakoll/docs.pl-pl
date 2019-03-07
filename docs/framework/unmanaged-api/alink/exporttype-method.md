---
title: ExportType — Metoda
ms.date: 03/30/2017
api_name:
- IALink.ExportType
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportType
helpviewer_keywords:
- ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a63a72eca636113ec5b339172a89441f3afdb092
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475752"
---
# <a name="exporttype-method"></a><span data-ttu-id="6155f-102">ExportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="6155f-102">ExportType Method</span></span>
<span data-ttu-id="6155f-103">Określa, że typ jest eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="6155f-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6155f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6155f-104">Syntax</span></span>  
  
```  
HRESULT ExportType(  
    mdAssembly      AssemblyID,  
    mdToken         FileToken,  
    mdTypeDef       TypeToken,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6155f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6155f-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6155f-106">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="6155f-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6155f-107">Plik tokenu lub zestawu identyfikator pliku, który definiuje typ możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="6155f-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="6155f-108">Token typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="6155f-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="6155f-109">W pełni kwalifikowana nazwa typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="6155f-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="6155f-110">`ComType` flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="6155f-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="6155f-111">Ten parametr może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="6155f-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="6155f-112">Odbiera token dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="6155f-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6155f-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6155f-113">Return Value</span></span>  
 <span data-ttu-id="6155f-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6155f-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6155f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6155f-115">Requirements</span></span>  
 <span data-ttu-id="6155f-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="6155f-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6155f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6155f-117">See also</span></span>
- [<span data-ttu-id="6155f-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6155f-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6155f-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="6155f-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6155f-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6155f-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
