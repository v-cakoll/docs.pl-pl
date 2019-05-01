---
title: Bezpieczeństwo i rejestr (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- security [Visual Basic], registry
- registry [Visual Basic], security issues
ms.assetid: 9980aff7-2f69-492b-8f66-29a9a76d3df5
ms.openlocfilehash: dc0071d1fddf99bd712ebe8aea5c61bbc3522f93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921215"
---
# <a name="security-and-the-registry-visual-basic"></a><span data-ttu-id="43a07-102">Bezpieczeństwo i rejestr (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43a07-102">Security and the Registry (Visual Basic)</span></span>
<span data-ttu-id="43a07-103">Ta strona zawiera omówienie ryzyko związane z przechowywaniem danych w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="43a07-103">This page discusses the security implications of storing data in the registry.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="43a07-104">Uprawnienia</span><span class="sxs-lookup"><span data-stu-id="43a07-104">Permissions</span></span>  
 <span data-ttu-id="43a07-105">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (listy kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="43a07-105">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (access control lists).</span></span>  
  
 <span data-ttu-id="43a07-106">Praca z rejestru może naruszyć bezpieczeństwo, zezwalając na niewłaściwe dostęp do zasobów systemowych lub informacje chronione.</span><span class="sxs-lookup"><span data-stu-id="43a07-106">Working with the registry may compromise security by allowing inappropriate access to system resources or protected information.</span></span> <span data-ttu-id="43a07-107">Aby korzystać z tych właściwości, konieczne jest posiadanie Odczyt i zapis z <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia, które kontrolują dostęp do zmiennych rejestru.</span><span class="sxs-lookup"><span data-stu-id="43a07-107">To use these properties, you must have read and write permissions from the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration, which controls access to registry variables.</span></span> <span data-ttu-id="43a07-108">Każdy kod z pełnym zaufaniem (w ramach domyślnych zasad zabezpieczeń, to każdy kod zainstalowana na lokalnym dysku twardym użytkownika) ma niezbędne uprawnienia dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="43a07-108">Any code running with full trust (under the default security policy, this is any code installed on the user's local hard disk) has the necessary permissions to access the registry.</span></span> <span data-ttu-id="43a07-109">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.RegistryPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="43a07-109">For more information, see <xref:System.Security.Permissions.RegistryPermission> class.</span></span>  
  
 <span data-ttu-id="43a07-110">Zmienne rejestru nie powinien być przechowywany w lokalizacji pamięci gdzie kodu bez <xref:System.Security.Permissions.RegistryPermission> mają do nich dostęp.</span><span class="sxs-lookup"><span data-stu-id="43a07-110">Registry variables should not be stored in memory locations where code without <xref:System.Security.Permissions.RegistryPermission> can access them.</span></span> <span data-ttu-id="43a07-111">Podobnie podczas nadawania uprawnień należy przyznać minimalne uprawnienia, które trzeba wykonać zadanie.</span><span class="sxs-lookup"><span data-stu-id="43a07-111">Similarly, when granting permissions, grant the minimum privileges necessary to get the job done.</span></span>  
  
 <span data-ttu-id="43a07-112">Uprawnienia dostępu do wartości są definiowane przez <xref:System.Security.Permissions.RegistryPermissionAccess> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="43a07-112">Registry permission access values are defined by the <xref:System.Security.Permissions.RegistryPermissionAccess> enumeration.</span></span> <span data-ttu-id="43a07-113">W poniższej tabeli przedstawiono jej członków.</span><span class="sxs-lookup"><span data-stu-id="43a07-113">The following table details its members.</span></span>  
  
|<span data-ttu-id="43a07-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="43a07-114">Value</span></span>|<span data-ttu-id="43a07-115">Dostęp do zmiennych rejestru</span><span class="sxs-lookup"><span data-stu-id="43a07-115">Access to Registry Variables</span></span>|  
|-----------|----------------------------------|  
|`AllAccess`|<span data-ttu-id="43a07-116">Tworzenia, odczytu i zapis</span><span class="sxs-lookup"><span data-stu-id="43a07-116">Create, read, and write</span></span>|  
|`Create`|<span data-ttu-id="43a07-117">Create</span><span class="sxs-lookup"><span data-stu-id="43a07-117">Create</span></span>|  
|`NoAccess`|<span data-ttu-id="43a07-118">Brak dostępu</span><span class="sxs-lookup"><span data-stu-id="43a07-118">No access</span></span>|  
|`Read`|<span data-ttu-id="43a07-119">Odczyt</span><span class="sxs-lookup"><span data-stu-id="43a07-119">Read</span></span>|  
|`Write`|<span data-ttu-id="43a07-120">Write</span><span class="sxs-lookup"><span data-stu-id="43a07-120">Write</span></span>|  
  
## <a name="checking-values-in-registry-keys"></a><span data-ttu-id="43a07-121">Sprawdzanie wartości w kluczach rejestru</span><span class="sxs-lookup"><span data-stu-id="43a07-121">Checking Values in Registry Keys</span></span>  
 <span data-ttu-id="43a07-122">Kiedy tworzysz wartość rejestru, musisz zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="43a07-122">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="43a07-123">Inny proces, fałszywy, być może już utworzył wartość i masz do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="43a07-123">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="43a07-124">Dane są umieszczane w wartości rejestru, dane są dostępne dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="43a07-124">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="43a07-125">Aby tego uniknąć, należy użyć `GetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="43a07-125">To prevent this, use the `GetValue` method.</span></span> <span data-ttu-id="43a07-126">Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="43a07-126">It returns `Nothing` if the key does not already exist.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43a07-127">Podczas odczytywania rejestru z aplikacji sieci Web, tożsamość bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowane w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="43a07-127">When reading the registry from a Web application, the identity of current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43a07-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43a07-128">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- [<span data-ttu-id="43a07-129">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="43a07-129">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
