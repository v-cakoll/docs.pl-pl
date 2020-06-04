---
title: 'Instrukcje: odczytywanie wartości z klucza rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 74069b111f4316eb81c74f5e62c1fbff6ab8f4b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401852"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="7e329-102">Porady: odczytywanie wartości z klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e329-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="7e329-103">`GetValue`Metoda `My.Computer.Registry` obiektu może służyć do odczytywania wartości w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7e329-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="7e329-104">Jeśli klucz "Software\MyApp" w poniższym przykładzie nie istnieje, zgłaszany jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7e329-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="7e329-105">Jeśli `ValueName` w poniższym przykładzie nie istnieje, zwracana jest wartość "name" (nazwa) `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="7e329-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="7e329-106">`GetValue`Metody można również użyć do określenia, czy dana wartość istnieje w określonym kluczu rejestru.</span><span class="sxs-lookup"><span data-stu-id="7e329-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="7e329-107">Gdy kod odczytuje rejestr z aplikacji sieci Web, bieżący użytkownik jest określany przez uwierzytelnianie i personifikację, która jest zaimplementowana w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7e329-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="7e329-108">Odczytywanie wartości z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="7e329-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="7e329-109">Użyj `GetValue` metody, określając ścieżkę i nazwę) do odczytu wartości z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="7e329-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="7e329-110">Poniższy przykład odczytuje wartość `Name` z `HKEY_CURRENT_USER\Software\MyApp` i wyświetla ją w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="7e329-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7e329-111">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7e329-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="7e329-112">W selektorze fragmentów kodu znajduje się on w **systemie operacyjnym Windows > Registry**.</span><span class="sxs-lookup"><span data-stu-id="7e329-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="7e329-113">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="7e329-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="7e329-114">Aby określić, czy wartość istnieje w kluczu rejestru</span><span class="sxs-lookup"><span data-stu-id="7e329-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="7e329-115">Użyj `GetValue` metody, aby pobrać wartość.</span><span class="sxs-lookup"><span data-stu-id="7e329-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="7e329-116">Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="7e329-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7e329-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="7e329-117">Robust Programming</span></span>  

 <span data-ttu-id="7e329-118">Rejestr zawiera klucze najwyższego poziomu (lub główne), które są używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="7e329-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="7e329-119">Na przykład klucz główny HKEY_LOCAL_MACHINE jest używany do przechowywania ustawień na poziomie komputera używanych przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER jest używany do przechowywania danych specyficznych dla pojedynczego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7e329-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="7e329-120">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="7e329-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7e329-121">Nazwa klucza to `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="7e329-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="7e329-122">Użytkownik nie ma uprawnień do odczytu z kluczy rejestru ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="7e329-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="7e329-123">Nazwa klucza przekracza limit 255 znaków ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="7e329-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7e329-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e329-124">.NET Framework Security</span></span>  

 <span data-ttu-id="7e329-125">Aby uruchomić ten proces, zestaw wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.RegistryPermission> klasę.</span><span class="sxs-lookup"><span data-stu-id="7e329-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="7e329-126">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="7e329-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="7e329-127">Analogicznie, użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania w ustawieniach.</span><span class="sxs-lookup"><span data-stu-id="7e329-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="7e329-128">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7e329-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="7e329-129">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7e329-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e329-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e329-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="7e329-131">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="7e329-131">Reading from and Writing to the Registry</span></span>](reading-from-and-writing-to-the-registry.md)
