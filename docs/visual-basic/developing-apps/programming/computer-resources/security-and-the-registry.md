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
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="09cc2-102">Bezpieczeństwo i rejestr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09cc2-102">Security and the Registry (Visual Basic)</span></span>

<span data-ttu-id="09cc2-103">Na tej stronie omówiono implikacje zabezpieczeń przechowywania danych w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="09cc2-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="09cc2-104">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="09cc2-104">Permissions</span></span>  

 <span data-ttu-id="09cc2-105">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (listy kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="09cc2-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="09cc2-106">Praca z rejestrem może naruszyć bezpieczeństwo przez umożliwienie nieodpowiedniego dostępu do zasobów systemowych lub chronionych informacji.</span><span class="sxs-lookup"><span data-stu-id="09cc2-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="09cc2-107">Aby użyć tych właściwości, musisz mieć uprawnienia do odczytu i zapisu z wyliczenia <xref:System.Security.Permissions.RegistryPermissionAccess>, które kontroluje dostęp do zmiennych rejestru.</span><span class="sxs-lookup"><span data-stu-id="09cc2-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="09cc2-108">Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń) jest to każdy kod zainstalowany na lokalnym dysku twardym użytkownika, który ma odpowiednie uprawnienia dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="09cc2-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="09cc2-109">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.RegistryPermission> Class.</span><span class="sxs-lookup"><span data-stu-id="09cc2-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="09cc2-110">Zmienne rejestru nie powinny być przechowywane w lokalizacjach pamięci, w których kod bez <xref:System.Security.Permissions.RegistryPermission> może uzyskać do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="09cc2-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="09cc2-111">Podobnie, podczas udzielania uprawnień należy przyznać minimalnych uprawnień niezbędnych do wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="09cc2-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="09cc2-112">Wartości dostępu do uprawnień rejestru są definiowane przez Wyliczenie <xref:System.Security.Permissions.RegistryPermissionAccess>.</span><span class="sxs-lookup"><span data-stu-id="09cc2-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="09cc2-113">Poniższa tabela zawiera szczegółowe informacje o jej elementach członkowskich.</span><span class="sxs-lookup"><span data-stu-id="09cc2-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="09cc2-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="09cc2-114">Value</span></span>|<span data-ttu-id="09cc2-115">Dostęp do zmiennych rejestru</span><span class="sxs-lookup"><span data-stu-id="09cc2-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="09cc2-116">Tworzenie, odczytywanie i zapisywanie</span><span class="sxs-lookup"><span data-stu-id="09cc2-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="09cc2-117">Utwórz</span><span class="sxs-lookup"><span data-stu-id="09cc2-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="09cc2-118">Brak dostępu</span><span class="sxs-lookup"><span data-stu-id="09cc2-118">No access</span></span>|  
|`Read`|<span data-ttu-id="09cc2-119">Odczyt</span><span class="sxs-lookup"><span data-stu-id="09cc2-119">Read</span></span>|  
|`Write`|<span data-ttu-id="09cc2-120">Zapis</span><span class="sxs-lookup"><span data-stu-id="09cc2-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="09cc2-121">Sprawdzanie wartości w kluczach rejestru</span><span class="sxs-lookup"><span data-stu-id="09cc2-121">Checking Values in Registry Keys</span></span>  

 <span data-ttu-id="09cc2-122">Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="09cc2-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="09cc2-123">Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="09cc2-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="09cc2-124">Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu.</span><span class="sxs-lookup"><span data-stu-id="09cc2-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="09cc2-125">Aby temu zapobiec, użyj metody `GetValue`.</span><span class="sxs-lookup"><span data-stu-id="09cc2-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="09cc2-126">Zwraca `Nothing`, jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="09cc2-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="09cc2-127">Podczas odczytywania rejestru z aplikacji sieci Web tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="09cc2-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09cc2-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09cc2-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="09cc2-129">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="09cc2-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
