---
title: 'Instrukcje: Utwórz klucz rejestru i określanie jego wartości w języku Visual Basic'
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
ms.openlocfilehash: 0cadff8b44c60041e2664b1d3b70830209014301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014027"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="ae325-102">Instrukcje: Utwórz klucz rejestru i określanie jego wartości w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae325-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>
<span data-ttu-id="ae325-103">`CreateSubKey` Metody `My.Computer.Registry` obiekt może służyć do tworzenia klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="ae325-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="ae325-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="ae325-104">Procedure</span></span>  
  
#### <a name="to-create-a-registry-key"></a><span data-ttu-id="ae325-105">Aby utworzyć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="ae325-105">To create a registry key</span></span>  
  
- <span data-ttu-id="ae325-106">Użyj `CreateSubKey` metody, wskazujące, której hive, umieszcza klucz w obszarze, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="ae325-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ae325-107">Parametr `Subkey` nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="ae325-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="ae325-108">W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ae325-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
#### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="ae325-109">Utwórz klucz rejestru i wartości w nim</span><span class="sxs-lookup"><span data-stu-id="ae325-109">To create a registry key and set a value in it</span></span>  
  
1. <span data-ttu-id="ae325-110">Użyj `CreateSubkey` metody, wskazujące, której hive, umieszcza klucz w obszarze, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="ae325-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="ae325-111">W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="ae325-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>  
  
     [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]  
  
2. <span data-ttu-id="ae325-112">Ustaw wartość z `SetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="ae325-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="ae325-113">W tym przykładzie ustawia wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ae325-113">This example sets the string value.</span></span> <span data-ttu-id="ae325-114">"MyTestKeyValue" do "To jest wartość testu".</span><span class="sxs-lookup"><span data-stu-id="ae325-114">"MyTestKeyValue" to "This is a test value".</span></span>  
  
     [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="ae325-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae325-115">Example</span></span>  
 <span data-ttu-id="ae325-116">W tym przykładzie tworzy klucz rejestru `MyTestKey` w gałęzi HKEY_CURRENT_USER, a następnie ustawia wartość ciągu `MyTestKeyValue` do `This is a test value`.</span><span class="sxs-lookup"><span data-stu-id="ae325-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>  
  
 [!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ae325-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ae325-117">Robust Programming</span></span>  
 <span data-ttu-id="ae325-118">Zbadaj strukturę rejestru w celu znalezienia odpowiedniej lokalizacji dla klucza.</span><span class="sxs-lookup"><span data-stu-id="ae325-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="ae325-119">Na przykład można otworzyć klucza HKEY_CURRENT_USER\Software bieżącego użytkownika, a następnie utworzyć klucz z nazwą Twojej firmy.</span><span class="sxs-lookup"><span data-stu-id="ae325-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="ae325-120">Następnie dodaj wartości rejestru do klucza Twojej firmy.</span><span class="sxs-lookup"><span data-stu-id="ae325-120">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="ae325-121">Podczas odczytywania rejestru z aplikacji sieci Web, bieżącego użytkownika zależy od uwierzytelniania i personifikacji zaimplementowane w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ae325-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>  
  
 <span data-ttu-id="ae325-122">Bezpieczniej jest do zapisywania danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="ae325-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>  
  
 <span data-ttu-id="ae325-123">Kiedy tworzysz wartość rejestru, musisz zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="ae325-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="ae325-124">Inny proces, fałszywy, być może już utworzył wartość i masz do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="ae325-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="ae325-125">Dane są umieszczane w wartości rejestru, dane są dostępne dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="ae325-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="ae325-126">Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ae325-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="ae325-127">Zwraca `Nothing` Jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="ae325-127">It returns `Nothing` if the key does not already exist.</span></span>  
  
 <span data-ttu-id="ae325-128">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (list usługi Access Control).</span><span class="sxs-lookup"><span data-stu-id="ae325-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>  
  
 <span data-ttu-id="ae325-129">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="ae325-129">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="ae325-130">Nazwa klucza jest `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ae325-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="ae325-131">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ae325-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="ae325-132">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ae325-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="ae325-133">Klucz jest zamknięty (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ae325-133">The key is closed (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="ae325-134">Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="ae325-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ae325-135">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae325-135">.NET Framework Security</span></span>  
 <span data-ttu-id="ae325-136">Aby uruchomić ten proces, zestaw wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.RegistryPermission> klasy.</span><span class="sxs-lookup"><span data-stu-id="ae325-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="ae325-137">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="ae325-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="ae325-138">Podobnie użytkownik musi mieć prawidłowe listy ACL dla tworzenia zmiennej czy zapisujemy do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ae325-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="ae325-139">Na przykład lokalnych aplikacji, które ma uprawnienia zabezpieczeń dostępu kodu ma uprawnienie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="ae325-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="ae325-140">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="ae325-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae325-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae325-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="ae325-142">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="ae325-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="ae325-143">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="ae325-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
