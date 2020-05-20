---
title: ICLRDomainManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager
helpviewer_keywords:
- ICLRDomainManager interface [.NET Framework hosting]
ms.assetid: f08b2390-d872-4521-a815-e9c237c4c45d
ms.openlocfilehash: dda243ccbf18f396c1bcc03358997ea0f06c42a8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615712"
---
# <a name="iclrdomainmanager-interface"></a><span data-ttu-id="ab9d1-102">ICLRDomainManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab9d1-102">ICLRDomainManager Interface</span></span>
<span data-ttu-id="ab9d1-103">Umożliwia hostowi określenie Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji, oraz do określania właściwości inicjacji.</span><span class="sxs-lookup"><span data-stu-id="ab9d1-103">Enables the host to specify the application domain manager that will be used to initialize the default application domain, and to specify initialization properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab9d1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab9d1-104">Methods</span></span>  
  
|<span data-ttu-id="ab9d1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab9d1-105">Method</span></span>|<span data-ttu-id="ab9d1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9d1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab9d1-107">SetAppDomainManagerType, metoda</span><span class="sxs-lookup"><span data-stu-id="ab9d1-107">SetAppDomainManagerType Method</span></span>](iclrdomainmanager-setappdomainmanagertype-method.md)|<span data-ttu-id="ab9d1-108">Określa typ, który pochodzi od <xref:System.AppDomainManager?displayProperty=nameWithType> klasy, Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab9d1-108">Specifies the type, derived from the <xref:System.AppDomainManager?displayProperty=nameWithType> class, of the application domain manager that will be used to initialize the default application domain.</span></span>|  
|[<span data-ttu-id="ab9d1-109">SetPropertiesForDefaultAppDomain, metoda</span><span class="sxs-lookup"><span data-stu-id="ab9d1-109">SetPropertiesForDefaultAppDomain Method</span></span>](iclrdomainmanager-setpropertiesfordefaultappdomain-method.md)|<span data-ttu-id="ab9d1-110">Ustawia właściwości, które zostaną użyte do zainicjowania domyślnej domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ab9d1-110">Sets properties that will be used to initialize the default application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab9d1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab9d1-111">Remarks</span></span>  
 <span data-ttu-id="ab9d1-112">Aby uzyskać wystąpienie tego interfejsu, wywołaj metodę [ICLRControl:: GetCLRManager —](iclrcontrol-getclrmanager-method.md) z menedżerem typu IID `IID_ICLRDomainManager` .</span><span class="sxs-lookup"><span data-stu-id="ab9d1-112">To get an instance of this interface, call the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method with the manager type IID `IID_ICLRDomainManager`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab9d1-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab9d1-113">Requirements</span></span>  
 <span data-ttu-id="ab9d1-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab9d1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9d1-115">**Nagłówek:** Obiekt ServiceHost. h</span><span class="sxs-lookup"><span data-stu-id="ab9d1-115">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab9d1-116">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab9d1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab9d1-117">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab9d1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9d1-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab9d1-118">See also</span></span>

- [<span data-ttu-id="ab9d1-119">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab9d1-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ab9d1-120">Hosting</span><span class="sxs-lookup"><span data-stu-id="ab9d1-120">Hosting</span></span>](index.md)
