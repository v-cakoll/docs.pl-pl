---
title: 'Porady: odczytywanie wartości z klucza rejestru w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 645ec80124a23ac86a06993bd4e06b59372a6d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586480"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="47e95-102">Porady: odczytywanie wartości z klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="47e95-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>
<span data-ttu-id="47e95-103">`GetValue` Metody `My.Computer.Registry` obiekt może służyć do odczytania wartości w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="47e95-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="47e95-104">Jeśli klucz "Software\MyApp" w poniższym przykładzie, nie istnieje, zwracany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="47e95-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="47e95-105">Jeśli `ValueName`, "Nazwa" nie istnieje w poniższym przykładzie, `Nothing` jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="47e95-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="47e95-106">`GetValue` Metody można również określić, czy dana wartość istnieje w kluczu rejestru.</span><span class="sxs-lookup"><span data-stu-id="47e95-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="47e95-107">Gdy kod odczytuje rejestru z aplikacji sieci Web, bieżącego użytkownika jest określana przez uwierzytelniania i personifikacji, która jest zaimplementowana w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="47e95-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="47e95-108">Odczytać wartości z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="47e95-108">To read a value from a registry key</span></span>  
  
-   <span data-ttu-id="47e95-109">Użyj `GetValue` metody, określając ścieżkę i nazwę) można odczytać wartości z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="47e95-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="47e95-110">Poniższy przykład odczytuje wartość `Name` z `HKEY_CURRENT_USER\Software\MyApp` i wyświetla je w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="47e95-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_1.vb)]  
  
 <span data-ttu-id="47e95-111">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="47e95-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="47e95-112">Selektor wstawek kodu, znajduje się się w **systemu operacyjnego Windows > rejestru**.</span><span class="sxs-lookup"><span data-stu-id="47e95-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="47e95-113">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="47e95-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="47e95-114">Aby określić, czy wartość istnieje w kluczu rejestru</span><span class="sxs-lookup"><span data-stu-id="47e95-114">To determine whether a value exists in a registry key</span></span>  
  
-   <span data-ttu-id="47e95-115">Użyj `GetValue` metody do pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="47e95-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="47e95-116">Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli jej nie ma.</span><span class="sxs-lookup"><span data-stu-id="47e95-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-read-a-value-from-a-registry-key_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="47e95-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="47e95-117">Robust Programming</span></span>  
 <span data-ttu-id="47e95-118">Rejestr zawiera najwyższego poziomu lub głównego kluczy, które są używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="47e95-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="47e95-119">Na przykład klucza głównego HKEY_LOCAL_MACHINE służy do przechowywania ustawień na poziomie komputera używane przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER jest używany do przechowywania danych specyficznych dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="47e95-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="47e95-120">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="47e95-120">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="47e95-121">Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="47e95-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="47e95-122">Użytkownik nie ma uprawnień do odczytu klucze rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="47e95-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="47e95-123">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="47e95-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="47e95-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="47e95-124">.NET Framework Security</span></span>  
 <span data-ttu-id="47e95-125">Aby uruchomić ten proces, używanemu zestawowi wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="47e95-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="47e95-126">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="47e95-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="47e95-127">Podobnie użytkownik musi mieć odpowiednich list ACL tworzenia i zapisywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="47e95-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="47e95-128">Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="47e95-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="47e95-129">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="47e95-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e95-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47e95-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.Win32.RegistryHive>  
 [<span data-ttu-id="47e95-131">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="47e95-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
