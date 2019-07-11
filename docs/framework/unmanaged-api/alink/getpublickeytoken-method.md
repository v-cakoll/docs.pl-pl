---
title: GetPublicKeyToken — Metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec2c357cd56670f4f2deed8023bed7842a7f4ed7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741872"
---
# <a name="getpublickeytoken-method"></a><span data-ttu-id="1a433-102">GetPublicKeyToken — Metoda</span><span class="sxs-lookup"><span data-stu-id="1a433-102">GetPublicKeyToken Method</span></span>
<span data-ttu-id="1a433-103">Pobiera token klucza publicznego do pliku danego klucza lub kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="1a433-103">Retrieves the public key token for a given keyfile or key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a433-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a433-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a433-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a433-105">Parameters</span></span>  
 `pszKeyFile`  
 <span data-ttu-id="1a433-106">Nazwa pliku klucza.</span><span class="sxs-lookup"><span data-stu-id="1a433-106">Filename of the key.</span></span>  
  
 `pszKeyContainer`  
 <span data-ttu-id="1a433-107">Nazwa kontenera kluczy.</span><span class="sxs-lookup"><span data-stu-id="1a433-107">Name of the key container.</span></span>  
  
 `pvPublicKeyToken`  
 <span data-ttu-id="1a433-108">Adres, gdzie token klucza ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="1a433-108">Address where key token is to be stored.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="1a433-109">Określa rozmiar w bajtach, bufor wskazywany przez `pvPublicKeyToken`.</span><span class="sxs-lookup"><span data-stu-id="1a433-109">Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`.</span></span> <span data-ttu-id="1a433-110">Po powrocie zawiera rzeczywista liczba bajtów używanych.</span><span class="sxs-lookup"><span data-stu-id="1a433-110">Upon return, contains actual number of bytes used.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a433-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a433-111">Return Value</span></span>  
 <span data-ttu-id="1a433-112">Zwraca wartość S_OK, jeśli metoda zakończy się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="1a433-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a433-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a433-113">Requirements</span></span>  
 <span data-ttu-id="1a433-114">Wymaga alink.h.</span><span class="sxs-lookup"><span data-stu-id="1a433-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a433-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a433-115">See also</span></span>

- [<span data-ttu-id="1a433-116">IALink2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a433-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="1a433-117">IALink, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a433-117">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="1a433-118">ALink, interfejs API</span><span class="sxs-lookup"><span data-stu-id="1a433-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
