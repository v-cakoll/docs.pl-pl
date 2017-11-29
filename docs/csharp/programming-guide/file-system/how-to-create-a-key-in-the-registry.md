---
title: 'Porady: tworzenie klucza w rejestrze (Visual C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6cc79a8a914d3ef5b7c496db4dc0d2b3eb17768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="f6590-102">Porady: tworzenie klucza w rejestrze (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="f6590-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="f6590-103">W tym przykładzie dodaje pary wartości, "Name" i "Isabella", do bieżącego użytkownika, kluczu rejestru "Nazwy".</span><span class="sxs-lookup"><span data-stu-id="f6590-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6590-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6590-104">Example</span></span>  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6590-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="f6590-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="f6590-106">Skopiuj kod i wklej ją do `Main` metoda aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="f6590-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="f6590-107">Zastąp `Names` parametr o nazwie klucza, czy istnieje bezpośrednio w węźle HKEY_CURRENT_USER rejestru.</span><span class="sxs-lookup"><span data-stu-id="f6590-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="f6590-108">Zastąp `Name` parametr o nazwie wartość, która istnieje bezpośrednio w węźle nazwy.</span><span class="sxs-lookup"><span data-stu-id="f6590-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6590-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f6590-109">Robust Programming</span></span>  
 <span data-ttu-id="f6590-110">Sprawdź, czy struktura rejestru można znaleźć odpowiedniej lokalizacji dla klucza.</span><span class="sxs-lookup"><span data-stu-id="f6590-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="f6590-111">Na przykład można otworzyć klucza oprogramowania bieżącego użytkownika i Utwórz klucz o nazwie firmy.</span><span class="sxs-lookup"><span data-stu-id="f6590-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="f6590-112">Następnie dodaj odpowiednie wartości rejestru do klucza w firmie.</span><span class="sxs-lookup"><span data-stu-id="f6590-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="f6590-113">Poniższe warunki może spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="f6590-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="f6590-114">Nazwa klucza jest pusta.</span><span class="sxs-lookup"><span data-stu-id="f6590-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="f6590-115">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="f6590-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="f6590-116">Nazwa klucza przekracza limit 255 znaków.</span><span class="sxs-lookup"><span data-stu-id="f6590-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="f6590-117">Klucz jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="f6590-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="f6590-118">Klucz rejestru jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="f6590-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6590-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6590-119">.NET Framework Security</span></span>  
 <span data-ttu-id="f6590-120">Jest bardziej bezpieczne można zapisać danych do folderu użytkownika — `Microsoft.Win32.Registry.CurrentUser` , a nie na komputerze lokalnym — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="f6590-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="f6590-121">Po utworzeniu wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6590-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="f6590-122">Inny proces, możliwe, że złośliwe jeden mogły już zostać utworzone wartość i jest do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="f6590-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="f6590-123">Po umieszczeniu danych w wartości rejestru, dane są dostępne do innego procesu.</span><span class="sxs-lookup"><span data-stu-id="f6590-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="f6590-124">Aby tego uniknąć, należy użyć.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="f6590-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="f6590-125">Metoda.</span><span class="sxs-lookup"><span data-stu-id="f6590-125">method.</span></span> <span data-ttu-id="f6590-126">Zwraca wartość null, jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6590-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="f6590-127">Nie jest bezpieczny do przechowywania kluczy tajnych, takie jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (ACL).</span><span class="sxs-lookup"><span data-stu-id="f6590-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6590-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6590-128">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="f6590-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6590-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6590-130">System plików i rejestr (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="f6590-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="f6590-131">Odczytu, zapisu i usuwania z rejestru w języku C#</span><span class="sxs-lookup"><span data-stu-id="f6590-131">Read, write and delete from the registry with C#</span></span>](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
