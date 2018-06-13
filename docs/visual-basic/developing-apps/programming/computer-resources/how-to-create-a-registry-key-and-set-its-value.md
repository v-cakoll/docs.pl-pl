---
title: 'Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- RegistryKey.CreateSubKey
- RegistryKey.SetValue
helpviewer_keywords:
- registry keys [Visual Basic], creating
- registry [Visual Basic], adding values
- registry [Visual Basic], adding keys
- registry keys [Visual Basic], setting values
- examples [Visual Basic], registry
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
ms.openlocfilehash: 4f74d41aa8055e26f5a707829449ddd310ff576f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590754"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="827dd-102">Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="827dd-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="827dd-103">`CreateSubKey` Metody `My.Computer.Registry` obiekt może służyć do tworzenia klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="827dd-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="827dd-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="827dd-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="827dd-105">Aby utworzyć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="827dd-105">To create a registry key</span></span>  
  
-   <span data-ttu-id="827dd-106">Użyj `CreateSubKey` metody, wskazujące, której hive można umieścić klucz w obszarze, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="827dd-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="827dd-107">Parametr `Subkey` nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="827dd-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="827dd-108">W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="827dd-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="827dd-109">Utwórz klucz rejestru i ustawić wartość w nim</span><span class="sxs-lookup"><span data-stu-id="827dd-109">To create a registry key and set a value in it</span></span>  
  
1.  <span data-ttu-id="827dd-110">Użyj `CreateSubkey` metody, wskazujące, której hive można umieścić klucz w obszarze, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="827dd-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="827dd-111">W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="827dd-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  <span data-ttu-id="827dd-112">Ustaw wartość z `SetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="827dd-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="827dd-113">W tym przykładzie wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="827dd-113">This example sets the string value.</span></span> <span data-ttu-id="827dd-114">"MyTestKeyValue" do "Jest wartość testu".</span><span class="sxs-lookup"><span data-stu-id="827dd-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="827dd-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="827dd-115">Example</span></span>  
 <span data-ttu-id="827dd-116">W tym przykładzie jest tworzony klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER, a następnie ustawia wartość ciągu `MyTestKeyValue` do `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="827dd-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="827dd-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="827dd-117">Robust Programming</span></span>  
 <span data-ttu-id="827dd-118">Sprawdź, czy struktura rejestru można znaleźć odpowiedniej lokalizacji dla klucza.</span><span class="sxs-lookup"><span data-stu-id="827dd-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="827dd-119">Na przykład można otworzyć klucza HKEY_CURRENT_USER\Software bieżącego użytkownika i Utwórz klucz o nazwie firmy.</span><span class="sxs-lookup"><span data-stu-id="827dd-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="827dd-120">Następnie dodaj odpowiednie wartości rejestru do klucza w firmie.</span><span class="sxs-lookup"><span data-stu-id="827dd-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="827dd-121">Podczas odczytywania rejestru z aplikacji sieci Web, bieżącego użytkownika zależy od uwierzytelniania i personifikacji wdrożone w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="827dd-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="827dd-122">Jest bardziej bezpieczne można zapisać danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="827dd-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="827dd-123">Po utworzeniu wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="827dd-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="827dd-124">Inny proces, możliwe, że złośliwe jeden mogły już zostać utworzone wartość i jest do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="827dd-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="827dd-125">Po umieszczeniu danych w wartości rejestru, dane są dostępne do innego procesu.</span><span class="sxs-lookup"><span data-stu-id="827dd-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="827dd-126">Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="827dd-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="827dd-127">Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="827dd-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="827dd-128">Nie jest bezpieczny do przechowywania kluczy tajnych, takie jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (listy kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="827dd-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="827dd-129">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="827dd-129">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="827dd-130">Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="827dd-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="827dd-131">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="827dd-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="827dd-132">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="827dd-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="827dd-133">Klucz jest zamknięta (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="827dd-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="827dd-134">Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="827dd-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="827dd-135">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="827dd-135">.NET Framework Security</span></span>  
 <span data-ttu-id="827dd-136">Aby uruchomić ten proces, używanemu zestawowi wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="827dd-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="827dd-137">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="827dd-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="827dd-138">Podobnie użytkownik musi mieć odpowiednich list ACL tworzenia i zapisywania ustawień.</span><span class="sxs-lookup"><span data-stu-id="827dd-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="827dd-139">Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu może nie ma uprawnienia systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="827dd-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="827dd-140">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="827dd-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="827dd-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="827dd-141">See Also</span></span>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>  
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>  
 [<span data-ttu-id="827dd-142">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="827dd-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)  
 [<span data-ttu-id="827dd-143">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="827dd-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
