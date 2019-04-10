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
ms.openlocfilehash: 95ff27143453e7772b4a463fa66ca039bbb715fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226920"
---
# <a name="exporttype-method"></a><span data-ttu-id="fe0ca-102">ExportType — Metoda</span><span class="sxs-lookup"><span data-stu-id="fe0ca-102">ExportType Method</span></span>
<span data-ttu-id="fe0ca-103">Określa, że typ jest eksportowalny.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-103">Specifies that a type is exportable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe0ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fe0ca-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="fe0ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fe0ca-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="fe0ca-106">Identyfikator zestawu, aby wyeksportować z.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-106">ID of the assembly to export from.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="fe0ca-107">Plik tokenu lub zestawu identyfikator pliku, który definiuje typ możliwy do eksportu.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-107">File token or assembly ID of file that defines the exportable type.</span></span>  
  
 `TypeToken`  
 <span data-ttu-id="fe0ca-108">Token typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-108">Token of type to be made exportable.</span></span>  
  
 `pszTypename`  
 <span data-ttu-id="fe0ca-109">W pełni kwalifikowana nazwa typu ma zostać wykonane można eksportować.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-109">Fully qualified type name to be made exportable.</span></span>  
  
 `dwFlags`  
 `ComType` <span data-ttu-id="fe0ca-110">flagi, takich jak `tdPublic` lub `tdNested`.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-110">flags such as `tdPublic` or `tdNested`.</span></span> <span data-ttu-id="fe0ca-111">Ten parametr może być przekazana do [defineexportedtype — metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span><span class="sxs-lookup"><span data-stu-id="fe0ca-111">This parameter may be passed to [DefineExportedType Method](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineexportedtype-method.md).</span></span>  
  
 `pType`  
 <span data-ttu-id="fe0ca-112">Odbiera token dla eksportowanego typu.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-112">Receives token for exported type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe0ca-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fe0ca-113">Return Value</span></span>  
 <span data-ttu-id="fe0ca-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="fe0ca-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe0ca-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fe0ca-115">Requirements</span></span>  
 <span data-ttu-id="fe0ca-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="fe0ca-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0ca-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe0ca-117">See also</span></span>

- [<span data-ttu-id="fe0ca-118">IALink — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fe0ca-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="fe0ca-119">IALink2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fe0ca-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="fe0ca-120">ALink — interfejs API</span><span class="sxs-lookup"><span data-stu-id="fe0ca-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
