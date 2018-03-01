---
title: "GetWin32ResBlob — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="5d806-102">GetWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d806-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="5d806-103">Pobiera obiekt blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="5d806-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="5d806-104">Tę metodę można wywołać po ustawieniu opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="5d806-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d806-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d806-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5d806-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d806-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5d806-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="5d806-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="5d806-108">Token pliku używany do pobierania nazwy pliku do użycia podczas tworzenia zasobów Win32 wersji</span><span class="sxs-lookup"><span data-stu-id="5d806-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="5d806-109">Wartość TRUE, jeśli plik jest biblioteki DLL, false dla pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="5d806-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="5d806-110">Ikona opcjonalne wstawiania do obiektu blob zasobów.</span><span class="sxs-lookup"><span data-stu-id="5d806-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="5d806-111">Odbiera zasobów obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="5d806-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="5d806-112">Odbiera rozmiar obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="5d806-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d806-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="5d806-113">Return Value</span></span>  
 <span data-ttu-id="5d806-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="5d806-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d806-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d806-115">Requirements</span></span>  
 <span data-ttu-id="5d806-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="5d806-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d806-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d806-117">See Also</span></span>  
 [<span data-ttu-id="5d806-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d806-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="5d806-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d806-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="5d806-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="5d806-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
