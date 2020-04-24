---
title: Bezpieczeństwo i rejestr
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: 454180207d6432e80d87941d1f329f2a4ea7a801
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345485"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="5b390-102">Bezpieczeństwo i rejestr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b390-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="5b390-103">Na tej stronie omówiono implikacje zabezpieczeń przechowywania danych w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="5b390-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="5b390-104">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="5b390-104">Permissions</span></span>  

 <span data-ttu-id="5b390-105">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (listy kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="5b390-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="5b390-106">Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji.</span><span class="sxs-lookup"><span data-stu-id="5b390-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="5b390-107">Aby użyć tych właściwości, musisz mieć uprawnienia do odczytu i zapisu z <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, które kontroluje dostęp do zmiennych rejestru.</span><span class="sxs-lookup"><span data-stu-id="5b390-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="5b390-108">Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń) jest to każdy kod zainstalowany na lokalnym dysku twardym użytkownika, który ma odpowiednie uprawnienia dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="5b390-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="5b390-109">Aby uzyskać więcej informacji, <xref:System.Security.Permissions.RegistryPermission> zobacz Klasa.</span><span class="sxs-lookup"><span data-stu-id="5b390-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="5b390-110">Zmienne rejestru nie powinny być przechowywane w lokalizacjach pamięci, w <xref:System.Security.Permissions.RegistryPermission> których kod nie może uzyskać do nich dostępu.</span><span class="sxs-lookup"><span data-stu-id="5b390-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="5b390-111">Podobnie, podczas udzielania uprawnień należy przyznać minimalnych uprawnień niezbędnych do wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="5b390-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="5b390-112">Wartości dostępu do uprawnień rejestru są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="5b390-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="5b390-113">Poniższa tabela zawiera szczegółowe informacje o jej elementach członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5b390-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="5b390-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="5b390-114">Value</span></span>|<span data-ttu-id="5b390-115">Dostęp do zmiennych rejestru</span><span class="sxs-lookup"><span data-stu-id="5b390-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="5b390-116">Tworzenie, odczytywanie i zapisywanie</span><span class="sxs-lookup"><span data-stu-id="5b390-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="5b390-117">Utwórz</span><span class="sxs-lookup"><span data-stu-id="5b390-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="5b390-118">Brak dostępu</span><span class="sxs-lookup"><span data-stu-id="5b390-118">No access</span></span>|  
|`Read`|<span data-ttu-id="5b390-119">Odczyt</span><span class="sxs-lookup"><span data-stu-id="5b390-119">Read</span></span>|  
|`Write`|<span data-ttu-id="5b390-120">Zapisywanie</span><span class="sxs-lookup"><span data-stu-id="5b390-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="5b390-121">Sprawdzanie wartości w kluczach rejestru</span><span class="sxs-lookup"><span data-stu-id="5b390-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="5b390-122">Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="5b390-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="5b390-123">Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="5b390-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="5b390-124">Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu.</span><span class="sxs-lookup"><span data-stu-id="5b390-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="5b390-125">Aby tego uniknąć, należy użyć `GetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="5b390-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="5b390-126">Zwraca `Nothing` , jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5b390-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b390-127">Podczas odczytywania rejestru z aplikacji sieci Web tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5b390-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b390-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5b390-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="5b390-129">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="5b390-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
