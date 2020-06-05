---
title: 'Instrukcje: usuwanie klucza rejestru'
ms.date: 07/20/2015
f1_keywords:
- vb.DeleteSetting
helpviewer_keywords:
- GetSetting function [Visual Basic]
- registry [Visual Basic], deleting values
- GetAllSettings function
- registry keys [Visual Basic], deleting
- registry [Visual Basic], deleting keys
- examples [Visual Basic], registry
ms.assetid: ab9aca0e-42b0-4ff7-8ff9-845a4bfdf9f2
ms.openlocfilehash: ea537d302f64933176f1a44fec2e27b804ff5809
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363322"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="0832b-102">Porady: usuwanie klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0832b-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="0832b-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29>Metody i <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> mogą służyć do usuwania kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="0832b-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="0832b-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="0832b-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="0832b-105">Aby usunąć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="0832b-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="0832b-106">Użyj `DeleteSubKey` metody, aby usunąć klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="0832b-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="0832b-107">Ten przykład usuwa klucz oprogramowanie/TestApp w gałęzi CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="0832b-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="0832b-108">Można zmienić tę wartość w kodzie na odpowiedni ciąg lub na podstawie informacji podawanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0832b-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0832b-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="0832b-109">Robust Programming</span></span>  

 <span data-ttu-id="0832b-110">`DeleteSubKey`Metoda zwraca pusty ciąg, jeśli para klucz/wartość nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="0832b-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="0832b-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="0832b-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="0832b-112">Nazwa klucza to `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="0832b-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="0832b-113">Użytkownik nie ma uprawnień do usuwania kluczy rejestru ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="0832b-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="0832b-114">Nazwa klucza przekracza limit 255 znaków ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="0832b-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="0832b-115">Klucz rejestru jest tylko do odczytu ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="0832b-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0832b-116">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0832b-116">.NET Framework Security</span></span>  

 <span data-ttu-id="0832b-117">Wywołania rejestru kończą się niepowodzeniem, jeśli nie przyznano wystarczających uprawnień w czasie wykonywania ( <xref:System.Security.Permissions.RegistryPermission> ) lub jeśli użytkownik nie ma poprawnego dostępu (zgodnie z listą ACL) do tworzenia lub zapisywania do ustawień.</span><span class="sxs-lookup"><span data-stu-id="0832b-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="0832b-118">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0832b-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0832b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0832b-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="0832b-120">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="0832b-120">Security and the Registry</span></span>](security-and-the-registry.md)
- [<span data-ttu-id="0832b-121">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="0832b-121">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
