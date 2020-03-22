---
title: 'Porady: odczytywanie wartości z klucza rejestru'
ms.date: 07/20/2015
helpviewer_keywords:
- registry keys [Visual Basic], determining if a value exists in
- My.Computer.Registry object, examples
- registry [Visual Basic], determining if values exist
- registry keys [Visual Basic], reading from
- registry [Visual Basic], reading
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
ms.openlocfilehash: 73c32aefe06a68bb42fcb5f4615da0927e57e892
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345615"
---
# <a name="how-to-read-a-value-from-a-registry-key-in-visual-basic"></a><span data-ttu-id="8c1d4-102">Porady: odczytywanie wartości z klucza rejestru w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c1d4-102">How to: Read a Value from a Registry Key in Visual Basic</span></span>

<span data-ttu-id="8c1d4-103">Metoda `GetValue` `My.Computer.Registry` obiektu może służyć do odczytywania wartości w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-103">The `GetValue` method of the `My.Computer.Registry` object can be used to read values in the Windows registry.</span></span>  
  
 <span data-ttu-id="8c1d4-104">Jeśli klucz "Software\MyApp" w poniższym przykładzie nie istnieje, zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-104">If the key, "Software\MyApp" in the following example, does not exist, an exception is thrown.</span></span> <span data-ttu-id="8c1d4-105">Jeśli `ValueName`, "Nazwa" w poniższym przykładzie, nie istnieje, `Nothing` jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-105">If the `ValueName`,  "Name" in the following example, does not exist, `Nothing` is returned.</span></span>  
  
 <span data-ttu-id="8c1d4-106">Metoda `GetValue` może również służyć do określenia, czy dana wartość istnieje w określonym kluczu rejestru.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-106">The `GetValue` method can also be used to determine whether a given value exists in a specific registry key.</span></span>  
  
 <span data-ttu-id="8c1d4-107">Gdy kod odczytuje rejestr z aplikacji sieci Web, bieżący użytkownik jest określany przez uwierzytelnianie i personifikację zaimplementowane w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-107">When code reads the registry from a Web application, the current user is determined by the authentication and impersonation that is implemented in the Web application.</span></span>  
  
### <a name="to-read-a-value-from-a-registry-key"></a><span data-ttu-id="8c1d4-108">Aby odczytać wartość z klucza rejestru</span><span class="sxs-lookup"><span data-stu-id="8c1d4-108">To read a value from a registry key</span></span>  
  
- <span data-ttu-id="8c1d4-109">Użyj `GetValue` metody, określając ścieżkę i nazwę), aby odczytać wartość z klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-109">Use the `GetValue` method, specifying the path and name) to read a value from registry key.</span></span> <span data-ttu-id="8c1d4-110">W poniższym przykładzie odczytuje wartość `Name` i `HKEY_CURRENT_USER\Software\MyApp` wyświetla ją w oknie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-110">The following example reads the value `Name` from `HKEY_CURRENT_USER\Software\MyApp` and displays it in a message box.</span></span>  
  
     [!code-vb[VbResourceTasks#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#4)]  
  
 <span data-ttu-id="8c1d4-111">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="8c1d4-112">W selektorze fragmentów kodu znajduje się w **rejestrze > systemu operacyjnego Windows**.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-112">In the code snippet picker, it is located in **Windows Operating System > Registry**.</span></span> <span data-ttu-id="8c1d4-113">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="8c1d4-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
### <a name="to-determine-whether-a-value-exists-in-a-registry-key"></a><span data-ttu-id="8c1d4-114">Aby ustalić, czy wartość istnieje w kluczu rejestru</span><span class="sxs-lookup"><span data-stu-id="8c1d4-114">To determine whether a value exists in a registry key</span></span>  
  
- <span data-ttu-id="8c1d4-115">Użyj `GetValue` metody, aby pobrać wartość.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-115">Use the `GetValue` method to retrieve the value.</span></span> <span data-ttu-id="8c1d4-116">Poniższy kod sprawdza, czy wartość istnieje i zwraca komunikat, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-116">The following code checks whether the value exists and returns a message if it does not.</span></span>  
  
     [!code-vb[VbResourceTasks#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#12)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8c1d4-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8c1d4-117">Robust Programming</span></span>  

 <span data-ttu-id="8c1d4-118">Rejestr zawiera klucze najwyższego poziomu lub katalogu głównego, które są używane do przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-118">The registry holds top-level, or root, keys that are used to store data.</span></span> <span data-ttu-id="8c1d4-119">Na przykład klucz główny HKEY_LOCAL_MACHINE służy do przechowywania ustawień na poziomie komputera używanych przez wszystkich użytkowników, podczas gdy HKEY_CURRENT_USER służy do przechowywania danych specyficznych dla poszczególnych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-119">For instance, the HKEY_LOCAL_MACHINE root key is used for storing machine-level settings used by all users, while HKEY_CURRENT_USER is used for storing data specific to an individual user.</span></span>  
  
 <span data-ttu-id="8c1d4-120">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="8c1d4-120">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8c1d4-121">Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="8c1d4-121">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="8c1d4-122">Użytkownik nie ma uprawnień do odczytu<xref:System.Security.SecurityException>z kluczy rejestru ( ).</span><span class="sxs-lookup"><span data-stu-id="8c1d4-122">The user does not have permissions to read from registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="8c1d4-123">Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).</span><span class="sxs-lookup"><span data-stu-id="8c1d4-123">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8c1d4-124">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c1d4-124">.NET Framework Security</span></span>  

 <span data-ttu-id="8c1d4-125">Aby uruchomić ten proces, zestaw wymaga poziomu <xref:System.Security.Permissions.RegistryPermission> uprawnień przyznanego przez klasę.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-125">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="8c1d4-126">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-126">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="8c1d4-127">Podobnie użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania do ustawień.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-127">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="8c1d4-128">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c1d4-128">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="8c1d4-129">Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8c1d4-129">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c1d4-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c1d4-130">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.Win32.RegistryHive>
- [<span data-ttu-id="8c1d4-131">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="8c1d4-131">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
