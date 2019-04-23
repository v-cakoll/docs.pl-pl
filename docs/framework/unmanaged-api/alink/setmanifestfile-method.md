---
title: SetManifestFile — Metoda
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8307960166cfc668a577431d688c439f0f794be2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072431"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="6d963-102">SetManifestFile — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d963-102">SetManifestFile Method</span></span>
<span data-ttu-id="6d963-103">Pozwala na określenie lub zresetowania pliku manifestu, który konsolidator używa podczas tworzenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="6d963-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d963-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d963-104">Syntax</span></span>  
  
```  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d963-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d963-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="6d963-106">Nazwa pliku manifestu, którego zawartość są umieszczane w obiekcie blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="6d963-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d963-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6d963-107">Return Value</span></span>  
 <span data-ttu-id="6d963-108">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="6d963-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d963-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d963-109">Remarks</span></span>  
 <span data-ttu-id="6d963-110">Połączenie się z tym przed żądaniem Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="6d963-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="6d963-111">Wartość `pszFile` parametr jest nazwą pliku manifestu, których zawartość jest odczytać i umieścić w zasoby Win32, za pomocą Identyfikatora RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="6d963-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="6d963-112">Gdy zostanie wywołana przy użyciu parametru o wartości NULL, jest wyczyszczone wszelkie wcześniej odczytu manifestu.</span><span class="sxs-lookup"><span data-stu-id="6d963-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="6d963-113">Dzięki temu jeden do zresetowania stanu konsolidator do tego czasu inicjowania.</span><span class="sxs-lookup"><span data-stu-id="6d963-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d963-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d963-114">Requirements</span></span>  
 <span data-ttu-id="6d963-115">Wymaga aLink.h</span><span class="sxs-lookup"><span data-stu-id="6d963-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d963-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d963-116">See also</span></span>

- [<span data-ttu-id="6d963-117">IALink3, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d963-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [<span data-ttu-id="6d963-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="6d963-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
- [<span data-ttu-id="6d963-119">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d963-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6d963-120">Al.exe (konsolidator zestawów)</span><span class="sxs-lookup"><span data-stu-id="6d963-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
