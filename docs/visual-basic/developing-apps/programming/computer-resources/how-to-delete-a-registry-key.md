---
title: 'Porady: usuwanie klucza rejestru'
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
ms.openlocfilehash: f38301a3a717a35b98e55804d6435d046bbbbab4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345656"
---
# <a name="how-to-delete-a-registry-key-in-visual-basic"></a><span data-ttu-id="a5e4f-102">Porady: usuwanie klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a5e4f-102">How to: Delete a Registry Key in Visual Basic</span></span>

<span data-ttu-id="a5e4f-103">I <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> metody mogą być używane do usuwania kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-103">The <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%29> and <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%28System.String%2CSystem.Boolean%29> methods can be used to delete registry keys.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="a5e4f-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="a5e4f-104">Procedure</span></span>  
  
#### <a name="to-delete-a-registry-key"></a><span data-ttu-id="a5e4f-105">Aby usunąć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="a5e4f-105">To delete a registry key</span></span>  
  
- <span data-ttu-id="a5e4f-106">Użyj `DeleteSubKey` tej metody, aby usunąć klucz rejestru.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-106">Use the `DeleteSubKey` method to delete a registry key.</span></span> <span data-ttu-id="a5e4f-107">W tym przykładzie usuwa klucz Software/TestApp w currentuser hive.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-107">This example deletes the key Software/TestApp in the CurrentUser hive.</span></span> <span data-ttu-id="a5e4f-108">Można to zmienić w kodzie na odpowiedni ciąg lub polegać na informacjach dostarczonych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-108">You can change this in the code to the appropriate string, or have it rely on user-supplied information.</span></span>  
  
     [!code-vb[VbResourceTasks#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a5e4f-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="a5e4f-109">Robust Programming</span></span>  

 <span data-ttu-id="a5e4f-110">Metoda `DeleteSubKey` zwraca pusty ciąg, jeśli para klucz/wartość nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-110">The `DeleteSubKey` method returns an empty string if the key/value pair does not exist.</span></span>  
  
 <span data-ttu-id="a5e4f-111">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="a5e4f-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a5e4f-112">Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="a5e4f-112">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="a5e4f-113">Użytkownik nie ma uprawnień do usuwania kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="a5e4f-113">The user does not have permissions to delete registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="a5e4f-114">Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).</span><span class="sxs-lookup"><span data-stu-id="a5e4f-114">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="a5e4f-115">Klucz rejestru jest tylko<xref:System.UnauthorizedAccessException>do odczytu ( ).</span><span class="sxs-lookup"><span data-stu-id="a5e4f-115">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a5e4f-116">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5e4f-116">.NET Framework Security</span></span>  

 <span data-ttu-id="a5e4f-117">Wywołania rejestru nie powiedzie się, jeśli nie<xref:System.Security.Permissions.RegistryPermission>udzielono wystarczających uprawnień w czasie wykonywania ( ) lub jeśli użytkownik nie ma poprawnego dostępu (określonego przez listy ACL) do tworzenia lub zapisywania w ustawieniach.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-117">Registry calls fail if either sufficient run-time permissions are not granted (<xref:System.Security.Permissions.RegistryPermission>) or if the user does not have the correct access (as determined by the ACLs) for creating or writing to settings.</span></span> <span data-ttu-id="a5e4f-118">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a5e4f-118">For example, a local application that has the code access security permission might not have operating system permission.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e4f-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5e4f-119">See also</span></span>

- <xref:Microsoft.Win32.RegistryKey.DeleteSubKey%2A>
- <xref:Microsoft.Win32.RegistryKey>
- [<span data-ttu-id="a5e4f-120">Bezpieczeństwo i rejestr</span><span class="sxs-lookup"><span data-stu-id="a5e4f-120">Security and the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/security-and-the-registry.md)
- [<span data-ttu-id="a5e4f-121">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="a5e4f-121">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
