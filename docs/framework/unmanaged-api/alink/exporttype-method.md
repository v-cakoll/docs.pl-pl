---
title: "ExportType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ExportType
api_location: alink.dll
api_type: COM
f1_keywords: ExportType
helpviewer_keywords: ExportType method
ms.assetid: 91a7ce63-f5b8-4f16-b2c4-e1d0baa88944
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f9cc61d0bc32545b486f4472904b17ed0b59526e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exporttype-method"></a><span data-ttu-id="f0f4b-102">ExportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="f0f4b-102">ExportType Method</span></span>
<span data-ttu-id="f0f4b-103">Określa, że typ jest możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0f4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0f4b-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="f0f4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0f4b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f0f4b-106">Identyfikator zestawu eksportu.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f0f4b-107">Identyfikator tokenu lub zestawu pliku, który definiuje typ możliwy do eksportu pliku.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="f0f4b-108">Token typu ma zostać wykonane eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="f0f4b-109">Pełni kwalifikowana nazwa typu ma zostać wykonane eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f0f4b-110">`ComType`flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-110">`ComType` flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="f0f4b-111">Ten parametr może być przekazana do [DefineExportedType — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="f0f4b-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="f0f4b-112">Odbiera token dla wyeksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0f4b-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f0f4b-113">Return Value</span></span>  
 <span data-ttu-id="f0f4b-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f0f4b-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0f4b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0f4b-115">Requirements</span></span>  
 <span data-ttu-id="f0f4b-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="f0f4b-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0f4b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0f4b-117">See Also</span></span>  
 [<span data-ttu-id="f0f4b-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0f4b-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f0f4b-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0f4b-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f0f4b-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="f0f4b-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
