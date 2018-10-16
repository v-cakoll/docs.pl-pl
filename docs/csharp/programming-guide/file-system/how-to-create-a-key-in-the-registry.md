---
title: 'Porady: tworzenie klucza w rejestrze (Visual C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- registry, adding keys and values [C#]
- registry keys, creating [C#]
- keys, creating in registry
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
ms.openlocfilehash: a3a6af8eb493ce17ac73769decd1f60b903ae165
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2018
ms.locfileid: "49337613"
---
# <a name="how-to-create-a-key-in-the-registry-visual-c"></a><span data-ttu-id="2ff6a-102">Porady: tworzenie klucza w rejestrze (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="2ff6a-102">How to: Create a Key In the Registry (Visual C#)</span></span>
<span data-ttu-id="2ff6a-103">Ten przykład dodaje parę wartości "Name" i "Isabella" do rejestru bieżącego użytkownika, pod kluczem "Nazwy".</span><span class="sxs-lookup"><span data-stu-id="2ff6a-103">This example adds the value pair, "Name" and "Isabella", to the current user's registry, under the key "Names".</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff6a-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ff6a-104">Example</span></span>  
  
```csharp  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2ff6a-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2ff6a-105">Compiling the Code</span></span>  
  
-   <span data-ttu-id="2ff6a-106">Skopiuj kod i wklej go w `Main` metoda aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-106">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
-   <span data-ttu-id="2ff6a-107">Zastąp `Names` parametr o nazwie klucza znajdującą się bezpośrednio pod węzłem rejestru HKEY_CURRENT_USER.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-107">Replace the `Names` parameter with the name of a key that exists directly under the HKEY_CURRENT_USER node of the registry.</span></span>  
  
-   <span data-ttu-id="2ff6a-108">Zastąp `Name` parametr z nazwą wartości znajdującą się bezpośrednio pod węzłem nazw.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-108">Replace the `Name` parameter with the name of a value that exists directly under the Names node.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="2ff6a-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2ff6a-109">Robust Programming</span></span>  
 <span data-ttu-id="2ff6a-110">Zbadaj strukturę rejestru w celu znalezienia odpowiedniej lokalizacji dla klucza.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-110">Examine the registry structure to find a suitable location for your key.</span></span> <span data-ttu-id="2ff6a-111">Na przykład możesz otworzyć klucz oprogramowania bieżącego użytkownika, a następnie utworzyć klucz z nazwą Twojej firmy.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-111">For example, you might want to open the Software key of the current user, and create a key with your company's name.</span></span> <span data-ttu-id="2ff6a-112">Następnie dodaj wartości rejestru do klucza Twojej firmy.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-112">Then add the registry values to your company's key.</span></span>  
  
 <span data-ttu-id="2ff6a-113">Następujące warunki mogłyby spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2ff6a-113">The following conditions might cause an exception:</span></span>  
  
-   <span data-ttu-id="2ff6a-114">Nazwa klucza ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-114">The name of the key is null.</span></span>  
  
-   <span data-ttu-id="2ff6a-115">Użytkownik nie ma uprawnień do tworzenia kluczy rejestru.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-115">The user does not have permissions to create registry keys.</span></span>  
  
-   <span data-ttu-id="2ff6a-116">Nazwa klucza przekracza limit 255 znaków.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-116">The key name exceeds the 255-character limit.</span></span>  
  
-   <span data-ttu-id="2ff6a-117">Klucz jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-117">The key is closed.</span></span>  
  
-   <span data-ttu-id="2ff6a-118">Klucz rejestru jest tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-118">The registry key is read-only.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2ff6a-119">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2ff6a-119">.NET Framework Security</span></span>  
 <span data-ttu-id="2ff6a-120">Bezpieczniej jest do zapisywania danych w folderze użytkownika — `Microsoft.Win32.Registry.CurrentUser` — a nie na komputerze lokalnym — `Microsoft.Win32.Registry.LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-120">It is more secure to write data to the user folder — `Microsoft.Win32.Registry.CurrentUser` — rather than to the local computer — `Microsoft.Win32.Registry.LocalMachine`.</span></span>  
  
 <span data-ttu-id="2ff6a-121">Kiedy tworzysz wartość rejestru, musisz zdecydować, co należy zrobić, jeśli ta wartość już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-121">When you create a registry value, you need to decide what to do if that value already exists.</span></span> <span data-ttu-id="2ff6a-122">Inny proces, fałszywy, być może już utworzył wartość i masz do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-122">Another process, perhaps a malicious one, may have already created the value and have access to it.</span></span> <span data-ttu-id="2ff6a-123">Dane są umieszczane w wartości rejestru, dane są dostępne dla innego procesu.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-123">When you put data in the registry value, the data is available to the other process.</span></span> <span data-ttu-id="2ff6a-124">Aby tego uniknąć, należy użyć.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span><span class="sxs-lookup"><span data-stu-id="2ff6a-124">To prevent this, use the.`Overload:Microsoft.Win32.RegistryKey.GetValue`</span></span> <span data-ttu-id="2ff6a-125">Metoda.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-125">method.</span></span> <span data-ttu-id="2ff6a-126">Zwraca wartość null, jeśli klucz już istnieje.</span><span class="sxs-lookup"><span data-stu-id="2ff6a-126">It returns null if the key does not already exist.</span></span>  
  
 <span data-ttu-id="2ff6a-127">Nie jest bezpieczne przechowywanie wpisów tajnych, takich jak hasła, w rejestrze jako zwykłego tekstu, nawet jeśli klucz rejestru jest chroniony przez listy kontroli dostępu (ACL).</span><span class="sxs-lookup"><span data-stu-id="2ff6a-127">It is not secure to store secrets, such as passwords, in the registry as plain text, even if the registry key is protected by access control lists (ACL).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ff6a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2ff6a-128">See Also</span></span>

- <xref:System.IO?displayProperty=nameWithType>  
- [<span data-ttu-id="2ff6a-129">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2ff6a-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2ff6a-130">System plików i rejestr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="2ff6a-130">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
- [<span data-ttu-id="2ff6a-131">Odczyt, zapis i usuwanie z rejestru z C#</span><span class="sxs-lookup"><span data-stu-id="2ff6a-131">Read, write and delete from the registry with C#</span></span>](https://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)
