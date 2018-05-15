---
title: Bezpieczeństwo i rejestr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: ddfe8f88763ee2db78d25d72e6c9cb3456ccd13f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="c1c6a-102">Bezpieczeństwo i rejestr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1c6a-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="c1c6a-103">Ta strona zawiera omówienie zabezpieczenia przechowywania danych w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c1c6a-104">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="c1c6a-104">Permissions</span></span>  
 <span data-ttu-id="c1c6a-105">Nie jest bezpieczny do przechowywania kluczy tajnych, takie jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (listy kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="c1c6a-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="c1c6a-106">Praca z rejestru może naruszyć bezpieczeństwo, zezwalając nieodpowiednie dostęp do zasobów systemowych lub chronionych informacji.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="c1c6a-107">Aby korzystać z tych właściwości, musi mieć uprawnienia z odczytu i zapisu <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, która kontroluje dostęp do zmiennych rejestru.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="c1c6a-108">Każdy kod uruchomiona z pełnym zaufaniem (w obszarze domyślnych zasad zabezpieczeń jest dowolny kod zainstalowana na lokalnym dysku twardym użytkownika) ma niezbędne uprawnienia dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="c1c6a-109">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.RegistryPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="c1c6a-110">Zmienne rejestru nie powinny być przechowywane w lokalizacji pamięci gdzie kodu bez <xref:System.Security.Permissions.RegistryPermission> mogą uzyskiwać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="c1c6a-111">Podobnie podczas udzielania uprawnień, należy przyznać minimalne uprawnienia, które trzeba wykonać zadanie.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="c1c6a-112">Uprawnienia dostępu do wartości są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="c1c6a-113">W poniższej tabeli przedstawiono jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="c1c6a-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="c1c6a-114">Value</span></span>|<span data-ttu-id="c1c6a-115">Dostęp do zmiennych rejestru</span><span class="sxs-lookup"><span data-stu-id="c1c6a-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="c1c6a-116">Tworzenia, odczytu i zapisu</span><span class="sxs-lookup"><span data-stu-id="c1c6a-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="c1c6a-117">Create</span><span class="sxs-lookup"><span data-stu-id="c1c6a-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="c1c6a-118">Brak dostępu</span><span class="sxs-lookup"><span data-stu-id="c1c6a-118">No access</span></span>|  
|`Read`|<span data-ttu-id="c1c6a-119">Odczyt</span><span class="sxs-lookup"><span data-stu-id="c1c6a-119">Read</span></span>|  
|`Write`|<span data-ttu-id="c1c6a-120">Write</span><span class="sxs-lookup"><span data-stu-id="c1c6a-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="c1c6a-121">Sprawdzanie wartości kluczy rejestru</span><span class="sxs-lookup"><span data-stu-id="c1c6a-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="c1c6a-122">Po utworzeniu wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="c1c6a-123">Inny proces, możliwe, że złośliwe jeden mogły już zostać utworzone wartość i jest do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="c1c6a-124">Po umieszczeniu danych w wartości rejestru, dane są dostępne do innego procesu.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="c1c6a-125">Aby tego uniknąć, należy użyć `GetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="c1c6a-126">Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c1c6a-127">Podczas odczytywania rejestru z aplikacji sieci Web, tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji wdrożone w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c1c6a-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c6a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c1c6a-128">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 [<span data-ttu-id="c1c6a-129">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="c1c6a-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
