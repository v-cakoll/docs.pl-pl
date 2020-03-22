---
title: 'Porady: tworzenie klucza rejestru i określanie jego wartości'
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
ms.openlocfilehash: 459c4b3f971009ee4b6b669c55bc058db0826595
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349200"
---
# <a name="how-to-create-a-registry-key-and-set-its-value-in-visual-basic"></a><span data-ttu-id="27f0d-102">Porady: tworzenie klucza rejestru i określanie jego wartości w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27f0d-102">How to: Create a Registry Key and Set Its Value in Visual Basic</span></span>

<span data-ttu-id="27f0d-103">Metoda `CreateSubKey` `My.Computer.Registry` obiektu może służyć do tworzenia klucza rejestru.</span><span class="sxs-lookup"><span data-stu-id="27f0d-103">The `CreateSubKey` method of the `My.Computer.Registry` object can be used to create a registry key.</span></span>

## <a name="procedure"></a><span data-ttu-id="27f0d-104">Procedura</span><span class="sxs-lookup"><span data-stu-id="27f0d-104">Procedure</span></span>

### <a name="to-create-a-registry-key"></a><span data-ttu-id="27f0d-105">Aby utworzyć klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="27f0d-105">To create a registry key</span></span>

- <span data-ttu-id="27f0d-106">Użyj `CreateSubKey` metody, określając, który gałąź umieścić klucz pod, jak również nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="27f0d-106">Use the `CreateSubKey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="27f0d-107">W `Subkey` przypadku przypadku przypadku nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="27f0d-107">The parameter `Subkey` is not case-sensitive.</span></span> <span data-ttu-id="27f0d-108">W tym przykładzie `MyTestKey` tworzy klucz rejestru w obszarze HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="27f0d-108">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

### <a name="to-create-a-registry-key-and-set-a-value-in-it"></a><span data-ttu-id="27f0d-109">Aby utworzyć klucz rejestru i ustawić w nim wartość</span><span class="sxs-lookup"><span data-stu-id="27f0d-109">To create a registry key and set a value in it</span></span>

1. <span data-ttu-id="27f0d-110">Użyj `CreateSubkey` metody, określając, który gałąź umieścić klucz pod, jak również nazwę klucza.</span><span class="sxs-lookup"><span data-stu-id="27f0d-110">Use the `CreateSubkey` method, specifying which hive to place the key under as well as the name of the key.</span></span> <span data-ttu-id="27f0d-111">W tym przykładzie `MyTestKey` tworzy klucz rejestru w obszarze HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="27f0d-111">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER.</span></span>

    [!code-vb[VbResourceTasks#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#17)]

2. <span data-ttu-id="27f0d-112">Ustaw wartość za `SetValue` pomocą metody.</span><span class="sxs-lookup"><span data-stu-id="27f0d-112">Set the value with the `SetValue` method.</span></span> <span data-ttu-id="27f0d-113">W tym przykładzie ustawia wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="27f0d-113">This example sets the string value.</span></span> <span data-ttu-id="27f0d-114">"MyTestKeyValue" do "Jest to wartość testowa".</span><span class="sxs-lookup"><span data-stu-id="27f0d-114">"MyTestKeyValue" to "This is a test value".</span></span>

    [!code-vb[VbResourceTasks#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#14)]

## <a name="example"></a><span data-ttu-id="27f0d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="27f0d-115">Example</span></span>

<span data-ttu-id="27f0d-116">W tym przykładzie `MyTestKey` utworzy klucz rejestru w obszarze `MyTestKeyValue` `This is a test value`HKEY_CURRENT_USER a następnie ustawi wartość ciągu na .</span><span class="sxs-lookup"><span data-stu-id="27f0d-116">This example creates the registry key `MyTestKey` under HKEY_CURRENT_USER and then sets the string value `MyTestKeyValue` to `This is a test value`.</span></span>

[!code-vb[VbResourceTasks#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#15)]

## <a name="robust-programming"></a><span data-ttu-id="27f0d-117">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="27f0d-117">Robust Programming</span></span>

<span data-ttu-id="27f0d-118">Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację dla klucza.</span><span class="sxs-lookup"><span data-stu-id="27f0d-118">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="27f0d-119">Na przykład można otworzyć klucz HKEY_CURRENT_USER\Oprogramowanie bieżącego użytkownika i utworzyć klucz o nazwie firmy.</span><span class="sxs-lookup"><span data-stu-id="27f0d-119">For example, you may want to open the HKEY_CURRENT_USER\Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="27f0d-120">Następnie dodaj wartości rejestru do klucza firmy.</span><span class="sxs-lookup"><span data-stu-id="27f0d-120">Then add the registry values to your company's key.</span></span>

<span data-ttu-id="27f0d-121">Podczas odczytywania rejestru z aplikacji sieci Web bieżący użytkownik zależy od uwierzytelniania i personifikacji zaimplementowanych w aplikacji sieci Web.</span><span class="sxs-lookup"><span data-stu-id="27f0d-121">When reading the registry from a Web application, the current user depends on the authentication and impersonation implemented in the Web application.</span></span>

<span data-ttu-id="27f0d-122">Bezpieczniejsze jest zapisywanie danych w<xref:Microsoft.Win32.Registry.CurrentUser>folderze użytkownika ( )<xref:Microsoft.Win32.Registry.LocalMachine>zamiast do komputera lokalnego ( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-122">It is more secure to write data to the user folder (<xref:Microsoft.Win32.Registry.CurrentUser>) rather than to the local computer (<xref:Microsoft.Win32.Registry.LocalMachine>).</span></span>

<span data-ttu-id="27f0d-123">Podczas tworzenia wartości rejestru, należy zdecydować, co zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="27f0d-123">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="27f0d-124">Inny proces, być może złośliwy, może już stworzył wartość i mieć do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="27f0d-124">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="27f0d-125">Po umieszczeniu danych w wartości rejestru dane są dostępne dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="27f0d-125">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="27f0d-126">Aby temu zapobiec, <xref:Microsoft.Win32.RegistryKey.GetValue%2A> użyj tej metody.</span><span class="sxs-lookup"><span data-stu-id="27f0d-126">To prevent this, use the <xref:Microsoft.Win32.RegistryKey.GetValue%2A> method.</span></span> <span data-ttu-id="27f0d-127">`Nothing` Zwraca, jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="27f0d-127">It returns `Nothing` if the key does not already exist.</span></span>

<span data-ttu-id="27f0d-128">Przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nie jest bezpieczne, nawet jeśli klucz rejestru jest chroniony listami kontroli dostępu (listami kontroli dostępu).</span><span class="sxs-lookup"><span data-stu-id="27f0d-128">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by ACLs (Access Control Lists).</span></span>

<span data-ttu-id="27f0d-129">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="27f0d-129">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="27f0d-130">Nazwa klucza jest `Nothing` <xref:System.ArgumentNullException>( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-130">The name of the key is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="27f0d-131">Użytkownik nie ma uprawnień do tworzenia<xref:System.Security.SecurityException>kluczy rejestru ( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-131">The user does not have permissions to create registry keys (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="27f0d-132">Nazwa klucza przekracza limit 255<xref:System.ArgumentException>znaków ( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-132">The key name exceeds the 255-character limit (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="27f0d-133">Klucz jest zamknięty<xref:System.IO.IOException>( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-133">The key is closed (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="27f0d-134">Klucz rejestru jest tylko<xref:System.UnauthorizedAccessException>do odczytu ( ).</span><span class="sxs-lookup"><span data-stu-id="27f0d-134">The registry key is read-only (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="net-framework-security"></a><span data-ttu-id="27f0d-135">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="27f0d-135">.NET Framework Security</span></span>

<span data-ttu-id="27f0d-136">Aby uruchomić ten proces, zestaw wymaga poziomu <xref:System.Security.Permissions.RegistryPermission> uprawnień przyznanego przez klasę.</span><span class="sxs-lookup"><span data-stu-id="27f0d-136">To run this process, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.RegistryPermission> class.</span></span> <span data-ttu-id="27f0d-137">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="27f0d-137">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="27f0d-138">Podobnie użytkownik musi mieć poprawne listy ACL do tworzenia lub zapisywania do ustawień.</span><span class="sxs-lookup"><span data-stu-id="27f0d-138">Similarly, the user must have the correct ACLs for creating or writing to settings.</span></span> <span data-ttu-id="27f0d-139">Na przykład aplikacja lokalna, która ma uprawnienie zabezpieczeń dostępu do kodu, może nie mieć uprawnień systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="27f0d-139">For example, a local application that has the code access security permission might not have operating system permission.</span></span> <span data-ttu-id="27f0d-140">Aby uzyskać więcej informacji, zobacz [Podstawy zabezpieczeń dostępu do kodu](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="27f0d-140">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="27f0d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27f0d-141">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>
- <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>
- <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>
- [<span data-ttu-id="27f0d-142">Odczytywanie z rejestru i zapisywanie w nim</span><span class="sxs-lookup"><span data-stu-id="27f0d-142">Reading from and Writing to the Registry</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)
- [<span data-ttu-id="27f0d-143">Podstawy zabezpieczeń dostępu kodu</span><span class="sxs-lookup"><span data-stu-id="27f0d-143">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
