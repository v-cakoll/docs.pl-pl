---
title: 'Instrukcje: Utwórz klucz rejestru i ustaw jego wartość w Visual Basic'
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
ms.openlocfilehash: 84fc824ad5911621c679d70f480d9b5e83c095ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054132"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="7b965-102">Instrukcje: Utwórz klucz rejestru i ustaw jego wartość w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b965-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="7b965-103">`CreateSubKey` Metoda`My.Computer.Registry` obiektu może służyć do tworzenia klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="7b965-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="7b965-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="7b965-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="7b965-105">Aby utworzyć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="7b965-105">To create a registry key</span></span>

- <span data-ttu-id="7b965-106">`CreateSubKey` Użyj metody, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="7b965-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="7b965-107">W parametrze `Subkey` nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="7b965-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="7b965-108">W tym przykładzie klucz `MyTestKey` rejestru jest tworzony w obszarze HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="7b965-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="7b965-109">Aby utworzyć klucz rejestru i ustawić w nim wartość</span><span class="sxs-lookup"><span data-stu-id="7b965-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="7b965-110">`CreateSubkey` Użyj metody, określając gałąź, w której ma zostać umieszczony klucz, a także nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="7b965-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="7b965-111">W tym przykładzie klucz `MyTestKey` rejestru jest tworzony w obszarze HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="7b965-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="7b965-112">Ustaw wartość za pomocą `SetValue` metody.</span><span class="sxs-lookup"><span data-stu-id="7b965-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="7b965-113">Ten przykład ustawia wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="7b965-113">This example sets the string value.</span></span> <span data-ttu-id="7b965-114">"MyTestKeyValue" do "jest to wartość testowa".</span><span class="sxs-lookup"><span data-stu-id="7b965-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="7b965-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b965-115">Example</span></span>

<span data-ttu-id="7b965-116">W tym przykładzie klucz `MyTestKey` rejestru jest tworzony w obszarze HKEY_CURRENT_USER, a następnie ustawia wartość `This is a test value` `MyTestKeyValue` ciągu na.</span><span class="sxs-lookup"><span data-stu-id="7b965-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="7b965-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="7b965-117">Robust Programming</span></span>

<span data-ttu-id="7b965-118">Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację klucza.</span><span class="sxs-lookup"><span data-stu-id="7b965-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="7b965-119">Na przykład możesz chcieć otworzyć klucz HKEY_CURRENT_USER\Software bieżącego użytkownika i utworzyć klucz z nazwą swojej firmy.</span><span class="sxs-lookup"><span data-stu-id="7b965-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="7b965-120">Następnie Dodaj wartości rejestru do klucza firmy.</span><span class="sxs-lookup"><span data-stu-id="7b965-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="7b965-121">Podczas odczytywania rejestru z aplikacji sieci Web bieżący użytkownik zależy od uwierzytelniania i personifikacji zaimplementowanego w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7b965-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="7b965-122">Bardziej bezpieczne jest zapisanie danych do folderu użytkownika (<xref:Microsoft.Win32.Registry.CurrentUser>), a nie na komputerze lokalnym (<xref:Microsoft.Win32.Registry.LocalMachine>).</span><span class="sxs-lookup"><span data-stu-id="7b965-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="7b965-123">Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b965-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="7b965-124">Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="7b965-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="7b965-125">Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu.</span><span class="sxs-lookup"><span data-stu-id="7b965-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="7b965-126">Aby tego uniknąć, należy użyć <xref:Microsoft.Win32.RegistryKey.GetValue%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7b965-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="7b965-127">Zwraca `Nothing` , jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="7b965-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="7b965-128">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy ACL (Access Control List).</span><span class="sxs-lookup"><span data-stu-id="7b965-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="7b965-129">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="7b965-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="7b965-130">Nazwa klucza to `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="7b965-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="7b965-131">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="7b965-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="7b965-132">Nazwa klucza przekracza limit 255 znaków (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="7b965-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="7b965-133">Klucz jest zamknięty (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7b965-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="7b965-134">Klucz rejestru jest tylko do odczytu (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="7b965-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="7b965-135">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7b965-135">.NET Framework Security</span></span>

<span data-ttu-id="7b965-136">Aby uruchomić ten proces, zestaw wymaga poziomu uprawnień przyznany przez <xref:System.Security.Permissions.RegistryPermission> klasę.</span><span class="sxs-lookup"><span data-stu-id="7b965-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="7b965-137">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="7b965-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="7b965-138">Analogicznie, użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania w ustawieniach.</span><span class="sxs-lookup"><span data-stu-id="7b965-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="7b965-139">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7b965-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="7b965-140">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="7b965-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b965-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b965-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="7b965-142">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="7b965-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="7b965-143">Podstawowe informacje o zabezpieczeniach dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="7b965-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
