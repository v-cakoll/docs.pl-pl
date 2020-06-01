---
title: Jak utworzyć klucz w przewodniku programowania w języku Registry-C#
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: 9e340083ffca118337dc9a53bdf20808cd1b15cb
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241633"
---
# <a name="how-to-create-a-key-in-the-registry-c-programming-guide"></a><span data-ttu-id="bd76f-102">Jak utworzyć klucz w rejestrze (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bd76f-102">How to create a key in the registry (C# Programming Guide)</span></span>
<span data-ttu-id="bd76f-103">Ten przykład dodaje parę wartości "name" i "Isabella" do rejestru bieżącego użytkownika w kluczu "names" (nazwy).</span><span class="sxs-lookup"><span data-stu-id="bd76f-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd76f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd76f-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bd76f-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="bd76f-105">Compiling the Code</span></span>  
  
- <span data-ttu-id="bd76f-106">Skopiuj kod i wklej go do `Main` metody aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="bd76f-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
- <span data-ttu-id="bd76f-107">Zastąp `Names` parametr nazwą klucza, który istnieje bezpośrednio w węźle HKEY_CURRENT_USER rejestru.</span><span class="sxs-lookup"><span data-stu-id="bd76f-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
- <span data-ttu-id="bd76f-108">Zastąp `Name` parametr nazwą wartości, która istnieje bezpośrednio pod węzłem nazwy.</span><span class="sxs-lookup"><span data-stu-id="bd76f-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bd76f-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="bd76f-109">Robust Programming</span></span>  
 <span data-ttu-id="bd76f-110">Sprawdź strukturę rejestru, aby znaleźć odpowiednią lokalizację klucza.</span><span class="sxs-lookup"><span data-stu-id="bd76f-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="bd76f-111">Na przykład możesz chcieć otworzyć klucz oprogramowania bieżącego użytkownika i utworzyć klucz z nazwą swojej firmy.</span><span class="sxs-lookup"><span data-stu-id="bd76f-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="bd76f-112">Następnie Dodaj wartości rejestru do klucza firmy.</span><span class="sxs-lookup"><span data-stu-id="bd76f-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="bd76f-113">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="bd76f-113">The following conditions might cause an exception:</span></span>  
  
- <span data-ttu-id="bd76f-114">Nazwa klucza ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="bd76f-114">The name of the key is null.</span></span>  
  
- <span data-ttu-id="bd76f-115">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="bd76f-115">The user does not have permissions to create registry keys.</span></span>  
  
- <span data-ttu-id="bd76f-116">Nazwa klucza przekracza limit 255 znaków.</span><span class="sxs-lookup"><span data-stu-id="bd76f-116">The key name exceeds the 255-character limit.</span></span>  
  
- <span data-ttu-id="bd76f-117">Klucz jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="bd76f-117">The key is closed.</span></span>  
  
- <span data-ttu-id="bd76f-118">Klucz rejestru jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="bd76f-118">The registry key is read-only.</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="bd76f-119">Zabezpieczenia platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bd76f-119">.NET Security</span></span>  
 <span data-ttu-id="bd76f-120">Bardziej bezpieczne jest zapisanie danych do folderu użytkownika — `Microsoft.Win32.Registry.CurrentUser` a nie na komputerze lokalnym — `Microsoft.Win32.Registry.LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="bd76f-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="bd76f-121">Podczas tworzenia wartości rejestru należy zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="bd76f-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="bd76f-122">Inny proces, prawdopodobnie złośliwy, mógł już utworzyć wartość i uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="bd76f-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="bd76f-123">Po umieszczeniu danych w wartości rejestru, dane są dostępne dla drugiego procesu.</span><span class="sxs-lookup"><span data-stu-id="bd76f-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="bd76f-124">Aby temu zapobiec, użyj.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="bd76f-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="bd76f-125">Method.</span><span class="sxs-lookup"><span data-stu-id="bd76f-125">method.</span></span> <span data-ttu-id="bd76f-126">Zwraca wartość null, jeśli klucz jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="bd76f-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="bd76f-127">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze w postaci zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (ACL).</span><span class="sxs-lookup"><span data-stu-id="bd76f-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd76f-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bd76f-128">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="bd76f-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bd76f-129">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bd76f-130">System plików i rejestr (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bd76f-130">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
- [<span data-ttu-id="bd76f-131">Odczytywanie, zapisywanie i usuwanie z rejestru przy użyciu języka C #</span><span class="sxs-lookup"><span data-stu-id="bd76f-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
