---
title: Bezpieczeństwo i rejestr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345485"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="a6ce1-102">Bezpieczeństwo i rejestr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6ce1-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="a6ce1-103">This page discusses the security implications of storing data in the registry.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="a6ce1-104">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="a6ce1-104">Permissions</span></span>  

 <span data-ttu-id="a6ce1-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span><span class="sxs-lookup"><span data-stu-id="a6ce1-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="a6ce1-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="a6ce1-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="a6ce1-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="a6ce1-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="a6ce1-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="a6ce1-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="a6ce1-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="a6ce1-113">The following table details its members.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="a6ce1-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="a6ce1-114">Value</span></span>|<span data-ttu-id="a6ce1-115">Access to Registry Variables</span><span class="sxs-lookup"><span data-stu-id="a6ce1-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="a6ce1-116">Create, read, and write</span><span class="sxs-lookup"><span data-stu-id="a6ce1-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="a6ce1-117">Create</span><span class="sxs-lookup"><span data-stu-id="a6ce1-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="a6ce1-118">No access</span><span class="sxs-lookup"><span data-stu-id="a6ce1-118">No access</span></span>|  
|`Read`|<span data-ttu-id="a6ce1-119">Odczyt</span><span class="sxs-lookup"><span data-stu-id="a6ce1-119">Read</span></span>|  
|`Write`|<span data-ttu-id="a6ce1-120">Write</span><span class="sxs-lookup"><span data-stu-id="a6ce1-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="a6ce1-121">Checking Values in Registry Keys</span><span class="sxs-lookup"><span data-stu-id="a6ce1-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="a6ce1-122">When you create a registry value, you need to decide what to do if that value already exists.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="a6ce1-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="a6ce1-124">When you put data in the registry value, the data is available to the other process.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="a6ce1-125">To prevent this, use the `GetValue` method.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="a6ce1-126">It returns `Nothing` if the key does not already exist.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a6ce1-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span><span class="sxs-lookup"><span data-stu-id="a6ce1-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6ce1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6ce1-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="a6ce1-129">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="a6ce1-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
