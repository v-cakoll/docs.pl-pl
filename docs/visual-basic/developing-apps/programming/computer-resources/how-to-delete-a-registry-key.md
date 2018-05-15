---
title: 'Porady: usuwanie klucza rejestru w Visual Basic'
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
ms.openlocfilehash: 8a983436b8c7415f0d356d65ae7d6c5ffd1c2db5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="dad71-102">Porady: usuwanie klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dad71-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="dad71-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> i <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metod można usunąć kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="dad71-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="dad71-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="dad71-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="dad71-105">Aby usunąć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="dad71-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="dad71-106">Użyj `DeleteSubKey` metodę, aby usunąć klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="dad71-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="dad71-107">W tym przykładzie powoduje usunięcie klucza oprogramowania/TestApp w gałęzi CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="dad71-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="dad71-108">Zmień kod na odpowiedni ciąg lub go na podstawie informacji dostarczone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dad71-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-delete-a-registry-key_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dad71-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="dad71-109">Robust Programming</span></span>  
 <span data-ttu-id="dad71-110">`DeleteSubKey` Metoda zwraca pusty ciąg, jeśli para klucza i wartości nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="dad71-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="dad71-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="dad71-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="dad71-112">Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="dad71-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="dad71-113">Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="dad71-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="dad71-114">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dad71-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="dad71-115">Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="dad71-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="dad71-116">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="dad71-116">.NET Framework Security</span></span>  
 <span data-ttu-id="dad71-117">Wywołania rejestru kończą się niepowodzeniem, jeśli nie są przyznawane albo wystarczające uprawnienia wykonawcze (<xref:System.Security.Permissions.RegistryPermission>) lub jeśli użytkownik nie ma dostępu (określone przez listy kontroli dostępu) do tworzenia lub zapisywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="dad71-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="dad71-118">Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="dad71-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad71-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dad71-119">See Also</span></span>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>  
 <xref:Microsoft.Win32.RegistryKey>  
 [<span data-ttu-id="dad71-120">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="dad71-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)  
 [<span data-ttu-id="dad71-121">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="dad71-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
