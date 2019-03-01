---
title: 'Instrukcje: Usuwanie klucza rejestru w Visual Basic'
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
ms.openlocfilehash: 7ff6ba8e31638b64fa7100b1807303c61a454c81
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981676"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="2f308-102">Instrukcje: Usuwanie klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f308-102">How to: Delete a Registry Key in Visual Basic</span></span>
<span data-ttu-id="2f308-103"><xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> i <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody służy do usuwania kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="2f308-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="2f308-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="2f308-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="2f308-105">Aby usunąć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="2f308-105">To delete a registry key</span></span>  
  
-   <span data-ttu-id="2f308-106">Użyj `DeleteSubKey` metodę, aby usunąć klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="2f308-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="2f308-107">W tym przykładzie usuwa klucz oprogramowania/TestApp w gałęzi CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="2f308-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="2f308-108">Możesz zmienić w kodzie na odpowiedni ciąg lub jego opierają się na informacjach dostarczonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2f308-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2f308-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2f308-109">Robust Programming</span></span>  
 <span data-ttu-id="2f308-110">`DeleteSubKey` Metoda zwraca pusty ciąg, jeśli para klucza i wartości nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2f308-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="2f308-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2f308-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2f308-112">Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="2f308-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="2f308-113">Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="2f308-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="2f308-114">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2f308-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="2f308-115">Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="2f308-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2f308-116">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f308-116">.NET Framework Security</span></span>  
 <span data-ttu-id="2f308-117">Wywołania rejestru kończyć się niepowodzeniem, jeśli nie są przyznawane albo wystarczające uprawnienia środowiska wykonawczego (<xref:System.Security.Permissions.RegistryPermission>) lub jeśli użytkownik nie ma prawidłowy dostęp (zgodnie z ustaleniami listy ACL), tworzenia i zapisywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="2f308-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="2f308-118">Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu ma uprawnienie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2f308-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f308-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f308-119">See also</span></span>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="2f308-120">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="2f308-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="2f308-121">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="2f308-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
