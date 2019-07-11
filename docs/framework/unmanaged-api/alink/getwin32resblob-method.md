---
title: GetWin32ResBlob — Metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdc1ef6490f250ebe93b0482adf244adfc0ffd56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741785"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="9b7e6-102">GetWin32ResBlob — Metoda</span><span class="sxs-lookup"><span data-stu-id="9b7e6-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="9b7e6-103">Pobiera obiekt blob zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="9b7e6-104">Wywołaj tę metodę po ustawieniu opcji zestawu.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b7e6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="9b7e6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b7e6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b7e6-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="9b7e6-107">Identyfikator zestawu.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="9b7e6-108">Token pliku używany do pobrania nazwy pliku, który będzie używany podczas tworzenia zasobów Win32 w wersji</span><span class="sxs-lookup"><span data-stu-id="9b7e6-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="9b7e6-109">Wartość TRUE, jeśli plik jest biblioteką DLL, false dla pliku EXE.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="9b7e6-110">Opcjonalne ikona Wstawianie obiektu blob zasobów.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="9b7e6-111">Odbiera zasobów obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="9b7e6-112">Uzyskuje rozmiar obiektu blob.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b7e6-113">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9b7e6-113">Return Value</span></span>  
 <span data-ttu-id="9b7e6-114">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="9b7e6-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b7e6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9b7e6-115">Requirements</span></span>  
 <span data-ttu-id="9b7e6-116">Wymaga alink.h</span><span class="sxs-lookup"><span data-stu-id="9b7e6-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b7e6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b7e6-117">See also</span></span>

- [<span data-ttu-id="9b7e6-118">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b7e6-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="9b7e6-119">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="9b7e6-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="9b7e6-120">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="9b7e6-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
